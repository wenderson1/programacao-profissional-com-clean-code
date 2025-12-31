## Principios do TDD
Os testes de unidade são uma prática fundamental no desenvolvivmento de software, garantindo que cada parte do sistema funcione corretamente de forma isolada.

Eles ajudam a identificar e corrigir erros precocemente no ciclo de desenvolvimento, proporcionando um feedback rápido e constante para os desenvolvedores.

Além disso, os testes de unidade facilitam a refatoração do código, promovendo um design mais limpo e modular.

### TDD - Test Driven Development
- 1 - Escreva um teste e assista ele falhar.
- 2 - Escreva o mínimo de código para passar no teste
- 3 - Refatorar, melhore e teste novamente

## As 3 leis do TDD

### Regra 1 - Não escreva código de produção até que você tenha escrito um teste que falhe
Essa lei enfatiza a importância de deixar que os testes guiem o desenvolvimento do código.

Ao começar com um teste que falha, você define claramente a funcionalidade desejada antes mesmo de escrever o código que a implementa.

Isso garante que cada pedaço de código de produção escrito tenha um propósito claro e esteja diretamente relacionado a um requisito funcional.

### Regra 2 - Escreva apenas um teste que falhe por vez.
A segunda lei promove um ciclo de desenvolvimento incremental, onde você escreve um teste de unidade que falha para uma única funcionalidade específica ou comportamento desejado.

Ao focar em escrever apenas um teste que falha por vez, você reduz a complexidade e o escopo de cada ciclo de desenvolvimento, permitindo que problemas sejam identificados e corrigidos rapidamente.

Isso ajuda a manter o código simples e fácil de entender, além de garantir que os testes sejam focados e relevantes.

### Regra 3 - Não escreva mais código de produção do que o necessário para passar no teste atual.
Esta lei reforça a prática de escrever o código de forma iterativa e incremental.

Após escrever um teste que falha, você deve implementar apenas a quantidade mínima de código necessária para fazer esse teste passar.

Isso evita a criação de código desnecessário ou complexo que não esteja diretamente relacionado à funcionalidade sendo testada.

Essa abordagem promove um design mais simples e claro, onde cada parte do código tem um propósito específico e comprovado por testes.

Além disso, ao escrever o mínimo de código necessário, você facilita a manutenção e a refatoração futura do sistema.


  
## Práticas de testes limpo

#### Mantendo os testes Limpos
Testes devem ser tratados com o mesmo cuidado que o código de produção. Devem ser claros, organizados e bem documentados.

### Linguagem de Teste Especifíca do Domínio
Utilize termos do domínio da aplicação dentro dos testes para facilitar o entendimento e a comunicação.

### Um padrão duplo
Evite duplicação de lógica entre os testes e o código de produção. Mantenha os testes simples e focados.

### Um Assert por Teste
Cada teste deve verificar uma única condição para facilitar a identificação de falhas.

### Conceito Único por Teste
Cada teste deve focar em um único conceito ou cenário para manter a clareza e a precisão.

### F.I.R.S.T
Os testes devem ser Fast(Rápidos), Indenpendent(Independentes), Repeatable(Repetíveis), Self-Validating (Auto-validaveis), e Timely(Oportunos)

### Fast (Rápidos)
Teste de unidade devem ser executados rapidamente para que possam ser rodados frequentemente, sem atrapalhar o fluxo de trabalho do desenvolvedor.

### Independent (Independentes)
Cada teste de unidade deve ser independente de outros testes. O resultado de um teste não deve depender do resultado ou do estado gerado por outro teste.

### Repeatable (Repetíveis)
Testes de unidade devem ter uma clara indicação de sucesso ou falha. Isso geralmente é feito através de asserts que verificam se os resultados esperados correspondem aos resultados reais.

### Timely (Oportunos)
Testes de unidade devem ser escritos no momento certo, preferencialmente antes do código de produção correspondente. Isso está alinhado com a prática de Test-Driven Development (TDD).




