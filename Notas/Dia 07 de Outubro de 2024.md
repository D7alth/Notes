Tem no mínimo 4 funções que são pontos de entradas para o banco, ate onde consigo ver, todas atualizam as mesmas propriedades, mas com logicas diferentes: 

-----
## IoTHubToDigitalTwins

 se trata de um [[EventGridTrigger]], que atualiza medidores com base em uma mensagem no evento (eventGridMessage).

Pelo visto, usa Reflection para atualizar os metadados do medidor, e as salvas na tabela de "NominalRecords" usando o método "SavePropertyInDb".

> [!NOTE]
> Me parece que o a tabela "NominalRecords" se trata de um "Log" das alterações no DT, ainda preciso comprovar isso com alguns testes.


Também atualiza as propriedades alteradas pelo reflection, no Json do data do DT e atualiza a tabela de Digital Twins. 

**No geral, atualiza um DT especifico, por via de uma mensagem**

------
## UpdateDigitalTwinsAreas1Min

**UpdateDigitalTwinsAreas1Min** - Se trata de uma TimerTrigger de 1 minuto, que atualiza a hierarquia inteira, de todos os DT's no banco. 
#### Primeira etapa 

Carrega uma hierarquia, em conceito semelhante a nossa, mas sem dividir por profundidade e sim apenas os relacionamentos da tabela de relationship junto com os modelos, de forma que, no método "UpdateHierarchy()", ele vai fazer o Update dos filhos apenas para os que não são medidores.

Ou seja, a cada 1 minutos, ele carrega a hierarquia inteira de todos os nós no digital twin, e faz o relacionamento usando a tabela de **relationehip**. 

Dessa forma, temos duas queries de **Select All**, com um sorting complexo feito diretamente pelo código. 

Na pratica, utiliza o método "**GetAllTwinsHandlers**" para buscar via reflection os modelos (todos de medidores), ao todo 21, o que me sugere que seriam todos os de medidores disponíveis. 

E por fim o método "**GetAllTwinsHandlers**" usa o método **"GetAllTwinsHandlersFromModel"**  para buscar os twins, diretamente do banco, para cada modelo da lista, essa sim retorna a lista de DigitalTwinHanlder, que será utilizada pela função que monta a hierarquia "**LoadHierarchy**", que faz o processo de montagem da hierarquia, com base nos relacionamentos da tabela de **Relationships**

Ordem de criação da hierarquia: 

- DigitalTwinsHierarchyHandler - Objeto de hierarquia
- LoadHierarchy - Primeira iteração, busca os medidores
- GetAllTwinsHandlers - retornar os modelos dos medidores por reflection
- GetAllTwinsHandlersFromModel - retorna os medidores
- GetAllRelationships - itera em cima da lista de DT's para buscar as relações
- LoadHierarchy - monta um dicionário de hierarquia, para **todos** os DT's 

#### Segunda etapa 

Primeiramente, para cada um dos  handlers que tenha um dos modelos iguais ao: 

"meter",
"environment",
"floor",
"wing",
"tower",
"building",
"campus",
"city",
"state",
"country",
"enterprise"

vai ser ter suas propriedades _alteradas?_ para os tipos adequados, no dto? 

Antes de salvar alguma alteração no banco (ate esse momento, ele apenas alterou as propriedades via reflection). 

E checkado os alarmes. 

**Checkagem dos alarmes**

Resumidamente, para cada um dos DT, da hierarquia completa, ele roda em paralelo uma task para cada tipo de checker de alert, ate onde pude ver, as notificações tem uma pipeline de verificação parecida, onde temos duas rotas possíveis. 

Uma para alerta de relacionado a modelos não medidores.

> [!NOTE]
> Importante ressaltar que não tem nenhuma verificação de modelo para nenhum tipo de alerta, o que me faz pensar que se trata de modelos diferentes de medidores, seria as propriedades e posteriormente pela propriedade de "childrenAlertConfig", que não poderia ser null para funcionar. 

Onde via reflection, e pego os consumos tanto do node quanto dos filhos do node, é e utilizado essas propriedades para verificar se o maior consumo entre do próprio lugar e dos filhos ultrapassa uma outra propriedade "Threshold".

Em caso positivo, 

e posteriormente, o e commitado (salvo na tabela do DT).

Pelo visto, as notificações estão de fato, relacionados a uma timeTrigger, porem, eles tem certo critérios para um possível commit no banco, um deles sendo o Threshold, e o outro sendo o grupo de atualização a qual eles pertencem, podendo ser, diário, semanal, mensal, anual, mas também percebi que só um pequena minoria segue esses critérios, a maioria, tem o valor da próxima notificação definida highcoded, por reflection. 

Sempre que os if dão match, ele manda a notificação via EMAIL. 

Lembrando, isso tudo, para cada um dos DT's. 

Por fim, o DT e atualizado, isso e, as propriedades que foram atualizadas com reflection e os alertas, foram definidos, atualizados e enviados. 

Sendo que, ate o final desse fluxo, não necessariamente e salvo qualquer valor referente a notificação, apenas enviada, e caso caia no caso onde seria salvo, o valor seria salvo na tabela "NumericRecords"

#### Resumo da execução

-  E montado a hierarquia completa para todos os DT's, usando um select all na tabela de digital twins e na tabela de relation_ships
- E montado e feito o sorting dos nós
- Para cada um no na hierarquia, que não seja medidor e usado os valores dos childrens (pelo menos os diretamente relacionados pelo relation_ship) para atualizar seus valores. 
- Para cada um no na hierarquia, que não seja medidor, e checkado os alarmes
- Os alarmes tem diversos critérios para serem "Lançados"
- Por fim, o JSON e atualizado com as informações do reflection, referente ao DT
- E commitado tudo isso para apenas um DT, por vez. 

Então, só e atualizado o Numeric / nominal records, nessa execução, ainda que envolva as notificações.

------

## UpdateDigitalTwinsAreas5Min 

Mesmo plano de execução que o de 1 min, mas em 5.


Entre - 2023-04-12 14:47:36.994 -0300
E - 2023-03-28 08:11:57.946 -0300