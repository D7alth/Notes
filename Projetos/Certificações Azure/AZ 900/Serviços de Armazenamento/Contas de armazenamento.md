Trata-se dos diretórios lógicos (namespace), da Azure, para agregar os serviços de storage.

Esses namespaces, são completamente exclusivos, seguros e altamente disponíveis, sendo que, eles compõem, junto com o sufixo do tipo de serviço de serviço contratado, um ponto de extremidade, o qual, pode ser acessado tanto por HTTP quanto por HTTPS, além de claro, os SDK da maior parte das linguagens.

Em relação a criação / configuração CLI, tem uma operação relativamente simples, sendo que o mais complexo, talvez seja sua parte conceitual, onde e preciso tratar as configurações da como um "alto nível", semelhante as configurações de "[[Resource group]]" que são herdadas pelos seus componentes.

Um exemplo básico de criação de uma account, conta com alguns elementos, mas não restrito só a eles, seria:

``` Bash
az storage account create \
	-n "name" -g "group" \
		--access-tier "Cold | Cool | Hot | Premium" \
			--allow-blob-public-access true | false
				--public-network-access Enabled | Disabled
					--location BrazilSouth
						--SKU "Premium_LRS | Premium_ZRS | Standard_GZRS | Standard_LRS | Standard_RAGRS | Standard_RAGZRS | Standard_ZRS"
```


Onde na primeira linha temos: "az storage account create", que delimita o recurso e a operação que estamos pretendemos realizar. A mesma linha, vale para o update. 

A segunda temos: 	-n "name" -g "group", que se trata da configuração mais elementar e obrigatória de qualquer componente. 

A terceira temos mais uma, que não e obrigatória, assim como todas daqui para frente. 
A linha: --access-tier "Cold | Cool | Hot | Premium"  descreve o modo como os arquivos serão acessados, o que vai ser abordado mais a frente, mas impacta diretamente no preço de armazenamento e acesso.

A próxima, "--allow-blob-public-access true | false", essa linha basicamente, garante que pessoas sem autorização nenhuma, possam ou não acessar blobs em containers. Entretanto, essa pratica e desaconselhável. 

A Próxima, "--public-network-access", ja permite, que os blobs sejam acessados pela internet. 

"--location", define a região onde ficara a região principal do recurso.

por fim a "--SKU", que será abordado nos tópicos de [[Redundancia]] e [[Redundância de Aramazenamento]]
