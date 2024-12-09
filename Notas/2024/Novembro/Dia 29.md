- [x] O cliente pode ser qualquer coisa, ele deveria ser relacionado com um prédio? 


https://besx-core-api-staging.azurewebsites.net/facility/scheduled-works?startDate=2024-11-01T00%3A00%3A00Z&endDate=2024-11-29T23%3A59%3A59Z&clients=clients%5B0%5D.clientId%3A129849%26clients%5B0%5D.tokenId%3APORTINARI


https://besx-core-api-staging.azurewebsites.net/facility/scheduled-works?clients[0].clientId=129849&clients[0].tokenId=PORTINARI&startDate=2024-11-01T00:00:00Z&endDate=2024-11-29T23:59:59Z




2. **Listagem de clientes sem acesso direto**  
**Dado** uma lista de prédios  
**E** o usuário tem acesso de visualização a clientes
**E** o usuário não tem acesso direto aos prédios  
**Quando** o usuário solicitar os contratos de terceiros  
**Então** os contratos de clientes para os prédios devem ser fornecidos



- [x] Verificar como criar um usuário em relação as permissões das paginas de contrato
	1. Usuários criados, sem relação com as Areas, automaticamente não tem permissão (administrador necessário) 
	2. Apenas administradores podem da permissões
	3. As permissões "especiais" são dadas manualmente por nós 
	4. Usuários já existentes, com relação aos prédios mas sem permissões não acessam. 
