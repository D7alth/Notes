
A ideia de maquinas virtuais, se trata de um recurso do modelo de IAAS, onde essencialmente, na criação de tal, espera-se um servidor, altamente configurável e personalizável. 

Nesse ponto difere, em grande parte de WebApp (PAAS) por exemplo, onde o foco esta apenas oferecer uma plataforma de hospedagem.

Caso, haja a necessidade de adquirir uma tal, deve se ter em mente, que a configuração, de cada detalhe envolvendo ate a camada do sistema operacional (seguindo o diagrama de responsabilidade da Microsoft), e a que lhe torna especial, se adequando a casos mais específicos, onde de fato, existe uma necessidade de um ambiente personalizado, no que se trata de servidor. 

> [!NOTE]
> A Azure disponibiliza, recursos de criação de maquinas virtuais, tal qual um EC2 da AWS.

Esse recurso exige uma configuração um tanto mais longa, tendo em vista o fato de se tratar de um IAAS, ainda assim existem opções de **imagens** e **ISO's** pre-configuradas, para facilitar sua instanciação. 


### Dimensionamento de VMs
Inúmeros são os procedimentos e jobs, que podem ser atribuídos a carga de trabalho de uma VM. 

Podemos pensar, desde: 
- Hosting de uma aplicação
- Execução de um job ou rotina especifica
- Execução de um job em determinado tempo (CronJob)
- Servidor de banco de dados
- Proxy
- Gerenciamento de redes

e diversos outros, talvez, seja de se pensar, que uma VM, seria uma alternativa análoga ao modelo Onpremise, na nuvem. 

Ainda existe opções de agrupamento de VMs, criando aquela topologia de alta disponibilidade.

==CRIAR UM DESENHO / PACKAGETRACER PARA EXEMPLIFICAR==

Essa estratégia, pode ser aplicada, para um infinitude de topologias e arquitetura de sistemas.

E para esses agrupamentos, temos dois tipos de conjuntos, que podem ou não serem usados em conjunto. 
### Conjunto de escala de máquina virtual

Se trata de um serviço da Azure, que instancia e orquestra, um numero especificado de maquinas virtuais com as mesmas configurações. 

Ele age em cima das tais, como um orquestrador com loadbalancer, distribuindo a carga, com base nos critérios definidos pelo contratante, podendo ser tanto de maneira manual, onde seria definido um numero especifico de VM's que seriam instanciadas, ou de forma automática e dinâmica, onde com base no uso das maquinas, seria alocado novas maquinas para suprirem a demanda.

### Conjunto de disponibilidade da máquina virtual

Se trata de outro serviço da Azure, projeto, para manter um ambiente de maquina virtual, altamente disponível. 

O serviço garante a disponibilidade, por uma estratégia de agrupamento, que e feito de duas maneiras. 

Agrupamento de: **Domínio de atualização** 
Agrupamento de: **Domínio de falha**

**Domínio de atualização** basicamente, as VM's nesse domínio, são separadas em diversos grupos, os quais, podem ser reiniciados em caso de falha, porem, e garantido, que sempre será um grupo por vez. 

**Domínio de falha** basicamente, as VM's nesse domínio, são agrupas por origem de Energia e rede, tal qual uma zona de disponibilidade. Por padrão, um conjunto de disponibilidade divida as VM em ate três domínios de falha. 

### Cenários de uso para VM's 
Em qualquer cenário, onde faça sentido, existir um host rodando N aplicações, que exija uma configuração e uma personalização, essa abordagem faz total sentido.

Claro que existe uma separação de interesses clara, na escolha entre uma VM e uma alternativa mais nova como [[Containers]], me parece claro, que a escolha da VM, e voltada para cenários mais especializados. 

- Hosting de uma aplicação, tanto para development, para test ou homologação
- Execução de um job ou rotina especifica
- Execução de um job em determinado tempo (CronJob)
- Servidor de banco de dados
- Proxy
- Gerenciamento de redes

