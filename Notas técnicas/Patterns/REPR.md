Um padrão interessante, o qual visa, simplificar o processo de desenvolvimento de API's, tipicamente relacionado ao padrão arquitetural [[MVC]], e análogo ao padrão "[[Vertical Slice]]". 
 
A ideia geral, e o ponto mais forte desse padrão e tentar relacionar a camada logica, não a um controller como no caso do [[MVC]], mas sim a um componente que abraça toda logica de processamento de um ponto de extremidade, isso incluindo desde o recebimento e tratativa das requests a sua resolução e devolutiva. Na pratica, seria o mesmo que falar que teríamos pelo menos uma classe, cujo o único objetivo, seria tratar a logica relacionada a uma endpoint.   

Esse componente, geralmente e dividido em 3 sub-componentes: 

**Request**: Essa seria responsável receber o input do usuário. 
**Endpoint**: Onde deve ser processada a logica. 
**Response**: Seria o "modelo" de resposta, semelhante ao conceito geral de DTO. 

E completamente visível, que o padrão existe nas lacunas que o [[MVC]] tem. Sempre pareceu muito contra intuitivo criar API's, cuja não existe uma VIEW propriamente dita, onde seria executada a logica da aplicação, pelo menos no modelo [[MVC]]. 

Sem contar com a tendência deles de com o aumentar do projeto, ficar cada vez com mais dependências e mais inchados, isso causa uma enorme dificuldade de manutenção dos controllers, onde existe intricadamente no conceito do controller uma violação do [[SRP]] (Single Responsability Principle).

