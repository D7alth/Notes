- [x] Finalizar revisão das PR's "Delete widget of dashboard" (@2025-01-20 10:40)  [#1]  
- [x] Adicionar em "BUG - FEATURES - IMPROVES" o IMPROVE da paginação das endpoints do infraspeak (@2025-01-20 10:04)  [#2] 
- [x] Desenhar regras de negocio e TDD do "Create Custom Widget" (@2025-01-20 15:00)
- [x] Refazer a revisão na PR "Delete widget of dashboard" (@2025-01-13 16:30) 
- [x] Criar Handler para criação de "CustomWidgets" (@2025-01-21 11:00)


### Anotações das Tasks

#### #1
_Mudar  o flow de excptions das controllers no pé que esta a aplicação, mesmo que de forma gradual e a melhor ideia? Estamos caminhando para o uso indevido de status code 500 e erros de banco quase não rastreáveis? _

- Existe alguma maneira mais "elegante" para suprirmos as exceptions? 
- Se o front não tem como resposta o status code correto, como pode diferenciar erros de fluxos com erros de uso? 

- [x] Pesquisar algumas maneira de tratar exceções de maneira mais elegante [#1-1]
- [x] Falar com o José [#1-2]

_A ideia e fazer um middleware global de tratamento de erros, e uma ideia com potencial, mas vejo varias gambiarras de domínio que pode invalidar isso. Como capturar um erro que não e lançável?_