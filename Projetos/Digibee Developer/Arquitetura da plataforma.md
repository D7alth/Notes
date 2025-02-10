#Digibee

Consiste em uma plataforma baseado no [[Tipos de serviços de nuvem]] (**SAAS**), e permite ao usuario criar todo o tipo de integração utilizando de LOW CODE.

## Infraestrutura

Foi criada e estruturada pensando no modelo de **cloud native**, então desde o inicio podemos pensar em componentes de **cloud native**, então toda a proteção, mecanismos e componentes que naturalmente existem em provedores de cloud como GCP ou Azure, já existem por padrão, isso porque os pipelines são executados dentro da plataforma **Digibee**, dos componentes naturais do cloud provider posso citar.

- Load balacing
- Segurança
- Cloud Armor

A base de execução dessa plataforma e o **[[Kubernetes]]**, o que proporciona ainda mais resiliência e escalabilidade, o que tambem e relacionado com os [[Benefícios da nuvem]]. 

Um ponto interessante e que ela e divida em vários componentes, como por exemplo: 

- Api Getaway, completamente nativo. 
-  Triggers, agem como ponto de entrada para os pipelines
- Fila nativa, garante maior resiliência e um processamento assíncrono  
- Pipeline engine, interpreta o pipeline montado e o prepara para execução
### Pipeline engine

 Esse o qual interpreta as pipelines definidas e montadas na plataforma e as prepara para execução de maneira completamente isolada.

- Cada pipleline e executado em múltiplas zonas de disponibilidade 
- Todo pipeline necessita de um trigger para ser invocado. 
### Triggers

São os acionadores das pipelines, sendo que esses sim se conectam com o mundo exterior. Os quais tem N métodos de conexão.

- Rest API
- Eventos
- Agendamentos
- Filas e mensageria
- Emails
- Http
### Filas de execução

Funcionam como as filas de mensageria normais, como um [[Rabbit MQ]] ou seja, eles recebem e armazenam as entradas nos triggers e as enfileiram. Isso funciona por pipeline, ou seja, a cada nova pipeline e instanciado uma nova fila de execução o que garante uma resiliência ainda maior.  

### Observabilidade e auditoria

Tambem como um mecanismo nativo, esse garante observabilidade individual para cada pipeline.

![[maxresdefault.jpg]]