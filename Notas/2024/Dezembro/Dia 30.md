### Sprint 63

- [ ] Registro de evento "internal command" no modulo de salvamento das faturas
- [ ] Excluir favoritos dos usúarios
- [ ] Juntar todos os requisitos faltantes, para todos os projetos.
- [ ] Subir requisitos de comparativos.
- [ ] Guia de uso para as paginas faltantes.


### Ultima atualização staging

Dia 24 de dezembro, terça feira.
PR: Employee Contracts.

----------------------

Fluxo de uso, internal command.

O tipo esta sendo salvo, e o evento e registrado como vazio.

EnergyBill add domínio de evento (IDomainEvent) =>
Tipo, EnergyBillSavedDomainEvent. Herda da classe "DomainEventBase" => 
"DomainEventBase" gera, Id e OccurredOn. _"Me parece esta relacionado com o outbox"_, herda de IDomainEvent => 
A interface "IDomainEvent", serve apenas como uma base de implementação. Como uma classe abstrata, porém, tem referencia com a classe "DomainEventDespatcher" => 
"DomainEventDespatcher", basicamente busca todos os eventos disponíveis associados a uma entidade e os move do contexto da entidade para o contexto de OutBox, onde esse sim e persistido. 


Pelo o que parece, não e persistido nenhuma mensagem especificamente para o internalcommand. Ele apenas tenta processar os comandos internos. 

Mas isso levanta uma duvida, se não tem nenhuma mensagem sendo salva, como ele salva o ID e o tipo e a data que foi enfileirado?

O CommandScheduler, cria um ID, um Type apartir do fullName do command e o EnqueueDate. Tambem adiciona o data. Pode ser aqui o problema.

Estranho,  ele tem uma instancia por life time, não deveria ser uma por escopo?

O Evento que dispara o enfileiramento não esta no domino, o que dispara ele? 

Pelo visto o outBox chama ele, não são padroes diferentes?


Foco nesse ==CommandsScheduler==


Pelo o que eu estou entendndo, o evento de dominio de salvar a bill gera um evento de notificação. Porem o handler não esta sendo chamado.


O CommandHandler de EnergyBillSavedDomainEventNotification e disparado (para criação), apenas a pois o dispose dos objetos de notificação. Logo ele sempre e nulo. 


O metodo, ClearAllDomainEvents, não limpa a lista de domainEventsNotifications do DomainEventDispatcher, mas limpa da entidade. O que e potencialmente perigoso. 


O problemas esta no outbox, basicamente ele esta dando como "processado" sempre no minuto seguinte a sua criação. Mesmo sem publicar o evento.


-----------------


Duvidas do dashboard customizado

Ordem de prioridade.

E nos casos de precisarmos de propriedades diferentes nos sensores (custmowidts)
- Endpoints que mostrams quais propriedades por tipo de sensor

Os requisitos, os dois primeiros são de salvar widget predefinido e salvar template