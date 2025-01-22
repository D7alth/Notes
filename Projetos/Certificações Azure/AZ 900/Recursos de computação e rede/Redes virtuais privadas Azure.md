#az900

O serviço prestado de VPN pela Azure, no contexto de cloud herda as mesmas definições gerais do conceito de [[VPN]]
### Getways de VPN da Azure

Se tratam de um serviço da Azure, que pode ser utilizado para enviar trafego criptografado entre uma [[Redes virtuais]] do Azure e uma rede publica ou insegura, como visto na definição de geral do que e um [[Getway]], não e difícil imaginar como funciona.

Como mencionado na definição do [[Getway]], ele também trata da tradução entre os protocolos, partindo desse conceito, esse serviço oferece vários tipos de conectividade: 

- Datacenters a redes virtuais por conexões [[Site a site]]
- Dispositivos finais a redes virtuais por conexões ponta a site
- Redes virtuais a redes virtuais por conexões rede a rede

Também e interessante o conceito de [[VPN]] dentro da Azure, tem uma depenica direta com a instanciação desses [[Getway]], que por sua vez, tem uma dependência direta com as [[Redes virtuais]] instanciadas, de forma que: 

- Para termos uma VPN e necessários termos **UMA** instancia de um recurso de Getway de VPN
- Para termos um Getway de VPN e necessário **UMA** e somente **UMA** rede conectada ao  serviço

No tópico geral de configuração desse serviço temos dois tipos de VPNs, onde a diferenciação existe na forma como os pacotes devem ser roteados dentro da rede. 

- **Baseado em políticas**, onde e definido estaticamente os IP's que terão os pacotes criptografados por meio dos tuneis
- **Baseado em rota**, preferível,  mais dinâmico no geral, pois o roteamento pode ser atribuído como uma responsabilidade do serviço, sendo que ele dispõem de interfaces de tuneis criptografados, os quais ele rotearia os pacotes, conforme o necessário. 

Os cenários para usar baseado em rotas, e amplo, mas e de se imaginar que em cenarios onde e exigido certa mobilidade ou flexibilidade em termos de rede, ele seja mais adequado. 

**Exemplos:**

- Conexões entre redes virtuais
- Ponto a site
- Multisite
- Coexistência com um getway do azure [[ExpressRoute]] 

**Aspectos de resiliência e alta disponibilidade**

Abrange os conceitos de alta disponibilidade gerais do azure, tais como [[Zonas de disponibilidade]], e estende esse conceito com alguns recursos padrões, como por exemplo.

Ativo/em espera, um mecanismo instanciado em background junto da contratação do getway de VPN, onde basicamente, existe uma alternativa completamente desligada do usuário final, para caso haja uma falha o trafego poder ser redirecionado em poucos segundos.

