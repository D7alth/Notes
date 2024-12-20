Esse conceito, diz respeito, a alocação (instanciação) recursos relacionados para a instanciação de recurso selecionado.

Quando alocamos ou melhor dizendo, instanciamos, um serviço, a **Azure** automaticamente "separa", recursos relacionados, que são de importância para o funcionamento do recurso instanciado. 

Temos como exemplo a instanciação de uma VM ([[Maquinas virtuais]]), para essa instanciação, e contra intuitivo, pensar que seria simplesmente uma instancia de um sistema operacional especificado, sem que a **Azure** repasse os valores de OPEx [[Conceitos de nuvem]], de cada um dos recursos físicos que estariam sendo consumidos. 

No caso da VM, teríamos diversos recursos associados, desde armazenamentos aos adaptadores de redes, todos eles são de certa forma "recursos", que sim, funcionariam por si só, e quando pensamos em um caso, onde excluiríamos a tal VM, esses recursos poderiam intencionalmente ou não continuar agregando como consumo.