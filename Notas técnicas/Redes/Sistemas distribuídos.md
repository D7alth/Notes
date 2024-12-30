### Cenário de exemplo 

Temos o seguinte diagrama para exemplificar um processo de requisição síncrona: 

![[Pasted image 20241219132922.png]]


Nesse cenário apresentado, temos um dispositivo IOT que por meio de uma requisição HTTP chama a aplicação diretamente, o que de fato não e um problema, porém, quando imaginamos um cenário onde temos milhares de dispositivos ou qualquer instabilidade entre a comunicação síncrona temos um problema de resiliência.

 