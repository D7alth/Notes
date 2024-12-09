Pelo visto, o modulo novo, de ecottaly, tem algumas divergencias em relação a arquitetura da aplicação.

Os DTOs estão sendo instanciados na camada de infraestrutura, não me parece correto. Principalmente pelo modo que esta sendo tratado as requests ao ARC, onde as interfaces estão sendo feitas dentro do application, como um helper, e posteriormente implementado na infrastruct. 

- Porque não estão em camada de serviço dentro do domínio? 
	- Seriam serviços de que?
	- Poderiam ser serviços de aplicação, ainda que não me pareça ser o caso

O modulo de facility tem dependências direta com o modulo de area, afinal precisaríamos acessar os nodes dos prédios para fazermos as validações / filtragens.

Precisariamos criar uma endpoint de getAuthorizedNodes. 