#Network #TechDictionary #TechNotes

Os dois componentes mais ementais e fundamentais para entendermos o funcionamento e a necessidade do Rabbit são, além do conceito geral de [[Mensageria]] e [[Event Sourcing]]:

- Filas:
	_Trata-se da mesma definição vista em [[Mensageria]], dentro do Rabbit a mesma tem algumas especificidades. Podemos citar_
	- **Persistência**: _No rabbit, podemos persistir filas a fim de manter a aplicação ainda mais resiliste mesmo que o message broker reinicie_
	- **Auto delatável**: _Quando uma fila chega a não ter mais consumidores conectados, por padrão a fila e deletada_
- Exchange: 
	_Agentes de roteamento das mensagens para as filas, para isso, utilizam de atributos no cabeçalho, routing keys ou ate bindings. Esse e o ponto onde o publicador se conecta para realizar a comunicação com esse Broker_
 - Binding: 
	_Esse e ponto que faz a conexão entre a Exchange e uma fila. Posso chamar de canal ou qualquer coisa que abstraia essa ideia_
 - Routing Key: 
	_É um atributo adicionado ao cabeçalho da mensagem, serve como uma identificação para o Exchange decidir como rotear a mensagem para os canais (bindings) estabelecidos_

### Aprofundando em Exchange

Temos tipos específicos de Exchange, que basicamente indicam o objetivo daquela conexão. Por exemplo, posso ter um publicador, que esta interessado em passar suas mensagens para todas as filas possíveis, ou apenas para um grupo e assim por diante. 

Temos os tipos: 

- Direct
- Default
- Topic
- Fanout

#### Direct

Envia as mensagens para a fila que de um Match completo com a Routing Key. 

Por exemplo, no cabeçalho de uma mensagem, temos o parâmetro de Routing Key : "xpto", esse tipo de Exchange, tentaria rotear essa mensagem diretamente para a fila "xpto".

#### Default

Igual ao **Direct**. 

#### Topic

Envia as mensagens para a fila que de um Match parcial com a Routing Key, porém, permite a relação dessa mensagem para múltiplas filas. 

Basicamente, podemos para o mesmo Routing Key ter várias filas relacionadas. Por exemplo, para a Routing Key: "xpto", poderíamos ter as filas: "process/xpto", "cars/xpto" e etc..

#### Fanout

Envia as mensagens para todas as filas registradas na Exchange, independentemente de estarem ou não dando Match com as Routings Keys. Funciona como um Broadcast. 

