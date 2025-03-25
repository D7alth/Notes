#Patterns #TechDictionary #TechNotes 

O padrão Pub/Sub (Publisher/Subscriber) e um modelo arquitetural e um padrão de 
comunicação assíncrona e orientada a eventos. Relacionada a sistemas distribuídos.

Ele resolve o problema de conectar múltiplos produtores de eventos (Publisher) a múltiplos consumidores (Subscriber) de forma que não haja vinculo direto entre eles. O que por sua vez, aumenta a escalabilidade e manutenibilidade, pela falta de acoplamento.


Em sistemas complexos, é comum haver múltiplas aplicações ou serviços interessados nos mesmos dados. Nesses cenários, gerenciar conexões ponto a ponto (um produtor para vários consumidores) cria dependências rígidas e aumenta a complexidade. A ideia geral e reduzir o acoplamento por meio de um Message Broker.

### Funcionamento

1. Publicadores enviam mensagem a tópicos que atuam como canais lógicos para categorizar dados. 
2. Assinantes registram interesse em tópicos específicos para receber apenas as mensagem relacionadas aos tópicos de seu interesse. 
3. Um Message Broker atua como intermediário, gerenciando o armazenamento, roteamento e a entrega de mensagens. 

Os principais componentes do padrão incluem: 

- Tópicos: Definem o escopo de mensagem que podem se publicadas e consumidas. 
- Filas (Queues): Podem ser usadas para armazenar mensagens temporariamente antes de serem entregues.
- Subscriptions: Configurações que ligam consumidores a tópicos com filtros opcionais. 

### Message Broker

O papel do broker nesse padrão e além de garantir a persistência.
- Filtragem: Enviar mensagens apenas para consumidores interessados
- Roteamento: Distribuir mensagem para múltiplos assinantes, aplicando estragais como [[Broadcast]] ou filtragem por regra. 

### Exemplo práticos

1. Sistemas IoT: Sensores publicam dados em tópicos como **meter/inverter**, e consumidores assinam esses tópicos para monitorar ou obter as informações.
2. Notificações em massa: Um aplicativo de redes sociais publica notificações em tópicos baseados no tipo de evento, como novos_amigos, e os consumidores recebem apenas as notificações configuradas em suas assinaturas. 
3. HTTP: Um cliente HTTP faz uma request, no tópico de services/food, para ser feito, assim que o subscriber de como concluido, faz uma segunda request HTTP para services/delivery.


> [!NOTE] Publisher
> Qualquer agente, que possa enviar um evento para a aplicação.

### Padrões complementares

O Pub/Sub pode ser combinado com outros padrões, talvez seja interessante pesquisar a respeito: 

- CQRS
- Event Sourcing
- Dead Letter Queues (DLQ)

### Representação

O diagrama abaixo ilustra o fluxo típico do Pub/Sub:

[Publisher] --> [Message Broker] --> [Subscriber A]
                           --> [Subscriber B]
                           --> [Subscriber C]


Em desenho

![[Pasted image 20241216123626.png]]
