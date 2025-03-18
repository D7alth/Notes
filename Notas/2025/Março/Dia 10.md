#Craft 

Recebi apenas um overview do que devo fazer. Mas me parece que devo receber alguns dados vindo de uma base de dados ou tabela (chamaram de VIEW) com o nome de **LadyMarina**. Que deve ser acessado por algo chamdado **cargowiseone** (chamaram de repo mas não achei o repo no devops).

Preciso Criar um fluxo de faturamento (preciso mesmo?). Talvez fique em algo como invoices, no projeto CargoWise. 

Posso falar com o Fabio para validar minhas ideias.

Pelo o que o Christian falou, parece simples, vou pegar essas informações do banco, vindo dessa "VIEW" **LadyMarina** e fazer algum tipo de "enriquecimento" (ainda preciso saber o que se trata), dividir em 2 XMLs um chamado de **UniversalShipment** e outro **UniversalEvent**.

Eles serão enviados ao que eu deduzo ser uma PLL chamada "**Inbound**" que também e do CW. Que server como um coringa para as coisas do CW. 

Dentro dessa PLL, ela deve ter vários caminhos, e algum campo com vai servir de discriminador para a entrada na branch do fluxo. O descriminador e **LAM**

Também recebi um exemplo no PPL: craft-cargowiseone-invoices-compliance-sequences, pelo visto ele esta relacionado ao invoice, talvez como ponto de entrada, e tambem passa dados para o PLL de "Inbound".

### Duvidas

- [ ] Payload de entrada do invoice
- [ ] Qual a finalidade desses dados (Para min)
- [ ] Quem e o consumidor e o que faz com esse dado (Para min)

-----

- [ ] Quais e a tabela que retorna aqueles dados?
- [x] Analisar Pipeline de craft-cargowiseone-invoices-compliance-sequences
- [ ] Desenhar o fluxo de craft-cargowiseone-invoices-compliance-sequences
- [ ] Analisar a Pipeline de Inbound 
- [ ] Desenhar o fluxo de Inbound 
- [ ] Desenhar o método de integração entre os dois componentes 