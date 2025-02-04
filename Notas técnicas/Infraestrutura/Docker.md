 Em essência cria uma camada de abstração entre as configurações do ambiente de desenvolvimento e o ambiente "exportação", de certa forma, encapsula as configurações do ambiente criando de certo modo uma "caixa" que funciona  de forma agnóstica, com os requisitos necessários para rodar o projeto, independentemente do local de execução. Evitando problemas de incompatibilidade, ou falta de algum LIB ou configuração especifica do ambiente.

A grande diferença entre na arquitetura, a forma de containerização do docker compartilha o kernel do sistema operacional do host, e consegue separar os processos por meios de namespaces.

Isso garante certa leveza, em comparação com um VM, por não carregar ou precisar integrar com todos os recursos de um sistema operacional de fato. 