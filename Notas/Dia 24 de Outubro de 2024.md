Continar as tasks do dia [[Dia 23 de Outubro de 2024]]!

- [ ] Entender como funciona o versionamento do JAVA
- [ ] Assistir algum vídeo sobre, no almoço
- [ ] Revisar meus pontos mais fracos para a AZ 900
	-  Politicas / governança
	-  Fazer a prova em inglês

----


## Tarefas de hoje

- [x] Adicionar o novo requisitos de classificação
- [x] Melhorar forma de como chamar os clients_names nos requesitos
- [x] Alternativa para validação de local
- [x] Tirar duvidas com a Marina
	- Filtro de "Última atualização"
	- Autorização
- [x] Montar BDD de autorização
- [x] Reunir com a Marina, para falar a respeito.
- [x] Pensar em algo para validarmos os locais_ids?
- [x] Fazer algumas provas de conceitos com o infraspeak



----

No site em produção, percebi que o Jack faz os filtros de forma em que se e passado todos os chamados de uma vez para o front, o front se encarrega de fazer essa filtragem, afinal esse comportamento não justificaria uma endpoint nova? 

- Pelo visto não tem como relacionar os locais_id diretamente com as areas no banco, talvez seja interessante pensar em algo que não comprometa as autorizações. 


- o JACK tem uma endpoint que monta a hierarquia
- A solução dele parece com a que eu pensei


----
## Perguntas gerais

**Para a Mariana:**
- Os filtros de atualização ignoram o filtro de tempo definido pelo cliente?
	- Isso se aplicaria a todos os outros cards? 

Exemplo: Se um usuário, definir no filtro, de novembro de 2023 a dezembro de 2023, e para esse intervalo, o índice de eficiência e de 90%, ao escolher a classificação de ultima atualização como sendo do ultimo dia, e para o dia fosse de 10%, então o valor do índice deve  cair para 10%? 

- _Quero saber se esse filtro implicaria em uma nova request ao infraspeak, e como temos mais de um dropdown de classificação, se um afetaria o card referente ao outro_

**Na verdade essa atualização e referente a data em que foi feito a atualização.**

- **Autorizações dos chamados**
	- Como funcionaria a distribuição das autorizações, sendo que não podemos autorizar por Areas, apensa por prédios? 
		- Seriam permitidos apenas usuários com autorizações aos prédios? 
		- Seriam permitidos usuários com autorizações filhas do prédio? Mesmo isso implicando em o usuário ter acesso a chamados de areas diferente? 
		
**A autorização deve ser necessariamente relacionada ao prédio**

## BDD 

Pressupondo que as autorizações para os chamados, seriam análogas a estrutura de autorização que existe atualmente.

Onde seria, "autorizáveis", areas de todo tipo, com exceção a medidores. 

**Característica**: Permissão para locais de chamados ao usuário

Cenário: autorização direta a nó
    	Dado o usuário "John doe" que tem acesso a Area **"Edifício A1"**
    	Quando o "John doe" solicitar os chamados para a Area **"Edifício A1"**
    	Então deve retornar os chamados cujo o **local** seja **"Edifício A1"** 

Cenário: autorização indireta a nó
    	Dado o usuário "John doe" que tem acesso a Area **"Edifício A1"**
    	Quando o "John doe" solicitar os chamados para as Areas filhas da Area **"Edifício A1"** sendo elas **"A1-A, A1-B"******
    	Então deve retornar "Sem permissão para acessar as Areas"

