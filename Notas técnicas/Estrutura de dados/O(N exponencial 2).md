Esse tipo de notação e descrito como uma linha "Constante Exponencial", isso se da ao fato de,  o tempo de execução de operação ser quadraticamente proporcional ao tamanho do input.

A maior parte das operações onde teríamos que repetir a função N vezes, para quais quer que seja o fim, poderiam se classificado como quadraticamente proporcional.
### Exemplos reais
Imagina o mesmo cenário do consultório medico, mas agora, para a recepcionista.

Digamos que para cada pessoa que ela atenda, cada pessoa em 5 minutos, e precisa fazer apenas N perguntas para cada.

Mas por algum erro na distribuição de senhas ela precise atender de forma que:

- A pessoa e chamada para ser atendida
- A pessoa responde qual a sua senha
- A pessoa volta para o fim da fila
- A pessoa espera ate ser chamada novamente
- A pessoa responde as perguntas

E sempre que chegar uma nova pessoa, ela precise que todos passem pelo processo todo novamente.

Ate que seja feito o numero de perguntas igual ao numero de pessoas que chegaram.
### Exemplos em codigo
Percorrer um array Bi Dimensional

``` C#
public static void Main(string[] args)
{
	int[,] arr = {{12,3,45}, {0, 2,45}};
	for(var i = 0; i < arr.Length; i++)
	{
		for(var j = 0; j < arr.Length; j++)
		{
			Console.WriteLine("colunm: " + i);
			Console.WriteLine("Row: " + j);
			Console.WriteLine("value: " + arr[i, j]);
		}
	}
}
```