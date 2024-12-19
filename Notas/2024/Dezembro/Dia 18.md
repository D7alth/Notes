Todas as endpoints de Ecotally estão com bugs, retornando 500 ou um valor default.

## Endpoints com problemas (Ultima branch)

- [x] GET SCORES - 500
- [x] GET CURRENT SCORES - 500
- [x] GET EMISSIONS - 500
- [x] GET SATISFACTION - Default
- [x] GET AUTHORIZED LATEST NOTIFICATIONS - Mais de 15 segundos na resposta
- [x] GET AUTHORIZED USER NOTIFICATIONS - Default
- [x] GET AUTHORIZED ENERGY BILLS - 500 (apenas na branch feature/subscription-and-mainarea-authorizations)


-----

As alterações foram todas feitas diretamente no servidor de staiging. Justifica o front receber 500.

--------

O atributo de isWithinHierarchy foi alterado na branch de get third party contracts

----

## Pesquisas

- [ ] Pesquisar mais sobre SonarQubePipeline
- [ ] CWE


--------

## Tarefas 

- [x] Criar testes para os commands e queries já criadas de autorização
	- [x] AddAreaAuthorizationsCommandHandler
	- [x] AddContractAuthorizationCommandHandler
	- [x] ChangeAdministratorStatusCommandHandler
	- [x] ChangeSubscriptionCommandHandler
	- [x] CreateAuthorizationCommandHandler
	- [x] RemoveAreaAuthorizationsCommandHandler
	- [x] RemoveAuthorizationCommandHandler
	- [x] RemoveContractAuthorizationCommandHandler
- [x] Criar testes para os atributos
- [x] Criar testes para os filtros
- [x] Verificar se favorites



------

- [x] GET AUTHORIZED METRIC OF BUILDING - FOBBIDEN
- [x] GET AUTHORIZED METRIC - FOBBIDEN
- [x] GET AUTHORIZED METRIC TYPES - FOBBIDEN[
TODOS DE METRIC COMO USUARIO

- [x] GET AUTHORIZED METRIC TYPES - FOBBIDEN
- [x] GET AUTHORIZED WATER BILLS  WITH PREVIOUS PERIOD - FOBBIDEN
