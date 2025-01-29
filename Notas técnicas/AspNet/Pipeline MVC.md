#AspNet

A pipeline no ASP.NET é composta por série de middlewares que manipulam solicitações e respostas relacionadas às requisições HTTP. Essa estrutura e extensível e customizável, o que permite adaptar o fluxo de execução conforme as necessidades do aplicativo. 
### Middlewares

São componentes que atuam no fluxo de processamento de requisições e repostas. Implementados como métodos de extensão e têm a responsabilidade de executar tarefas especificas, como autenticação autorizações e manipulação de erros. Entre outros.

No ASP.NET, os middlewares podem:
- Interceptar e processar a requisição antes que ela chegue ao controller.
- Modificar ou manipular a resposta antes que ela seja enviada ao cliente. 

> [!NOTE] Importante
> A pipeline é bidirecional: a requisição desce pela cadeia de middlewares, e a resposta retorna pelo mesmo caminho. Logo a logica do middleware pode manipular os dados da requisição tanto na entrada quanto na saida, um erro pode ser "anotado" no começo do processamento, passar com o "**next()**" para o próximo middleware, e apenas na volta, o erro ser retornado. 

#### Exemplo de Middleware

**Middleware de anotação simples** (apenas invoca o próximo)
``` csharp
app.use(async (context, next) => {
	Console.WriteLine("Execução dentro do middleware - Processo do request");
	await next.Invoke(); // Continua a pipeline ate o fim, apos o processamento
	Console.WriteLine("Execução dentro do middleware - Processo do response");
})
```

**Middleware Terminais**
``` csharp
app.use(async (context, next) => {
	if (context.Request.Path == "/fim")
	{
		await context.Response.WriteAsync("Termainl - Processo de request");
		return; // Finaliza a execução do programa sem executar o proximo middleware, trata-se de um curto-circuito
	}
	await next.Invoke(); // Continua a pipeline ate o fim, apos o processamento
})
```

### Ordem de execução dos middlewares

![[Pasted image 20250117093527.png]]

Trata-se da ordem padrão, mas esse fluxo pode ser customizável dependo da necessidade e do tipo de projeto. 

### Exceptions







