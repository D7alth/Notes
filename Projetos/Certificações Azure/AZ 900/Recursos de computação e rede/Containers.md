#az900

Trata-se, dos recursos de virtualização em containers, oferecidos pela Azure, não tão curiosamente, classificado como um Paas, o que faz sentido, tendo em vista a sua finalidade. 

A definição mais simplória, pode-se tratar um container, como uma "espécie" de ambiente virtualizado, tal qual, uma VM, entretanto, o modo de operação difere em um ponto interessante, onde nas [[Maquinas virtuais]], havia uma necessidade entisica de separa o kernel da maquina física, via um "hypervisor", que não só separava todos os recursos como também, emulava o sistema operacional inteiro da [[Maquinas virtuais]], criada.    

Aqui podemos dizer que, existe um grau de separação a nível de sistema operacional, referenciando todo esse processo de separação quase física, pelos mecanismos de virtualização. 

Ainda assim, no artigo [[Maquinas virtuais]], e deixado claro que para certos fins, como rodar vários aplicativos em um ou vários host virtual, essa abordagem tem total sentido, ainda que possa ser mais complexa.

Voltando ao assunto. A tecnologia dos containers, e um pouco diferente, partindo do proposito que, por mais que no lato senso, a criação de [[Maquinas virtuais]] tenha como objetivo, utilizar apps do sistema para prover algo a alguém, ainda podemos voltar a ideia do sistema operacional, necessariamente, uma maquineta virtual, tem um sistema operacional totalmente gerenciável e personalizável. 

Logo me vem a mente, que o proposito para uma maquina, de forma mais abstraída possível, seria de prover um sistema operacional. Ate certo ponto claro.

Em contra ponto, abstraindo e especializando esse conceito, temos os containers, cujo o proposito, não se prende ao sistema operacional, mas sim as aplicações que rodariam nesses sistemas.

Pois bem, essa separação entre a maquina real e a aplicação fica um pouco mais tênue, em visão desse proposito, o mecanismo de conteinerização, funciona de forma diferente das [[Maquinas virtuais]], onde ele basicamente escuta, separa e atende, os "requisitos" (entenda isso como qualquer binário, biblioteca, dll ou coisa do tipo), que uma aplicação possa vir a solicitar. 

Uma forma de "Emular" um sistema operacional onde aquela aplicação rodaria, mas de forma mais inteligente, pois, para um ambiente virtualizado mais simples, muitos recursos do SO são meramente desnecessários.  

Na literatura, esse mecanismo e comumente chamado de Engine de conteinerização, e ela e responsável por fazer esse gerenciamento, entre os ambiente das aplicações, que por sua vez, são individuais e separadas, por mais que esse mecanismo, distribua certos recursos de forma que uma aplicação consiga buscar da mesma fonte, mas isso não gera acoplamento ou dependência entre elas.

Um ponto importante a se ressaltar, e a capacidade de utilizar o kernel da maquina física (host), isso e importante também para a distribuição, ainda que de modo isolado, as aplicações conseguem receber recursos partindo do kernel do host. 

Também e importante ressaltar, que um contêiner e significativamente mais leve em comparação com [[Maquinas virtuais]], tendo em vista todos os pontos mencionados. 
