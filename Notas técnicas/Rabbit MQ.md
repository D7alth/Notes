O mais utilizado em comunicação assíncrona entre sistemas.   

Funciona como um intermediário, entre o publicador e os consumidores, o que remete bastante ao pattern de [[Publish Subscribe]]. 

Basicamente, temos o mesmo fluxo, onde o Rabbit MQ atua como um Message Broker (intermediário), ou seja, o produtor recebe uma _requisição_ e produz um evento para o Rabbit MQ. 

> [!NOTE] Requisição
> Não estamos falando especificamente sobre um HTTP, podemos pensar em qualquer ação que haja como gatilho para o publicador. 


