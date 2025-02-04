#az900

Me parece um recurso análogo a uma rede corporativa local, ou como seria estruturada pensando em um ambiente on-premise, certamente, adaptado para o contexto de cloud. 

Basicamente conceitos gerais de gerenciamento de redes, tais quais como, criação de grupos de redes menores dentro de um range de IP (subnets), ou a configuração de rede para [[Maquinas virtuais]] especificas. Podem ser herdados, em termos gerais de comportamento. 

No que se trata especifico de Azure, as redes virtuais, são tratados como "recursos", muito atrelados e comumente necessariamente relacionado a boa parte dos recursos de IAAS ([[Tipos de serviços de nuvem]]).

A Azure permite configuração de ponta, comparável com uma configuração local, dando suporte a pontos de extremidades privados e/ou públicos (IP's), dependendo da configuração. 

Além de fornecer meios para os recursos se comunicarem dentro das redes virtuais especificadas. 

> [!NOTE]
> Como conceito, me parece errado, seguir o trecho da documentação onde se refere a rede virtual como uma "extensão" da rede local, do cliente/usuário. Talvez, seja mais correto afirmar que se trata de um conjunto de regras e definições de redes, que por meio de parâmetros estabelecidos, muda o comportamento e como os recursos dentro daquela rede se comunicam com o mundo exterior. 
> 

Também me parece certo que esse conceito, só se estenda para os recursos dentro da Azure, onde por exemplo, não existira um caso que faria sentido termos uma infraestrutura de rede baseada nas redes virtuais da Azure, onde todos os componentes, estariam fora da Azure, como, desktop, firewalls e outros do meio. 

Ainda que existam recursos de roteamento interessantes, dentro desse recurso. 

### Roteamento de trafego de rede

Existe uma personalização, em como os pacotes devem ser entregues por entre as separações logicas, locais e ate na internet. 

Podendo ser tanto por "tabelas de rotas", que definem as regras que serão aplicadas em relação a como o trafego deve ser direcionado. 

Quanto por BGP, que funciona como uma [[VPN]] Azure.

### Filtragem de trafego de rede 

Diz respeito, a filtragem especificamente entre as sub-redes. 
Existem algumas maneiras, de fazer certa "moderação", nesse contexto, principalmente quanto esse contexto esta relacionado a politicas internas ou a segurança, onde teríamos.

- Grupos de segurança de redes, definido com base em endereços IP's, tanto de entrada quanto de destino. 
- Outros recursos, como firewalls e afins. 

