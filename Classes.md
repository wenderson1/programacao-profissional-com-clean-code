## Organização e Encapsulamento
No desenvolvimento de Software, as classes são as unidade fundamentais de estrutura e comportamento.

A forma como organizamos e encapsulamos o código dentro das classes pode influenciar significativamente a clareza, manutenção e a extensibilidade da aplicação.

Este módulo aborda as principais práticas para a organização de classe e a importância do encapsulamento, bem como a responsabilidade e a coesão que uma classe deve ter para manter o código limpo e eficiente.

Organizar classes de forma lógica e clara é crucial para manter um código limpo e fácil de entender. As classes devem ser organizadas em pacotes ou namespaces que reflitam sua funcionalidade e propósito dentro da aplicação.

Encapsulamento é o princípio de esconder os detalhes de implementação de uma classe e expor apenas o que é necessário. Isso protege a integridade do objeto e previne alterações externas indesejadas.

## Responsabilidade e Coesão

- #### Classes devem ser pequenas!
Classes pequenas são mais fáceis de entender, manter e testar. Uma classe deve ter apenas uma única responsabilidade ou razão para mudar.

- #### O principio da responsabilidade única (SRP)
Uma classe deve ter uma, e somente uma razão para mudar. Este princípio, conhecido como SRP (Single Responsibility Principle), ajuda a manter a coesão e facilita a manutenção.

- #### Coesão
Coesão refere-se ao quão intimamente os elementos dentro de uma classe estão relacionados. Uma alta coesão é desejável, pois indica que a classe tem uma única responsabilidade bem definida.

- #### Manter a coesão resulta em diversas classes pequenas
Classes coesas são frequentemente pequenas e focadas em uma única tarefa. Isso leva a um design mais modular e flexível.

- #### Organizando para mudanças
Organizar o código de forma que mudanças futuras afetem o mínimo possível de classes é fundamental para um código sustentável.

- #### Isolando para mudanças
Isolar partes do código que são suscetíveis a mudanças frequentes ajuda a limitar o impacto das mudanças e mantém o sistema robusto.
