- [x] Descobrir o que e **improvement scores**
- [x] Para buscar os scores, teriamos que fazer uma busca mês a mês, o ARC devolve apenas um mes por vez
- [x] O data improves são alcançáveis pelo data?
- [x] Reviver conversão automatica


- 10391003
- 9862308
- 10389869

---------------------

Me parece correto tomar algumas suposições como verdade, em relação a como deve ser montado o objeto de **"sla"**

- Eficiência e um calculo.  Me parece correto pensar que ele deva ser algo como o numero de faliures do mesmo tipo para um determinado client.
- Esse "Mesmo tipo", sendo de fato o problem_name. 
- deadLine, se trata da diferença entre: 
  included[*].attributes.max_target_status_date - included[*].attributes.start_status_date 
- A lista de failuresOutOfDeadline, se tratam dos faliures cujo o deadline se passou. 
- Me parece que a arrumação desse objeto e dado primeiramente pelo nome do chamado, agrupando os failures por nome, o que caracterizaria um "tipo". Depois seria plausível relacionar os failures a lista de **failuresOutOfDeadLine** ou adicionando no totalFailures.
- As categorias parecem levem em consideração o problem_name inteiro, então não e "Controle de Acesso", seria algo como "Controle de Acesso - Disponibilidade dos Equipamentos", nome completo.

TypeSLA, também me parece o mesmo problem_name

-----

### Ideias

Não me parece correto fazer uma nova request ao infraspeak nesse momento, pelo menos. 
Basicamente com os valores associados as failures (chamados) já conseguiríamos devolver essas estatísticas de SLA, de certa forma, sim haveria a necessidade de uma busca no infraspeak, afinal não armazenaríamos os dados no banco, isso não faz sentido. 

O queryHandler, pode simplesmente buscar os chamados do período especificado, e a partir disso, definir quais estão ou não abertos, não haveria necessidade de um modelo

### Modelo


Efficiency = A eficiencia e calculada pelo numero de chamados realizados divido pelo numero de de chamados total multiplicado por 100.

_E considerado um chamado realizado, ele simplesmente ter sido feito ou necessariamente deve esta dentro do prazo?_ 

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
**Atualizado em** = data[*].attributes.**update_at**  - data[*].attributes.**report_date** 



- Qual o critério para esse percentual? Nos cartões de chamados? 
- Porque so mostra os detalhes dos que estão atrasados? 
- A categoria do SLA e o mesmo motivo das chamadas? 

-----
Perguntas: 

- Como e feita o calculo de eficiência deve ser feito? Não parece ser apenas o percentual que estão dentro ou fora do prazo
- Como e feito o calculo da eficiência da categoria? 
----


- auditStats,
- buyOrders,
- client,
- completedBy,
- elementRegistries,
- entity,
- events,
- eventsPlanned,
- files,
- gatekeeperAnswerRegistries,
- networkStatus,
- otherCosts,
- participants,
- pausedBy,
- reminderRules,
- reminders,
- requests,
- scheduledWorkSlas,
- startedBy,
- stock,
- stockTasks,
- survey,
- surveyFeedbacks,
- work,
- realStartDateEditedBy,
- completeDateEditedBy,
- failureScheduleMapping




--------


- client,
- costCenter,
- entity,
- events,
- eventsPlanned,
- failure,
- files,
- firstWorkScheduled,
- gatekeeper,
- gatekeeperNotifications,
- interventions,
- lastWorkScheduled,
- locals,
- locations,
- previousWorkScheduled,
- nextWorkScheduled,
- ongoingWorkScheduled,
- operators,
- responsibles,
- supplier,
- technicalSkills,
- workInterventions,
- workMaintenanceProcedures,
- workNetwork,
- workPeriodicity,
- workReminderRules,
- workSchedules,
- workSlaRules,
- workType,
- workUsageTrigger,
- workAutoSchedule,
- workNotifications


-----

Primeiro, filtro de classificação de periocidade, pode ser dado pelo campo de **"recurrence"**.

### Ideias

Precisamos fazer uma requisição cruzada, primeiramente para os scheduled works, usando o expanded work, e depois para cada um dos works, nesse caso, teriamos quer montar esse relacionamento, de forma que possamos filtrar as os clients.

-----
### Modelo

**Nome** = work - data[*].attributes.name
**Data** = ScheduledWork - data[*].attributes.start_date
**Local** = work - included[0].attributes.full_name
**Recorrência** = work - data[*].attributes.periodicity
**Status** = ScheduledWork - data[*].attributes.state
**Tipo** = work - data[*].attributes.name
**Observações** = ScheduledWork - data[*].attributes.observation




_Um work pode esta relacionado a varios locais._ Pelo visto, e pego apenas o primeiro item nessa lista de locations.

------

**Organizar as perguntas:** 

- [x] Como e feito esse percentual de SLA dentro das categorias?
- [ ] O que as observações dentro das preventivas?
- Qual a abordagem faz sentido usar para buscar as preventivas? 

**Organizar ideias:**

- Como poderíamos buscar os "works" para um cliente especifico de forma eficiente? 
	- Enitity e Client são as mesmas coisas?

_Não mas os works são relacionados com client, posso usar isso para filtrar a buscar usando o included_


Vamos tentar uma nova abordagem, procurar os works relacionados aos locais, e relacionar os works aos schedules a partir disso. 


-----

**Caminhos para filtrar os scheduled works aos clients_id:**

Por locations, não tenho relação alguma em que eu encontre os works. 
Por failures, não tenho relação alguma em que eu encontre os works. 
