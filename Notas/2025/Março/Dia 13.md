#Craft 

Vou continuar com as demandas do [[Dia 12]].

- [x] Verificar com o Fabio a possibilidade de não setar retry para erros do tipo 400
- [x] Verificar com o Fabio a necessidade de percorrer o array de payloads sendo que necessariament so vai ter um item
- [x] Validar as ideias de tratamento de exceção

Falei com o Fabio, pelo visto realmente o Retry não faz sentido para esse PPL. Pelo visto o fluxo do NS parece está correto. 

Agora preciso tratar especificamente do fluxo do CW, esse tem algumas particularidades. Uma delas e que se trata de um payload só, que pelo o que eu entendi, pode vir ate 3 payloads acoplados. 

A ideia e simples, me parece que tem existe mais de evento associado ao mesmo trigger. Preciso criar uma validação para garantir o processamento de pelo menos os 2 payloads obrigatorios (DraftStructureFlow e EventDIMReferenceFlowId) e caso exista algum arquivo no 3 payload, também devo garantir a execução dele ou para a execução da aplicação. 

-----

- [x] Analisar o fluxo mais curto para interrupção da branch do CW 
- [x] Modelar um validador de esquema

-----

Parada e usar o JOLT para criar uma condicional maluca para remover ou não os itens opcionais. 


----------------


## 📝 Change Log

### ✨ Alterações

Foram realizadas mudanças lógicas e estruturais com base em um novo entendimento sobre a validação dos campos obrigatórios e opcionais dos eventos disparados. Além disso, foram feitas melhorias para aumentar a manutenibilidade do projeto e seus componentes.

---

### 🔹 Implementações

- **✅ Bloco de Validação para  Cargo Wise Flow**
    - Separação dos objetos opcionais e obrigatórios
    - Validação dos seguintes campos obrigatórios:
        - `objectTrackCode`
        - `configurations`
        - `eventType`
        - `eventDescription`
        - `payload`
    - Interrupção do fluxo em caso de erro na validação (`Throw`)

---

### 🔄 Alterações

- **🔹 Exceção bloco de validação do Netship Flow:** Lançamento de exceção (`Throw`) em caso de falha na validação
- **🔹 Tratamento de Exceções Personalizado:**
    - Implementado nos blocos:
        - `Origin Flow`
        - `DraftSendToOrigin`
        - `Main Block`
- **🔹 Movimentação de Tratamento de Exceção:**
    - Validação do fluxo `N Payload to send` movida para `OnException` do bloco `Origin Flow`
- **📧 E-mail Estruturado:**
    - Agora trata erros de validação de forma genérica
- **🛠️ Novo JOLT:**
    - Criado para processar objetos de forma genérica (`get CW xmls`)

---

### ❌ Removido

- **🔻 Fluxo de Retry:**
    - Removido do `OnException` do bloco `Main Block`

---

### ⚠️ Observação

Todos os campos a serem validados, tanto do Cargo Wise quanto do fluxo Netship, foram devidamente verificados.