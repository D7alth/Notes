#AspNet #TechDictionary #EntityFramework

## OwnsMany

Esse tipo de relação implica na parte "mais fraca" não ter um identidade e de fato ser uma tabela que apenas **COMPOEM** outra tabela, ou seja, a tabela filha e de fato, parte da tabela pai.

De acordo com a documentação oficial (Microsoft)[]

_"As entidades de propriedade são essencialmente parte do proprietário e não podem existir sem ele, elas são conceitualmente semelhantes às agregações. Isso significa que a entidade de propriedade é por definição do lado dependente da relação com o proprietário" _

Isso significa que o **EF** exige que cada **OwnsMany**, tenha um único dono. Conceitualmente e como se no banco, cada **Owned Entity** fosse criado dentro da tabela proprietária, isso deixa claro o intuito desse relacionamento.  - _esse caso pode ocorrer literalmente, mas não e um padrão, depende da configuração do EF._
### Onde faz sentido:

E adequando quando o objeto relacionado não tem um identidade independente e e conceitualmente ligado a entidade PAI.

- Objetos ou atributos complexos
- Listas de ValueObjects complexos
- Um objeto ou valor que deve ser tratado fora da tabela proprietária mas ainda tenha forte dependência. 

### Características:

- Não possuem identidade fora do contexto do proprietário 
	- Elas podem ter chaves primárias definidas dentro desse contexto
	- No caso de coleções possuídas, e comum a chave primaria ser definida a partir da chave estrangeria + um identificado único. 
- Caso a entidade não tenha nenhum atributo que possa ser classificado como um identificador o próprio EF vai criar um **Id** como uma **propriedade shadown**, e vai usar ela junto da FK para compor o identificador. 
- Não pode ser referenciado por outras entidades diretamente
- Não pode ter múltiplos donos 

### Casos de uso:
#### Projeto Cortex

**Desenvolvimento do modulo de dashboard de comparativo** - A modelagem foi proposta como na figura abaixo.

![[Pasted image 20250130152510.png]]

A ideia seria adicionar uma nova tabela "Tabela B", discriminado a relação por uma propriedade de separação.

A modelagem estava parcialmente concluída para a **Tabela A**, porém, porem, nos requisitos era especificado que ambas as tabelas deveriam ser proprietárias da mesma entidade apropriada.

##### **Problema**

Por uma característica / restrição do "by-design" do próprio EF em relação as diretrizes do tipo de relação

Como consta na documentação [Microsoft](https://learn.microsoft.com/pt-br/ef/core/modeling/owned-entities?utm_source=chatgpt.com#limitations)
_"Instancias de tipos de entidade de propriedade não podem ser compartilhadas por vários proprietários (este é um cenário bem conhecido para objetos de valor que não podem ser implementados usando tipos de entidade de propriedade) _

**E impossível criar esse tipo de relação.**
##### **Soluções possíveis**

- Adicionar um "identificador artificial" no VO e tratar a tabela como uma tabela de identidade própria, separando assim ela da necessidade de ter um proprietário
	- Isso também implicaria em novos atributos **nullables**, como um identificador para cada uma das tabelas, porque a tabela deveria diferenciar as tabelas com as quais ela estiver fazendo o relacionamento 
- Uma tabela para cada proprietário, criar uma tabela de apropriados para cada um dos proprietários 
	- Implica em uma nova tabela e da separação das buscas por tabela ao invés do atributo de descriminação proposto 
##### **Soluções proposta**

**Uma tabela para cada proprietário, criar uma tabela de apropriados para cada um dos**.

Essa e a solução mais simples, ainda que haja uma "repetição" nas tabelas, os contextos diferentes dentro do mesmo agregado justificam essa "repetição", principalmente por se tratar de um tipo complexo, mas que não exige a necessidade de uma identificação. 

