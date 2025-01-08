
Montar BDD da tela de contratos. 

----

**Característica**: Adição de terceiros / Licenças 
 
Contexto:
    Dado o usuario "John doe".
         
Cenário: Adição de terceiros
      Dado que "John doe" tenha o acesso devido ao Edifício "CECNC" 
      E dado que "John doe" tenha especificado um fornecedor
      Quando "John doe" tentar adicionar um novo "**Terceiro**", para o Edifício "CECNC" 
      Então deve-se adicionar o **"Terceiro"** solicitado, relacionado ao prédio especificado 

Cenário: Adição de terceiros sem fornecedor especificado
      Dado que "John doe" tenha o acesso devido ao Edifício "CECNC" 
      E dado que "John doe" tenha especificado um fornecedor o qual ainda não existe
      Quando "John doe" tentar adicionar um novo "**Terceiro**", para o Edifício "CECNC" 
      Então deve-se adicionar o "**Fornecedor**" o qual foi especificado
      E então o **"Terceiro"** solicitado, relacionado ao prédio especificado 

Cenário: Adição de terceiros sem fornecedor 
      Dado que "John doe" tenha o acesso devido ao Edifício "CECNC" 
      E dado que "John doe" não tenha especificado um "**fornecedor**"
      Quando "John doe" tentar adicionar um novo "**Terceiro**", para o Edifício "CECNC" 
	  Então deve-se retornar "404, bad request"
	  
Cenário: Adição de terceiros duplicado 
      Dado que "John doe" tenha o acesso devido ao Edifício "CECNC" 
      E dado que o nome do terceiro já exista relacionado ao Edifício "CECNC" 
      E dado que tenha o mesmo fornecedor do que existirá 
      Quando "John doe" tentar adicionar um novo "**Terceiro**", para o Edifício "CECNC" 
	  Então deve-se retornar "404, bad request"
	  
-----

**Característica**: Adição de Funcionários 
 
Contexto:
    Dado o usuario "John doe".
         
Cenário: Adição de funcionário 
      Dado que "John doe" tenha o acesso devido ao Edifício "CECNC" 
      E dado que "John doe" tenha especificado um tipo de documento
      Quando "John doe" tentar adicionar um novo "**Funcionário**", para o Edifício "CECNC" 
      Então deve-se adicionar o **"Funcionário"** solicitado, relacionado ao prédio especificado 

Cenário: Adição de funcionário documento especificado
      Dado que "John doe" tenha o acesso devido ao Edifício "CECNC" 
      E dado que "John doe" tenha especificado um documento o qual ainda não existe
      Quando "John doe" tentar adicionar um novo "**Funcionário**", para o Edifício "CECNC" 
      Então deve-se adicionar o "**Documento**" o qual foi especificado
      E então o **"Funcionário"** solicitado, relacionado ao prédio especificado 

Cenário: Adição de funcionário sem documento  
      Dado que "John doe" tenha o acesso devido ao Edifício "CECNC" 
      E dado que "John doe" não tenha especificado um "**Documento**"
      Quando "John doe" tentar adicionar um novo "**Fucionario**", para o Edifício "CECNC" 
	  Então deve-se retornar "404, bad request"
	  
Cenário: Adição de terceiros duplicado 
      Dado que "John doe" tenha o acesso devido ao Edifício "CECNC" 
      E dado que o nome do terceiro já exista relacionado ao Edifício "CECNC" 
      E dado que tenha o mesmo fornecedor do que existirá 
      Quando "John doe" tentar adicionar um novo "**Terceiro**", para o Edifício "CECNC" 
	  Então deve-se retornar "404, bad request"

-----

**Característica**: Autorização de acesso
 
Contexto:
    Dado o usuario "John doe".
         
Cenário: 
      Dado que "John doe" tenha acesso direto ao Edifício "CECNC" 
      E dado que não tenha restrições para o tipo de "**Terceiros**"
      Quando "John doe" tentar acessar a pagina de "**Terceiros**"
      Então deve-se mostrar todos os terceiros cadastrados para o Edifício o qual tem acesso 
 
