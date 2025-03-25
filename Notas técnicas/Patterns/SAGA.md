#Patterns #TechDictionary #TechNotes 

Aplicado entre microsserviços em cenários de transação distribuída.
### Ideia geral

A ideia desse pattern e não criar mas atribuir em uma sequencia de transações distribuídas em diversos serviços, "**mensagens**" ou "**registros**" dessas transações em cada um dos serviços. 

Poderíamos pensar no seguinte, temos um sistema, que roda em 3 serviços diferentes em locais diferentes e com bancos diferentes.

Imaginamos que, o primeiro serviço faça apenas a "limpeza" e validação dos dados em um formato especifico, por definição, temos aqui uma "[[Transação]]", não se trata de algo que será persistido, mas não muda o fato. 

Esse serviço manda esses dados para o próximo que cria um usuário com base nos dados, e os persiste no Azure B2C, e no seu próprio banco registra apenas o ID para usos futuros

Por fim o ultimo, dispara um email para esse usuário criado e salva o alguns dados do usuário, junto com o ID do modelo do email. 

Não entrando no mérito de funcionalidade nem de se faz sentido ou não esse sistema, o fato e que temos 3 transações diferentes, 3 processos em 3 serviços diferentes.  

A ideia do padrão e para cada um desses serviços com transações, ter um "mapeamento" que garante que para cada novo serviço, a [[Transição]] do serviço anterior foi feita corretamente.

E em caso de falha absoluta, ter uma series de "**Contramedidas**" que desfazem os passos e transações anteriores. 

### Implementações

Para que tenha esse comportamento, existem duas maneiras de fazer a implementação desse padrão. 

**Orquestração**

Temos um componente central, que informa aos participantes quais transações locais executar. O orquestrador manipula as transações com base em eventos, ele executa as ações de SAGA, armazena e interpreta os estados de cada tarefa. 

Funcionando de certa forma como uma "maquina de estado" para os serviços participantes.

**Coreografia**

Cada um dos participantes trocam eventos entre si, nessa implementação, cada transação publica eventos de domínio que disparam as próximas transações. 