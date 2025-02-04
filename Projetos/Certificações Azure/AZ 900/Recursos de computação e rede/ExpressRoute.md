#az900 

Esse serviço tem semelhanças com os conceitos de [[VPN]], trazendo uma nova perspectiva, onde para cenários que faça sentido "alugar", um "Link" privado para fazer a comunicação entre a rede local e os data centers da Microsoft. 

De certa forma, também e irrefutável a semelhança, pelo menos conceitual com os conceitos de conexões [[Site a site]], porem sem a necessidade de transferência de dados por rede publica. 

Basicamente, tendo em vista que a rede local e a rede (ainda estamos falando de cloud), tenha um "Circuito ExpressRoute", o que sugere a necessidade latente de uma conexão física por algum canal, como e predominantemente escolhido a fibra ótica, e para esse ponta a Microsoft recorre a parceiros certificados.

Com toda a questão de roteamento, mas partindo do fato que se trata de uma conexão privada, poderia ser conectado essas duas topologias por uma rede segura e privada da Microsoft.

De certa forma, estamos puxando um cabo entre os Datacenters da Microsoft e a LAN, e de fato alugando um "link" privado.

Onde teríamos, a contratação de um serviço que prove um "link", que serviria de canal, para comunicação entre a rede local aos serviços da Microsoft. 

Isso traz, diversos benefícios, principalmente se tratando de resiliência e latência, onde a Microsoft se encarrega de montar uma arquitetura de alta disponibilidade para os próprios links.

> [!NOTE]
> 
> Esse conceito ainda se estende para atender redes **WAN**, com alternativas de conectividade "*Any-to-Any*", tão bem como Ponta a ponta, por via de Ethernet

