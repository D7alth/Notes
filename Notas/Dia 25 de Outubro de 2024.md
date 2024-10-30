Continar as tasks do dia [[Dia 24 de Outubro de 2024]]!

-----

## Tarefas de hoje

- [ ] Fazer deploy da 1.10 em produção
- [ ] Revisar o código do ARC Score


----  

Ao invés de termos um método "Convert", que de fato faz a conversão, retornando o valor, a unidade e quantidade de casas decimais movidas. 

Devemos quebrar a responsabilidade desse método, em pelo menos 3

- Um para validar, se a conversão se trata de uma conversão valida, e retornar uma exceção  caso não seja, e caso seja, retornar a nova unidade de medida
- Um para mapearmos, o tipo de conversão que deve ser feito, e retornar o valor que será usado na operação 
- E por fim, a operação de fato, onde poderíamos ter um "convert", ou simplesmente pular esse passo, e fazer todos os cálculos dentro do handler. _O que você achar melhor_

