
## Definição geral

Por definição, as redes virtuais privadas ou VPNs, se tratam de túneis criptografados, que visam conectar dois pontos seguros por um meio inseguro. 

Por exemplo, quando temos fazemos uma requisição HTTP via uma rede publica ou insegura, existe alguma probabilidade desse dado ser interceptado (poderíamos esta falando de  "[[Man in the middle]] ou [[ARP poisoning]]), as VPNs, criam um túnel criptografados entre o requisitante e o destino, o que dificultaria essas ações, afinal, mesmo sendo interceptados, sem as devidas chaves de criptografia dificilmente os dados seriam acessados. 

 Esse comportamento explica a capacidade de uma VPN de simular uma requisição de outro lugar do mundo, o túnel, não passa de um "desvio", que a requisição faz.
 
 Os dados são mandados para um dos servidores de borda da VPN, os quais podem esta em qualquer parte do mundo, e por fim, ao chegar nesse servidor de borda, a integridade do dado criptografado e verificado por meios de algoritmos como [[HMAC]] (Hash-based Message Authentication Code) ou [[TLS]], por fim, os dados podem ou não manter a criptografia da VPN, dependendo da configuração do destino. 