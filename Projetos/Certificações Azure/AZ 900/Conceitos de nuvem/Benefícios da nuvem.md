#az900
### Alta disponibilidade

Como o nome sugere, quando referimos a alta disponibilidade, estamos falando da capacidade de um recurso "X" (webapp, banco, function e etc.) está disponível em relação ao tempo.

Isso significa que enquanto mais tempo, um recurso esteja acessível, online, disponível ou funcionando, melhor, em termos gerais de disponibilidade.

Esse termo tambem e fortemente relacionado com o termo "SLA", basicamente, se trata de um contrato que estabelece um limite mínimo de (mas não limitado só a isso), disponibilidade.

Esse valor reflete em um percentual, que e mensurado, pela relação entre o **UP/DOWN Time**.

> [!NOTE]
>   Em um cenário, atípico, onde o tempo de down time, ultrapasse o valor estabelecido pelo contrato de SLA, o consumidor do recurso, deve pelas politicas da Azure, ser recompensado com voucther de credito, pela indisponibilidade.  

### Escalabilidade

Trata-se da capacidade de aumentar os recursos de um ambiente para suprir determinada demanda.

Em cenários de onpremisse, decisões de escalabilidade costumam ser mais previas e permanentes, na nuvem isso tende a ser mais flexível.

Em suma, temos dois conceitos principais:

**Escalabilidade Horizontal**: Diz respeito a capacidade de adicionar mais maquinas para dividir a carga

**Escalabilidade Vertical**: Diz respeito a capacidade, de aumentar os recursos físicos da(s) máquina(s) no ambiente.
### Elasticidade

Trata-se da capacidade de ajustar dinamicamente os recursos, de acordo com a demanda, podendo ser automaticamente ou não.
### Confiabilidade

A capacidade de um sistema de funcionar de maneira consistente e previsível durante o tempo necessário. Evolve tanto a capacidade de evitar, quanto a de se recuperar de falhas rapidamente.
### Resiliência

E a capacidade de se recuperar falhas rapidamente e garantir a disponibilidade mesmo em cenários de erros/falhas.