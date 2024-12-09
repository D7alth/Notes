Opção 01 : Declarar no Template cheker quais são os Alerts Chekers que devem ser ou não examinados.

**Pros**: Removeria todos os alertas inválidos. 
**Contras**: Não temos como saber para cada Nó, quais propriedades estão declaradas erradas ou simplesmente está sem valor. 

Opção 02 :  Criar um script SQL para Aumentar o threshold de todos os alertas para cada tipo de alerta

**Pros**: Aumentaria o intervalo entre as notificações, para casos onde o threshold e igual ou menor que 0, evitaria notificações infinitas.
**Contras**: O threshold e diferente entre os nós. E não resolve o problemas dos alertas inválidos. 

Opção 03 : Adicionar novo objeto que copie os valores das propriedades anteriores e verifique se o valor vindo e exatamente o mesmo 

**Pros**: Removeria alguns alertas inválidos.
**Contras**: Seria a mesma coisa que simplesmente aumentar o Threshold, por exemplo, se o alerta de consumo, envia a notificação a cada vez que o produto da subtração entre o valor da medição atual e o valor do medição no momento do alarme anterior e maior que o Threshold, verificar se a medição atual e a mesma que a medição anterior, seria apenas garantir que o valor entre esse produto será diferente, evitaria um calculo repetido, porem, o comportamento ainda seria o mesmo, se e maior que o Threshold manda a notificação, se não agenda para a próxima hora. 

Opção 04 : Adicionar propriedade nos objetos de alertas que salve o valor do produto do alerta anterior 

**Pros**: Removeria alguns alertas inválidos.
**Contras**: Seria a mesma coisa que simplesmente aumentar o Threshold, por exemplo, se o alerta de consumo, envia a notificação a cada vez que o produto da subtração entre o valor da medição atual e o valor do medição no momento do alarme anterior e maior que o Threshold, verificar se a medição atual e a mesma que a medição anterior, seria apenas garantir que o valor entre esse produto será diferente, evitaria um calculo repetido, porem, o comportamento ainda seria o mesmo, se e maior que o Threshold manda a notificação, se não agenda para a próxima hora. 


----------------------
falei com o Vitor, na verdade, os medidores poderiam estar marcando 0 na corrente e na voltagem e estarem funcionando. 

Isso nos leva a uma

Opção 5: 
Remover os checkers de alertas de Corrente e voltagem, assim como os demais que não fazem sentido

no total de alertas ate o mês 2 de 2024, foram mais de 876k de alarmes para esses checkers.

sendo que no total temos 926k

temos menos de 50k de notificações "reais". 

-----



