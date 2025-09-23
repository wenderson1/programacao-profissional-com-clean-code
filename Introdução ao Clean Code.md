# Introdução ao Clean Code
## Oque é Clean Code?
Clean Code é uma filosofia de desenvolvimento de software que enfatiza o uso de um conjunto de princípios e práticas para escrever código de forma clara, legível e sustentável.
O objetivo principal é tornar o código fácil de entender e modificar por outros desenvolvedores. Clean Code promove a simplicidade, a clareza e a eficiência, permitindo que o software seja mantido e expandido de maneira mais eficaz.
Essencialmente, Clean Code é sobre escrever código que não apenas funcione, mas também que seja fácil de ler, entender e melhorar.

#### Código Ruim
##### O Custo Total de Possuir uma Bagunça
- O Impacto na Produtividade: A produtividade da equipe diminui a medida que o código ruim aumenta, porque cada alteração ou adição de funcionalidade se torna mais complexa e arriscada.
- Aumento dos Custos: Com o tempo, o custo de manutenção de um código ruim supera o custo inicial de escrever código limpo. A necessidade constante de corrigir bugs e lidar com problemas de desempenho adiciona custos contínuos ao projeto
- Ciclo de Decadência: Equipes acabam pedindo um redesign completo do sistema devido a insustentabilidade do código existente, resultando em um ciclo de redesenvolvimento 
caro e ineficaz

## Princípios e Atitutes de Clean Code
### Redesign - Reescrever tudo do zero?
#### Impactos negativos de tempo e recursos
- Grandes redesigns frequentemente consomem muito tempo e recursos, desviando atenção de melhorias incrementais que poderiam trazer valor imediato.
- Risco de Falhas: Grandes mudanças introduzem muitos riscos. O novo sistema pode não atender todas as necessidades do antigo, pode ter novos bugs ou pode nunca ser concluído.
- Moral da Equipe: Reescrever um sistema do zero pode ser desmoralizante para a equipe que trabalhou no sistemas original

#### Estratégias Alternativas
- Refatoração Contínua: Em vez de um grande redesign, melhorar continuamente o código existente através de refatorações incrementais
- Divisão de Responsabilidades: Quebrar a aplicação em pedaços menores e mais gerenciáveis. Dividida por responsabilidades de negócios e funcionalidades.
- Testes Automatizados: Implementar e mlehorar a cobertura de testes para assegurar que mudanças não introduzam novos bugs.

### Atitudes
#### A Importância da Atitude
- A mentalidade de um desenvolvedor impacta diretamente na qualidade do código.
- Assim como em outras profissões( médicos, engenheiros) é necessária muita responsabilidade e ética profissional.

#### Responsabilidade do Desenvolvedor
- Qualidade do código: Desenvolvedores devem sentir-se responsáveis pela clareza, manutenção e eficiência do código que escrevem.
- Comunicação e Transaparência: Informar gestores e stakeholders sobre as implicações de decisões técnicas e de prazo.

#### Atitude Proativa
- Refatoração Contínua: Não esperar que o código fique insustentável para começár a melhora-lo
- Feedback e Aprendizado: buscar feedback constante sobre o código e estar aberto a aprender e aplicar melhores práticas.

#### Boas e Más Atitudes
- Boa Atitude: Desenvolvedores que se preocupam com a legibilidade do código, fazem revisões de código frequentes e incentivam boas práticas.
- Má Atitude: Desenvolvedores que escrevem código apressadamente sem pensar na manutenção futura, deixando dívidas técnicas acumularem.

### O Dilema da Produtividade
#### Produtividade vs Qualidade
- O jeito mais rápido de fazer algo, é fazer certo na primeira vez.
- Um caso muito clássico é o do healthcare.gov (USA)

#### Impacto do Código Sujo na Produtividade
- Débito técnico: Acúmulo de código mal escrito e não refatorado que, ao longo do tempo, aumenta a complexidade e dificulta a manutenção.
- Manutenção e Correção de Bugs: Maior esforço necessário para corrigir falhas e implementar novas funcionalidades em um código desorganizado.

#### Estratégias para Equilibrar Velocidade e Qualidade
- Test-Driven  Development(TDD): Adotar TDD para garantir que cada nova funcionalidade tenha cobertura de testes, facilitando a identificação de problemas antes do lançamento.
- Revisões de Código: Implementar revisões de código regulares para garantir que o código mantenha um padrão de qualidade elevado.
- Pair Programming: Utilizar PairProgramming para melhorar a qualiade do código e promover o compartilhamento de conhecimento.

## Conceituando Clean Code
### Como grandes programadores definem Clean Code
- Bjarne Stroustrup: Código Limpo é elegante e eficiente, com lógica clara e sem ambiguidades. Deve ser focado em uma única tarefa e ter um tratamento completo de erros.
- Grady Booch: Código limpo é simples e direto, lê-se como um livro bem escrito, com abstrações claras e fluxos de controle diretos.
- Dave Thomas: Código limpo pode ser lido e melhorado por outro desenvolvedor. Deve ter testes de unidade e de aceitação, nomes significativos, dependências mínimas e uma API clara
- Michael Feathers: Código limpo é escrito com cuidado, sem melhorias óbvias pendentes, mostrando a dedicação do autor á sua arte.

### A Regra do Escoteiro (The Boy Scout Rule)
Sempre deixe o acampamento mais limpo do que você encontrou.
- Refatore
- Teste
- Renomeie
- Documente
- Organize
- Otimize
