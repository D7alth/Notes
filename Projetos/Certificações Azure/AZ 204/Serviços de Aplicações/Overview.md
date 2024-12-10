Os serviços de Aplicação do Azure, e um serviço baseado em HTTP, que por padrão, disponibiliza um [[Ponto de Extremidade]], para uma aplicação ou [["Workload"]], acessível. 

Também proveem **suporte a dimensionamento integrado de forma automática**, tanto vertical quanto horizontalmente. Onde para cada progressão entre os Tiers, e criado uma nova copia da aplicação/workload.

**Suporte a implantação continua**, por via de uma serie de aplicações terceiras, como o próprio azure devops, github, gitlab. Entre outros. 

**Suporte a Slots de implantação**, diz a respeito de para qual aplicação os pontos de extremidade estão olhando de fato. Por exemplo, poderíamos ter uma aplicação com dois slots de implantação, um com uma versão MVP, cujo o código esteja acessível para implantação via github, enquanto, o segundo slot, seria a aplicação de produção de fato, com o código para implantação no azure devops. 

**Suporte a implantação por container**, tanto a uma biblioteca de imagens privadas providas e configuradas pela Microsoft, quanto a implantação por imagens do próprio docker hub.

Todas as features suportadas acima, estão disponíveis para servidores baseados em Windows e Linux. Com algumas ressalvas para ambientes Linux. 