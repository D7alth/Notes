
Vamos testar as duas rotas possíveis para as autorizações:

**Usar um tipo composto** 
ARRAY [ 
	VARCHAR Field
	ARRAY Permissions [ VARCHAR ] 
]

- Permissões simples
- Levemente Flexível (extensível para métricas, com ressalvas)
- Necessário relação 1 para 1 com areas 
- Tipado
- Unsset, eventuais buscas por permissão poderiam usar operadores diretos como "="
- Tende a ser mais rápido do que a opção com json

| UserId                               | AreaId             | Permissions                                                       |
| ------------------------------------ | ------------------ | ----------------------------------------------------------------- |
| 9a4556d9-ab0d-40df-94dc-5318576fb1af | ALASUL-MANEVIRGULA | [ <br>{"Terceritos", ["Read", "Create"]},  {"Energy", [""]} <br>] |

**Usar um tipo composto** fortemente tipado com ENUM 
ARRAY [ 
	VARCHAR Field
	ARRAY Permissions [ ENUM ] 
]

- Permissões simples
- Menos Flexível (extensível para métricas, com ressalvas)
- Necessário relação 1 para 1 com areas 
- Tipado
- Unsset, eventuais buscas por permissão poderiam usar operadores diretos como "="
- Tende a ser mais rápido do que as outras opções
- Indicies nos ENUMs
- Mais seguro

| UserId                               | AreaId             | Permissions                                                       |
| ------------------------------------ | ------------------ | ----------------------------------------------------------------- |
| 9a4556d9-ab0d-40df-94dc-5318576fb1af | ALASUL-MANEVIRGULA | [ <br>{"Terceritos", ["Read", "Create"]},  {"Energy", [""]} <br>] |


**Usar um JSONB** 
JSONB
{
	"Fields": 
	[
		{
			"Field",
			["Permissions"]
		}
	]
	
}

- Permissões complexas
- Altamente Flexível
- Poderíamos ter apenas uma linha por UserId, as relações podem ser dadas pelo JSON 
- Necessário desserialização
- Jsonb, Eventuais buscas por permissão poderiam usar operadores diretos como "->"
- Tende a ser mais lento do que a opção com tipo composto

