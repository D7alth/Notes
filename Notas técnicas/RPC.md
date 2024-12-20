Padrão de resposta de sistemas distribuídos, poderíamos relaciona-lo com o [[Request-Reply]] ou com o [[Command-Reply]] por exemplo. 

A ideia e que a comunicação entre o Message Broker e o client seja bi direcional, de forma que o cliente possa devolver confirmações ao Broker ou fazer novas requisições.

Nesse padrão nos importamos com a devolutiva do consumidor. 

> [!NOTE] 
>  Esse padrão é útil em sistemas que requerem algum tipo de confirmação (_acknowledgement_) ou política de _retry_. No entanto, pode introduzir desafios em sistemas que demandam baixo acoplamento, já que a comunicação bidirecional aumenta a dependência entre as partes.

