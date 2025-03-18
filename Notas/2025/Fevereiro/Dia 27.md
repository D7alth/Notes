#Craft 

- [x] Verificar resposta da API (integra-netship)
	- [x] 10.228.777/0002-42 
	- [x] 06.221.176/0001-50
- [x] Verificar Implicação nos campos que vem padrão
- [x] Verificar consistência com o banco 
- [x] Finalizar fluxo
	- [x] PPL craft-cp-sync
	- [x] PPL dados-craft-async
		- [x] ImportDrafts - Insert
		- [x] DraftSendToOrigin - Good descriptions (avaliar)
-------
- [ ] Continuar projeto de blog 
	- [ ] Subir repo com demo de autenticação com JWT
	- [ ] Subir repo com demo de autenticação com identity






### Pergunta: 

Cara, tô com uma dúvida aqui sobre o funcionamento da **Craf.IntegrationManager (API)**, mais especificamente na **endpoint "from-to/translate"**.

Fazendo uns testes, percebi um padrão: quando um **draft** tem **"ViaPais" não nulo**, **"Rco_DraftDLine" maior ou igual à data atual** e **"Cntr_Quantidade" maior que 0**, ele é do tipo **LCL**. Já no caso do **FCL**, reparei que **sempre que "Rco_DraftDLine" é maior ou igual à data atual e "Cntr_Quantidade" é maior que 0, o campo "ViaPais" está nulo**. Ou seja, ele pode ter, mas nessas condições específicas, nunca aparece preenchido.

A questão é que, quando a **PPL** tenta chamar a **API "from-to/translate"** passando uma carga do tipo **LCL**, recebo esse erro aqui:

_"The key draft_sending_to_cw_service_type with value from LCL does not exist."_

Pelo erro, fiquei na dúvida se isso faz parte de alguma **regra de negócio**, onde simplesmente **não se faz esse "from-to" para cargas do tipo LCL** ou se realmente se trata de uma exceção.