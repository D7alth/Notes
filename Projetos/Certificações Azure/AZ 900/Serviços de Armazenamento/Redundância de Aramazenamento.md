#az900

Por padrão o Azure, já guarda varias copias dos mesmos arquivos, para garantir a disponibilidade em casos de problemas técnicos ou desastres, em uma escala menor. 

### LRS

"Local Redudancy Storage", e um ótimo exemplo disso, pois, dentro do mesmo data center,  temos varias copias do mesmo arquivo, essa também e a opção de redundância padrão, e a com menor custo, e só com isso, garante **11 noves de durabilidade dos objetos**, no determinado ano. 

Claro, que para um caso mais problemático, por exemplo, um incêndio no datacenter, poderia significar uma perca. 

### ZRS

"Zone Redundancy Storage", aqui, a redundância está distribuída entre as zonas da mesma região, isso garante **16 noves de durabilidade**, pois como nos conceitos vistos em [[Redundancia]], temos o arquivo, distribuído em zonas totalmente individuais e autônomas entre si. 

No caso de um desastre, e simplesmente reapontado o DNS para o datacenter que tem o arquivo disponível. 


### GRS

"Geography Redundancy Storage", baseia-se no conceito geral de Par de região, juntamente com os recurso de LRS, ou seja, esse tipo de redundância, recebe e disponibiliza os arquivos dentro de um datacenter de uma região e os copia para a região PAR da mesma.

### GZRS

Estende o conceito do GRS, apenas adicionando o esquema de redundância do ZRS **NA REGIÃO PRIMARIA**.