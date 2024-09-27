O inversor - INVERTER-PORTINARI-100058 está relacionado tanto ao prédio **"BUILDING-POC-BESX"** na área **"POWER-PLANT-POC-BESX"**, Quanto diretamente no **"RPV-PORTINARI"**.

------------- 

Os apartamentos do edifico **CICEROBARROS** também tem um relacionamento duplo, com areas no mesmo nível, elas são, relacionamento direto com seu **floor**, e relacionamento direto com seu **wing**

Para ser mais exato, pelo o que da a se entender, os apartamentos, estão conectados a uma wing e a um floor. 

O floor, tem relacionamento com todos os apartamento de uma "serie", ou seja, o floor "3PV", representa todos os apartamentos da serie 30x, assim como o "4PV", representa todos da serie 40x.

Enquanto a wing, tem relacionamento, apenas com alguns dos apartamentos, me parece ter uma certa ordem na distribuição, onde existe 3 wings, A, B e C, onde cada uma contem 2 apartamentos de cada serie, em ordem DESC. 
****
**Implicações na querie**: o nível de relacionamento do ponto de vista dos apartamentos, para qualquer uma das areas e 2, o que sugeriria, uma possível duplicação, mas como uso o `DISTINCT ON (TWIN_ID)`, implica que dependendo do _sorting_, pode montar primeiro a hierarquia dos **WINGs** (essa e a tendencia, ao menos que faça um _sorting_ diferente), com os apartamentos que ele venha a ter conexão, porem, quando chegar no loop que monta a hierarquia dos **FLOORs**, ele removeria os ids que já foram utilizados, deixando assim os pavimentos com prédios faltando. 

**Obs**: essa implicação só aconteceria, em um cenário, onde o usuário tem acesso tanto as **wings** quanto aos **floors**. 

-------------

O mesmo comportamento e visto no EDIFICIO PORTINARI, com a ELETRO NORTE, onde todas as areas de um contam com os mesmos relacionamento na outra.

-------

Algo semelhante com o problema do  INVERTER-PORTINARI-100058 ocorre com alguns medidores do FLAMBOYANT, onde temos como exemplo o medidor de agua **WATER-A100-FLAMBOYANT**, onde ele tem relacionamento com duas areas, distintas, **REAQT-FLAMBOYANT** e **SHOPPINGFLAMBOYANT**

Sendo que o  **REAQT-FLAMBOYANT** tem relacionamento direto com o ADMIN / ENT-REAQT, mas sem relacionamento com o building **SHOPPINGFLAMBOYANT**.

-----------------
 
Todos os problemas estão, Tanto no banco de teste quanto no de produção.







---------------------


Testes de performance

### GET AUTHORIZED HIERARCHY

**Acesso de total/ADMIN**

| Node            | linhas Dev | linhas Imp | Match | Time Dev | Time Imp |
| --------------- | ---------- | ---------- | ----- | -------- | -------- |
| CECNC           | 5172       | 5172       | V     | 1964 ms  | 1001 ms  |
| ADMIN           | 23031      | 23033      | F     | 6.93 s   | 1773 ms  |
| MANEVIRGULA     | 690        | 690        | V     | 388 ms   | 346 ms   |
| PORTINARI       | 148        | 148        | V     | 449 ms   | 361 ms   |
| USP *MAIN AREA* | 1342       | 1342       | V     | 1480 ms  | 827 ms   |

**Acesso de usuário (acesso a areas)**

| Node        | linhas Dev | linhas Imp | Match | Time Dev | Time Imp |
| ----------- | ---------- | ---------- | ----- | -------- | -------- |
| MANEVIRGULA | 61         | 61         | V     | 433 ms   | 332 ms   |
| PORTINARI   | 61         | 61         | V     | 471 ms   | 348 ms   |
| CAMPUSUSP   | 200        | 200        | V     | 357 ms   | 337 ms   |

-----

### GET AUTHORIZED METRIC

| Node        | Valor Dev | Valor Imp | Match | Time Dev | Time Imp |
| ----------- | --------- | --------- | ----- | -------- | -------- |
| CECNC       | 0         | 0         | V     | 15.37 s  | 2.23 s   |
| MANEVIRGULA | 41860.369 | 41860.369 | V     | 4.10 s   | 1937 ms  |
| PORTINARI   | -4178232  | -4178232  | V     | 16.67 s  | 2.02 s   |
| CAMPUSUSP   | 373296.7  | 373296.7  | V     | 15.04 s  | 2.02 s   |





Hierarquia de configurações - AZ 900
Estudar bastante AD - AZ 900
Estudar active directory - AZ 900


