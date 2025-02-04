Agregados são definidos como um **Clouster de objetos de domínio** (Entidades, Value Objects, Enums, etc..) tratados como um **unidade coesa** para garantir a consistência nas regras de domino.

**Parafraseando Elemar Jr.** _"Agregados são um Ilha de código coeso e conciso"_.

Junto a isso temos um conceito de "**Limites Transacionais**", que posso extrapolar esse conceito para fazer uma analogia. 

_"Limites Transacionais, são como organizar os ingredientes de uma receita, essa receita e uma salada verde com tomate simples. Em uma caixinha, separamos tudo que e importante e que precisamos para criar uma salada por exemplo, dentro dessa caixa escrito 'salada', temos, alface, tomate, limão, sal, e outras coisas. Repare que cada um desses ingredientes são necessários para montar essa salada, todos eles tem uma 'identidade'' afinal conseguimos separar o que e um limão de um tomate, e todos eles tem suas propriedades que podem ser iguais ou diferentes. Logo, precisamos ter todos esses ingredientes inseridos dentro dessa caixa para garantirmos que podemos fazer uma salada"_

Esse limite como explicado na analogia, delimita ate onde podemos "imaginar" um agregado, quais entidades realmente pertencem a esse agregado? Quais VO's? e por assim vai.

Um exemplo mais palpável para programação seria por exemplo um Blog, com a seguinte modelagem: 

![[Pasted image 20250123091918.png]]


Temos diversas entidades, Posts, Comentários, Categorias e ate Usuários.

Todo esse conjunto classifica um **Agregado**, porem, para a modelagem faz sentido os **Users** estarem no mesmo diagrama, mas ai entra o **Limite Transacional**, a entidade **Users**, não depende de uma Postagem, pelo contrario, esta completamente descolado a não ser pela referencia do ID.

Nesse caso onde estamos modelo o domínio, consigo ver o **Users**, sendo um agregado próprio e posts tendo essa referencia de forma a não acoplar os dois. 

A ideia e manter a ideia de "**Post**"  concisa e fechada para si mesma, assim como os Usuários. Enquanto as outras entidades se tratam de entidades internas, pois por mais que tenham identidade, não são o "ponto de entrada" para o agregado de "Posts". 

### Agregado Raiz

O ponto de entrada para o agregado, como no exemplo acima temos o "**Post**", trata-se de um entrypoint ou onde o processo que instancia / persiste um agregado começa. 

