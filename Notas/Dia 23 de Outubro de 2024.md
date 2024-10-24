Tenho que perguntar algumas coisas sobre o ARC, principalmente sobre o funcionamento desse modulo. 

Afinal tem varias telas, e a IRIS já tem uma integração. 


- Em termos de gerais, qual o objetivo desse INFRASPEAK? 
_Quero saber até onde vai ser necessário criar commands,  me parece uma pergunta muito importante, e importante saber o o objetivo real, isso deve me responder a maior parte das perguntas_


- Vamos da suporte a consultas e a 


- Como vai ser feito o acesso aos dados? 
_E bem provável que fale algo como: via API_ 
- Quem prove esses dados?
_A ideia e entender se precisaremos_


-----

e importante, pensar em uma forma viável de garantir que um client não possa requerer outro dentro do mesmo token.

Consigo ver algumas possibilidades para isso. 

#### Opção 01 

**Ideia:**
Poderíamos, salvar no nosso banco uma relação entre o **NODEID** e o token, nesse caso, teríamos que lidar com os nodesId nas requests, ou seja, para cada nodeId requerido, teríamos que buscar o name dentro do data dele. 

Seria simples, se partirmos do pressuposto, que lidaríamos apenas com os nodesId que são diretamente as areas que vamos pegar o nome para montarmos filtrarmos. Mas isso tambem implica em para cada request, guardarmos os json inteiro na memoria, para podermos fazer a filtragem. 

![[Pasted image 20241023091552.png]]

**Autorização:**
Nesse caso seria simples tratar os cenários bases de autorização, ainda que, para casos uma boa parte dos casos, não seja abrangível. Basicamente, os nodesId requisitados, teriam que necessariamente ter autorização para serem consultados. 

**Problemas:**
Essa abordagem, não trataria o caso de um usuário, não ter acesso direto ao nó que teria a relação com o _'Client_Name'_. 

#### Opção 02 

**Ideia:**
A opção que me parece mais correta seria, montarmos uma tabela, que relacione um token com os nodesId, mas apenas os que estejam relacionados a um _'client_name'_, no infraspeak. 

Na request, deve ser exigido apenas os nodesId, quer representem os locais relacionados aquele _'client_name'_ de forma que, seria possível, validar se os nós requeridos, relacionados ou não com o que eu vou chamar de no _'**Root**'_, sendo esse o nó ligado ao _'client_name'_, tem ou não autorização para serem devolvidos, caso tenha autorização, devolveríamos o TOKEN do banco, juntamente com o _'**Root**'_ relacionado com as areas autorizadas, e utilizaremos o _'Root'_, como o filtro de **'s_client_id'**, e os nodesId requeridos, como os '**local_id**'. 

**Autorização:**
Essa abordagem, me parece resolver a questão das autorizações

**Problemas:**
Caso o usuário peça um nó autorizado que exista na tabela, mas não exista na resposta, ele tentaria aplicar ao filtro. Pode causar problemas
 
- Nesse caso, a API não deve retornar valor nenhum a mais, principalmente pelo fato de definirmos os  _'**Root**'_  como o **'s_client_id'**.

#### Opção 02 - Alternativa

Ao invés de relacionar um token com varias areas, podemos relacionar as "InfraspeakLocations" com os tokens, fazendo um relacionamento de 1:1.

no processamento da requests, podemos usar o DATA do _'**Root**'_ ou  _'**Roots**'_, que estão relacionados com os nodesIds passados na request, e fazer a relação entre o InfraspeakLocations de cada um, com os tokens que devem ser utilizados. 

**Pontos fortes:**
Poderiamos diminuir o tamanho da requisição, para apenas o nó requisitado.

----- 

Pelo visto, existe uma propriedade em "manutenção", dentro do json de data do dt, ela e facilmente acessível, porem, notei que na maior parte dos prédios existem (ate onde eu vi), mas nas areas desses prédios não. 

-----
# 

Fazer perguntas para o Jack, sobre algumas coisas que devemos buscar. 
- Existe alguma forma de relacionar um local_id no infraspeak, com um local no banco de dados, sem ser pelo name? 

- approvedBy,
- client,
- completedBy,
- contacts,
- costCenter,
- createdBy,
- entity,
- events,
- failureElements,
- failureElementsNetwork,
- failureOtherCosts,
- failureNetwork,
- failurePauseReason,
- failurePriority,
- failureSlas,
- files,
- local,
- location,
- messages,
- meteringRegistryFiles,
- operator,
- participants,
- orders,
- otherCosts,
- pausedBy,
- problem,
- publicMessages,
- quoteRequests,
- reportedBy,
- reporter,
- requests,
- responsible,
- responsibles,
- schedules,
- signedFiles,
- startedBy,
- stock,
- stockTasks,
- supplier,
- survey,
- surveyFeedbacks,
- tasks,
- gatekeeper,
- gatekeeperNotifications,
- gatekeeperAnswerRegistries

### Chamados

Mapeamento dos chamados (failures)

**ID** = data[*].id
**Prioridade** = data[*].attributes.**priority_text**
**Data** = data[*].attributes.**report_date**
**Local** = data[*].attributes.**local_name**
**Estado** = data[*].attributes.**status**
**Tempo decorrido** = data[*].attributes.**completed_date** - data[*].attributes.**started_date**
**Prazo** = included[*].max_target_date - included[*].**start_status_date** 
**Responsável** = included[*].attributes.**full_name**
**Tipo** = data[*].attributes.**problem_name**
**Motivo** = data[*].attributes.**description**
**Atualizado em** = data[*].attributes.**last_status_change_date**  - data[*].attributes.**report_date** 

O tipo de chamado (Operações, eventuais, internos, externos etc...), está relacionado com o nome do problema?

------

==Lembra de por nos requisitos, que deve ter um filtro, de "Classificação"==

![[Pasted image 20241023152747.png]]