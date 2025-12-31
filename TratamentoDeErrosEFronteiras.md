## Práticas de Exceções
O tratamento de erros é uma parte crucial no desenvolvimento de software, pois permite que um programa lide com situações inesperadas de maneira controlada, mantendo a robustez e a confiabilidade do sistema.
O Objetivo principal é garantir que, ao ocorrer um erro, o programa possa continuar executando ou, pelo menos, falhar de maneira graciosa, fornecendo informações úteis para a correção do problema.

## Boas práticas com Null
#### Não Retorne Null
Evite retornar null em métodos. Em vez disso, utilize objetos especiais, coleções vazias ou outras técnicas para representar ausência de valor.

#### Não passe Null
Não utilize null como argumento ao chamar métodos. Utilize alternativas como objetos padrão ou valores especiais para evitar a necessidade de lidar com null no código.

## Integração com Código de Terceiros
A integração com o código é uma habilidade essencial para desenvolvedores de software, pois raramente desenvolvemos todas as funcionalidade de um sistema do zero.
Utilizar bibliotecas, frameworks e APIs externas pode acelerar o desenvolvimento e adicionar funcionalidades robustas aos nossos projetos.
No entanto, essa integração deve ser feita com cuidado para garantir que o código externo não comprometa a qualidade e a manutenção do nosso sistema.

#### Usando Código de Terceiros
Integrar códigos de terceiros pode proporcionar grandes benefícios, como a economia d tempo e a adição de funcionalidades avançadas. Contudo, é fundamental escolher bem essas bibliotecas, avaliando critérios como confiabilidade, documentação, suporte e comunidade ativa. A integração deve  ser feita de maneira que o código externo seja bem encapsulado, facilitando futuras atualizações ou substituições.

#### Explorando e Aprendendo Fronteiras
Compreender e explorar as fronteiras entre o nosso código e o código de terceiros é crucial. Saber onde essas fronteiras estão permite que isolamos a lógica externa, testando-a separadamente e garantindo que qualquer falha ou mudança no código de terceiros não afete o núcleo do nosso sistema. Isso envolve conhecer bem as APIs e o comportamento das bibliotecas que estamos utilizando, além de estabelecer contratos claros para a interação entre os componentes internos e externos.

## Práticas de Fronteira
#### Usando código que ainda não existe
Em muitos casos, durante o desenvolvimento, precisamos definir interfaces para componentes ou serviços que ainda não existem. Esta prática envolve a criação de abstrações claras e contratos que permitirão a integração futura de maneira suave. Podemos utilizar técnicas como mocks e stubs para simular o comportamento desses componenetes inexistentes, permitindo o desenvolvimento e deste do nosso código de forma isolada.

#### Fronteiras Limpas
Manter as fronteiras limpas significa garantir que as interações entre diferentes módulos ou sistemas sejam bem definidas e mínimas. Isso pode ser alcançado através de interfaces claras, desacoplamento e encapsulamento. Fronteiras bem delineadas facilitam a manutenção e evolução do sistema, permitindo que mudanças em uma parte do sistema não tenham impactos inesperados em outras partes. Além disso, facilita o teste independente de cada módulo, garantindo a robustez e qualidade de software.
