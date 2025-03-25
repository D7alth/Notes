#DataStructures #TechDictionary #TechNotes 

Esse tipo de notação e descrito como uma linha de "**Crescimento linear**" no gráfico, isso se da ao fato de,  o crescimento do tempo de execução da função cresce proporcionalmente ao tamanho do input.
### Exemplos reais
**Cenário 01**

Imagine um consultório medico, onde o medico, demora, exatamente 20 minutos, para cada uma das consultas.

caso ele tenha 1 paciente, podemos dizer que: O(1), pois o tempo de atendimento e constante, e não tem um crescimento baseado no input.

Ainda assim internamente, teríamos exatamente 20 minutos de "Execução".

O que poderia aumentar, conforme aumentarmos o numero de pacientes, por exemplo: 12 pacientes.

Ou seja, temos algo como : **O(13)**, ignoramos as operações de tempo constante (como a soma no caso).

Com um tempo total de: 20 * 13.

ainda que o tempo da consulta não seja importante para o algoritmo em si.
### Exemplos de código
**Cenário 01**

Imagine um consultório medico, onde o medico, demora, exatamente 20 minutos, para cada uma das consultas.

``` c#
public static int AmountOfTime(int pacients)
{
	var time = 0;
	for(int i = 0; i < pacients; i++)
	{
	  time += 20;
	}
	return time;
}
```