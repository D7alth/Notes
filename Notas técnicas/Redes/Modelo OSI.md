Esse modelo descreve uma relação mais aprofundada entre os componentes que compõem a internet, quando falo em modelo OSI, predominantemente estou falando de protocolos de comunicação de redes. 

O modelo tem como base em 7 camadas diferentes (Layers), as quais manipulam as informações de maneiras diferentes, para propósitos diferentes, elas são: 

7. Aplication
6. Presentation
5. Session
4. Transport
3. Network
2. Data link
1. Physical

**Aplication Layer**

Camada responsável por prover os protocolos de comunicação entre a aplicação provedora e o usuário, um dos protocolos que podem ser dado como exemplo e o "**BitTorrent**", pois, esse protocolo conversa diretamente com o usuário. 

> [!NOTE]
> Uma questão interessante a ser levantada seria, qual a finalidade desse modelo? Em questão de arquitetura, teríamos um padrão de fato, que tem com ideia facilitar a comunicação entre as tais redes, onde sim, existiria uma possibilidade de existirem redes que propositalmente não seguem esse padrão para dificultar ou inviabilizar a comunicação externa, ou seja, alguém capacitado poderia rearranjar o modelo ou criar o seu próprio se comunicando da forma que achasse melhor, tendo os mesmo componentes, mas com uma estruturação logica diferente. 
> 
> Ou seria uma questão mais relacionada a fabricação dos componentes, ou seja, caso essa pessoa, compre um roteado qualquer, não existiria a possibilidade de por si só, mudar as configurações de como os pacotes seriam tratados, afinal seria como um padrão menos logico "arquitetural" e sim algo fechado, onde os próprios componentes existentes já trabalhariam assim. 

### Presentation Layer

Essa camada e responsável por formatar os dados a serem apresentados, de forma que a aplicação provedora teria essa responsabilidade e por sua vez, entregaria ao client.

Um bom exemplo, seria o Azure Blob Storage, que para compartilhar com o client de maneira eficiente e legivel existe a necessidade de especificarmos o "Content-type" sendo "image/webp".

Esse layer segue esse principio. 


### Session Layer

Essa camada e responsável por "orquestrar" a comunicação e coordenar o fluxo de dados entre a aplicação e o client.

Também prove mecanismos de segurança e métodos para lidar com falhas ou percas de pacotes. 