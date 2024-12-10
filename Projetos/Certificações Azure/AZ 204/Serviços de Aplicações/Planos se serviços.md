Os planos de serviços, atuam como "containers" dos [[Webapps]], talvez, não um tipo de "container" de fato, ainda que se fossemos montar um diagrama, os [[Webapps]] estariam dentro dos planos de serviço. 

A ideia geral desse recurso e, definir os recursos que determinada aplicação, webapp, [[Functions]], ou qualquer outra do tipo que se encaixe nesse modelo. Por meio de uma seleção de Tiers de maquinas virtuais. 

Começando por um **Tier de maquinas gratuitos**, onde todos os recursos são compartilhados, ou seja, a maquina virtual "aluga", uma cota pequena, de CPU e processamento para cada [[Workload]], com um numero de instancias de maquinas limitadas a uma. 

A compartilhada herda as mesmas características. 

Enquanto os **Tiers básicos**, como Basic (B1), Basic Premium e por ai vai, ainda dividem esses recursos porem, esses tem um percentual da CPU disponibilizada para si. Além da capacidade de dimensionamento, aumentando o numero de instancias. 

==Importante==: As aplicações implantadas no plano de serviço, vão preencher o numero de instancias disponíveis, ou seja, se eu tenho um plano de serviço B1, com 3 instancias e uma aplicação, essa aplicação vai estar em execução em todas as 3 instancias. 


> [!NOTE] O numero de instancias aumenta o valor no plano de serviço?
> _Resposta:_ Você será cobrado por cada instância alocada na contagem mínima de instâncias, independentemente das funções serem executadas ou não.


Por fim, as **Tiers isoladas**, são definidas como as de mais alta dimensionalidade, por se tratarem de maquinas especificas, que estão de fato isoladas, não compartilham recursos com outras diretamente, além de executarem em redes virtuais dedicadas do Azure.