Cenário: Autorização indireta a terceiros por **Main Area**
    Dado que "John doe" tenha acesso de "**administrador**" da **Main Area** "x" 
    E dado que a tal, tenha vários Edifícios relacionados 
    Quando "John doe" tentar acessar a pagina de "**Terceiros**"
    Então deve-se mostrar os terceiros de cada um dos edifícios relacionados a **Main Area** "x" 
 
Cenário: Acesso a terceiros com restrição
    Dado que "John doe" tenha acesso direto ao Edifício "CECNC" 
    E dado que  tenha apenas a restrição para o tipo de "**Terceiros**"
    Quando "John doe" tentar acessar a pagina de "**Terceiros**"
    Então deve-se retornar  "403, fobbiden"

Cenário: Acesso a terceiros indireto sem autorização
    Dado que "John doe" tenha a todas as torres e pavimentos relacionados ao Edifício "CECNC" 
    E dado que não tenha restrições para o tipo de "**Terceiros**"
    Quando "John doe" tentar acessar a pagina de "**Terceiros**"
    Então deve-se retornar  "403, fobbiden"



------

### Especifica de clientes

Cenário: Autorização a clientes como administrador 
    Dado que "John doe" tenha acesso de "**administrador**" da **Main Area** "x"
    E dado que a essa, tenha alguma relação com as **Main Area** do "Grupo Orion"
    Quando "John doe" tentar acessar a pagina de "**Clientes**"
    Então deve-se mostrar os clientes de cada um dos edifícios relacionados a **Main Area** "x" 

Cenário: Autorização a clientes como relacionado
    Dado que "John doe" tenha acesso direto ao Edifício "CECNC" 
    E dado que tenha alguma relação com as **Main Area** do "Grupo Orion"
    E dado que não tenha restrições para o tipo de "**Clientes**"
    Quando "John doe" tentar acessar a pagina de "**Clientes**"
    Então deve-se mostrar todos os terceiros cadastrados para o Edifício o qual tem acesso 

Cenário: Acesso a clientes como administrador não relacionado
    Dado que "John doe" tenha acesso de "**administrador**" da **Main Area** "x"
    E dado que a essa não tenha alguma relação com as **Main Area** do "Grupo Orion"
    Quando "John doe" tentar acessar a pagina de "**Clientes**"
    Então deve-se retornar  "403, fobbiden"

Cenário: Autorização a clientes como relacionado com restrição
    Dado que "John doe" tenha acesso direto ao Edifício "CECNC" 
    E dado que tenha alguma relação com as **Main Area** do "Grupo Orion"
    E dado que tenha restrições para o tipo de "**Clientes**"
    Quando "John doe" tentar acessar a pagina de "**Clientes**"
    Então deve-se retornar  "403, fobbiden"

------

## Perguntas gerais

Fornecedores
- Os campos na criação de fornecedores devem ser abertos a edição? - _"Não, e nem apagáveis, caso ocorra algum problema, o ideal e mudarmos manualmente."_

- Uma pessoa do prédio X e uma do prédio Y, por mais que não se conheçam, podem ver os fornecedores uma das outras? - _"Não tem problema"_

- O que acontece se uma pessoa do prédio X criar um fornecedor com um nome e uma pessoa do prédio Y tentar criar o mesmo fornecedor, com um nome muito parecido? Não deve existir quaisquer padronização? - _"Não tem problema"_

Clientes
- Se o intuito e apenas mostrar, os prédios que são clientes. Não faria mais sentido apenas criarmos os campos do card na propriedade "Info" do DT?  - _"Poderia ser feito diretamente no DT, mas ela indicou que a ideia e ser o mais simples possível, para não atribuirmos a nós mesmos a responsabilidade em eventuais falhas"__

- A aba clientes deve mostrar apenas os clientes da "Orion"? Os clientes dos clientes não seriam inclusos? - _"Completamente interno, ou seja, temos que garantir que quem vai usar deva tenha uma mainarea relacionado a orion. Mas tambem deve ser restrito aos prédios os quais a pessoa tem autorização"_

------

### Requisitos 

Autorização por função. (Editar, Visualizar, Apagar)