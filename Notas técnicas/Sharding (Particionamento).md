#TechDictionary #SystemDesing

Trata-se de uma técnica de particionamento de dados, especialmente útil quando se trata de escalonamento horizontal, ou seja, como detalhado em [[Benefícios da nuvem]], aumentar o contingente de maquinas para resolver ou suprimir uma demanda ou se adaptar a uma carga. 

Importante ressaltar que Sharding e uma das técnicas relacionadas ao _P_ do [[Teorema CAP]].

Essa técnica e particularmente especial em sistema de com alta carga de dados, que dependem muito de leituras e escritas e lidam com um numero de registros alto o suficiente para não conseguir manter uma performance adequada nessas consultas.

A técnica por si só, garante alguns pontos interessantes no ponto de vista arquitetural, eles incluem: 

- Disponibilidade
- Performance
- Escalabilidade
## Funcionamento

No processo de sharding os dados são divididos com base em uma chave de particionamento, isso pode variar com base no **método de particionamento** sendo que cada um deles tem seus prós e seus contras. 

Podemos fazer esse particionamento com base em um atributo identificador de uma determinada entidade / agregado ou outro atributo que sirva como base para esse particionamento, como a data.

Poderíamos particionar por range por exemplo, o que nos levaria para um dos métodos de particionamento, que abordarei em detalhes mais a frente. 

Logo, criamos uma "partição especializada" em um determinado assunto ou fazendo uma analogia ao mundo real. 

_E como se tivéssemos diversos tipos de canetas em uma caixa, para ser especifico, tem exatamente 20 mil canetas, de todos os tipos, incluindo do mesmo modelo, mas todas tem o numero de código diferente. A questão e a seguinte, se todas as canetas estão em apenas uma caixa, seria difícil encontrarmos uma de cor, tipo, e código especifico. Por isso, separaríamos toas as 20 mil canetas em 20 caixas diferentes. Poderíamos elencar uma especificidade ou propriedade em comum para distribuirmos as canetas nas caixas, por exemplo, podemos ter uma caixa cujo vamos adicionar apenas canetas com o final do código de identificação igual a 18 e outra seguindo o mesmo principio mas para o final 81 e assim por diante... Isso nos possibilitaria identificar mas facilmente onde poderíamos encontrar uma caneta especifica_


