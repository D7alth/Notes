#az900

Impossível falar de **Functions**, sem mencionar **serveless**, dois conceitos que andam completamente conectados.

O recurso de **Function**, fornecido pela **Azure**, fica em um limiar dubio entre um modelo de PAAS e um modelo de SAAS, ambos descritos em [[Tipos de serviços de nuvem]], isso se da ao fato, de sim, se tratar de uma um recurso, cujo o foco esta em oferecer uma ferramenta para o desenvolvimento.

Ao mesmo tempo em que, o recurso em si, por definição, tem uma exigência mínima de configuração, e principalmente de manutenção.

Em termos de arquitetura, não difere tanto, de **WebApps** normais, apenas com algumas diferenças, onde sim ele e executado em servidores físicos, ao contrario do que indica o termo **serveless**, porem e executado de tal forma que, não existe uma necessidade termos uma aplicação completa rodando constantemente.

Basicamente, cada rotina executável de uma aplicação, e traduzido em uma função, e definido gatilhos, os quais, por meios de mecanismos da Azure, indicam para o próprio provedor, qual rotina deve ser executada. Não e importante para o consumidor saber, como e onde foi executado, afinal, entende-se da própria arquitetura, que isso não e importante.

Ainda que pareça improvável, existem maneiras de manter estado entre funções, por padrão, uma **Function** não tem um estado, porem, e possível manter estado entre as funções, onde e criado um contexto, que e divido entre N funções, essas por sua vez, são chamadas de "**Durable Functions**".

E importante ressaltar a forma com que e feito o pagamento, afinal, estamos consumindo apenas o processamento daquela função, logo, diferentemente de um VM ou de um WebApp, o pagamento não e feito em relação a disponibilidade do recurso e sim pelo seu uso.