| UserId                               | AreaId             | Permissions                                                                                                              |
| ------------------------------------ | ------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| 9a4556d9-ab0d-40df-94dc-5318576fb1af | ALASUL-MANEVIRGULA | {<br>	"Fields": <br>	[<br>		{<br>			"Terceiros",<br>			["Read", "Create]<br>		},<br>		{<br>			"Energy"<br>		}<br>	]<br>} |
|                                      |                    |                                                                                                                          |



-----

### Requisitos de autorização

Obs: 

**Relação indiretas** : qualquer relação que não seja direta com o prédio, como por exemplo a uma área interna ao prédio.  

- [x] Atribuição ações (Contratos - Geral)
	1. Qualquer ação atribuída (Visualizar, Editar, Criar, Excluir), concede permissão de visualização, mesmo que implícita. 
- [x] Atribuição de autorização (Contratos - Geral)
	1. Apenas administradores da "MainArea" devem atribuir autorizações 
	2. Usuários sem relações diretas aos prédios não devem acessar as paginas
	3. Usuários com relações diretas aos prédios mas, sem permissões explicitas não devem acessar as paginas
	4. Usuários com relações "indiretas" aos prédios não devem ter permissões aos contratos
	5. Usuários não devem ter permissões para fora de sua "MainArea"
	6. As atribuições das ações podem ser feitas todas de uma vez (Ler, editar, criar e excluir) mas as atribuições das relações devem ser feitas uma a uma (Usuário - Prédio)
	7. Usuários podem ter atribuições de permissões e ações diferentes para o mesmo prédio (por exemplo, um usuário pode editar mas não excluir).
- [x] Atribuições de permissões (Clientes - Especial)
	1. Atribuída e gerida manualmente (equipe do back)


Um administrador, apenas pode, adiciona uma permissão de acesso direta a um prédio e a um usuário o qual o prédio esteja em sua main area.




Tem algum caso para um usuário ter que ver suas permissões? 



















[[_TOC_]]

Gerenciamento de Autorizações

**Objetivo:**  

Definir os requisitos de autorização e gerenciamento de permissões para acesso e controle de funcionalidades em sistemas associados a contratos gerais ou específicos de clientes, garantindo um modelo de controle flexível e seguro.

* * *

### Requisitos Funcionais

1.  **Gestão de Permissões:**
    *   O sistema deve permitir atribuir as seguintes permissões de forma independente:
        *   Visualizar
        *   Criar
        *   Editar
        *   Excluir
    *   Usuários podem ter diferentes níveis de permissão para o mesmo recurso.
2.  **Gestão de Autorizações:**
    *   O sistema deve permitir atribuir autorizações baseadas em:
        *   Relações diretas (ex.: usuário associado diretamente a um prédio).
3.  **Restrições de Escopo:**
    *   As permissões devem ser limitadas à área de atuação ("MainArea") do usuário.
    *   Relações indiretas não devem receber permissões a contratos.
4.  **Delegação de Autorizações:**
    *   Apenas administradores podem delegar permissões ou autorizações.

* * *

### Requisitos Não Funcionais

1.  O sistema deve validar permissões e autorizações antes de qualquer operação.
2.  O desempenho do sistema não deve ser impactado por verificações de permissões, mesmo em estruturas hierárquicas complexas.

* * *

### Critérios de Aceitação

#### 1. **Usuário com Permissão**

**Dado** que o usuário esteja autenticado no sistema  
**E** que tenha todas as permissões possíveis  
**E** que tenha relação direta com pelo menos um prédio  
**Quando** acessar uma página de contratos para suas permissões atribuídas  
**Então** a ação deve ser permitida.

#### 2. **Usuário Sem Permissão Específica**

**Dado** que o usuário esteja autenticado no sistema  
**Quando** tentar acessar uma funcionalidade sem a permissão necessária  
**Então** a ação deve ser bloqueada e uma mensagem de erro exibida.

#### 3. **Usuário Fora da MainArea**

**Dado** que o usuário esteja autenticado no sistema  
**Quando** tentar acessar funcionalidades fora de sua área de responsabilidade  
**Então** o acesso deve ser bloqueado.

#### 4. **Atribuição de Permissão**

**Dado** que o usuário seja um administrador autenticado no sistema  
**E** esteja dentro de sua área de responsabilidade  
**Quando** delegar permissões diretamente relacionadas a um prédio ao usuário  
**Então** a delegação deve ser realizada com sucesso.

#### 5. **Atribuição de Permissão com Relação Indireta Negada**

**Dado** que o usuário seja um administrador autenticado no sistema  
**E** esteja dentro de sua área de responsabilidade  
**Quando** delegar permissões indiretamente relacionadas a um prédio ao usuário  
**Então** a delegação deve ser negada e uma mensagem de erro exibida.

#### 6. **Atribuição de Permissão Fora da Área de Responsabilidade Negada**

**Dado** que o usuário seja um administrador autenticado no sistema  
**E** esteja fora de sua área de responsabilidade  
**Quando** delegar permissões diretamente relacionadas a um prédio ao usuário  
**Então** a delegação deve ser negada e uma mensagem de erro exibida.

* * *

### Cenários de Autorização

1.  **Permissões Gerais:**
    *   As permissões atribuídas para "Visualizar", "Criar", "Editar" e "Excluir" podem ser combinadas ou atribuídas individualmente.
    *   Qualquer permissão atribuída concede automaticamente "Visualizar".
2.  **Relações Diretas e Indiretas:**
    *   Relações diretas podem receber acesso, condicionadas às permissões atribuídas.
    *   Relações indiretas não podem receber permissões por padrão.

* * *

### Estrutura de Banco de Dados

#### Alternativas para Estruturar Autorizações

##### **1. Permissão diretas**

**Características:**
*   Permissões simples.
*   Necessário relação N:1 com áreas.

**Exemplo de Tabela:**

| UserId                               | AreasId              | Permissions                                           |
| ------------------------------------ | -------------------- | ----------------------------------------------------- |
| 9a4556d9-ab0d-40df-94dc-5318576fb1af | [MANEVIRGULA, CECNC] | [{"Terceritos", ["Read", "Create"]}]                  |



------


Requisitos novos? 

Contract_permissions
ou 
Algo com autorization


Uma alternativa e a partir de um usuário criado, adicionar um evento que crie uma autorização default.

**Evento de domínio** 
Eventos de domino que não são dominos de notificações 
(DomainEventsDispatcher)

Usar como referencia as energy bill 

Se criar não conseguiu salvar o usuário no B2C então nada de usuário

