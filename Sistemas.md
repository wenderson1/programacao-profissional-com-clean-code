## Arquitetura de Sistemas
A arquitetura de sistemas é a espinha dorsal de qualquer aplicação bem-sucedida.

Assim como um arquiteto planeja meticulosamente uma estrutura física, um arquiteto de software deve desenhar a estrutura de uma aplicação para garantir que ela seja robusta, escalável e fácil de manter.

A separação de responsabilidades, modularidade e a escalabilidade não são apenas boas práticas, mas sim requisistos essenciais para o desenvolvimento de aplicações que possam crescer e se adaptar ás mudanças ao longo do tempo.

#### Como você construiria uma cidade?
Construir uma aplicação complexa é similar á construção de uma cidade.

Ambas exigem planejamento, divisão de responsabilidades e serviços oferecidos.

Requer uma visão clara do futuro e a flexibilidade para crescer e se adaptar as necessidades emeergentes.

## Preocupações Transversais e Testes de Arquitetura
#### Cross-Cutting Concerns
Preocupações transversais são aspectos que afetam múltiplos módulos, como loggging, segurança, autenticação e transações. Gerenciar essas preocupações de forma centralizada evita a duplicação do código e facilita a manutenção.

#### Testar a Arquitetura do Sistema
Testar a arquitetura garante que o design atende aos requisitos de desempenho, escalabilidade e segurança. Garante que ninguém violou a responsabilidade das camadas.

#### Otimizar a tomada de decisão
Envolve escolher a melhor abordagem para resolver um problema de design, considerando requisitos e restrições. Devem ser baseadas em princípios de engenharia de software, dados empíricos e experimentação. É importante analisar trade-offs entre simplicidade, flexibilidade, desempenho e custo.

#### Use padrões com sabedoria
Padrões de design são soluções para problemas recorrentes no desenvolvimento de software. O uso excessivo ou inadequado pode levar a complexidade desnecessária. É essencial entender o problema e aplicar o padrão mais adequado.

#### Sistemas precisam de linguagens específicas de Domínio
As Ubiquitous Language são utilizadas para resolver problemas específicos de um domínio, facilitando a expressão de soluções de maneira natural e eficiente. O uso correto ajuda a aumentar a produtividade e facilitar a manutenção, descrevendo soluções de maneira próxima á linguagem do domínio de negócios.

# Transcrição (revisada e anotada) — Aula: **Sistemas / Arquitetura, Escalabilidade, Cross-cutting e Testes de Arquitetura**

> **Observação importante**: O texto abaixo é uma **transcrição revisada** a partir do material fornecido (com alguns trechos do ASR/ditado claramente truncados). Eu **mantive apenas o que está semanticamente claro** e marquei pontos onde o áudio/transcrição original está confusa.

## 1) Contexto do módulo
- O módulo faz parte do curso **“Programação profissional com Clean Code”**.
- Continuação do tema de **separação de responsabilidades**, que no módulo anterior foi aplicado a **classes**.
- Agora o foco sobe de nível: **responsabilidades no nível de sistema**, isto é:
  - camadas,
  - módulos,
  - “coleções de classes” com papéis bem definidos,
  - organização para manutenção, evolução, escalabilidade e testabilidade.

## 2) Por que arquitetura de sistemas importa
- **Arquitetura de sistemas** é descrita como a “espinha dorsal” de uma aplicação bem-sucedida.
- Objetivos citados:
  - **robustez**,
  - **escalabilidade**,
  - **manutenibilidade**,
  - capacidade de **crescer** e **se adaptar** ao longo do tempo.
- Ideias-chave reforçadas:
  - **separação de responsabilidades** (SoC),
  - **modularidade**,
  - **evitar acoplamento indevido entre camadas**.

## 3) Analogia 1 — Engenharia civil (prédio) vs. Engenharia de software
### 3.1 Semelhanças
- Tanto prédios quanto software precisam:
  - ser “**seguros**” (em software: confiáveis),
  - ser “**eficientes**” (uso de recursos),
  - ser “**fáceis de manter**” (ex.: acessar canos vs. localizar responsabilidades/códigos).

### 3.2 Diferença crucial
- **Prédios não são projetados para mudanças drásticas frequentes** (mover elevadores, lobby, etc.).
- **Software muda o tempo inteiro** e essa mudança é tratada como **premissa inevitável**.
- Conclusão enfatizada:
  - o software deve ser arquitetado para sofrer mudanças **com o menor custo e dor possível**.

## 4) Analogia 2 — “Como você construiria uma cidade?” (provocação do Uncle Bob)
- A aula usa a provocação do Uncle Bob: pensar arquitetura como **construção de uma cidade**.
- Restrições realistas:
  - existe um **budget** (tempo/dinheiro) e você não pode “construir tudo perfeito sem limites”.
- Ponto central:
  - assim como uma cidade precisa de planejamento (malha viária, expansão, serviços),
  - um sistema precisa de planejamento de **estrutura**, **responsabilidades** e **pontos de extensão**.

### 4.1 O “exercício mental” proposto
- Em vez de ir direto ao código, pensar:
  - “qual é a **primeira classe**?”
  - “qual é a **raiz** do problema?”
  - “qual estrutura inicial permite crescer sem virar uma bagunça?”

## 5) Separar **construção** do sistema vs. **uso** do sistema
- Um dos pontos repetidos: **separar a construção (wiring/configuração)** do **uso (execução/regra)**.

### 5.1 Metáfora (cidade)
- **Cidade = classe/sistema**
- **Serviço externo = serviço contratado** (ex.: coleta de lixo)
- Ideia:
  - a “cidade” não precisa **criar** a empresa de lixo;
  - ela **contrata** e integra o serviço.

### 5.2 Tradução para software
- Em software, isso aparece como:
  - **injeção de dependência (DI)**,
  - configuração central (ex.: `Program.cs` no .NET),
  - módulos responsáveis por **compor** dependências, sem espalhar `new` por todo lado.

## 6) “Isolar o main” (ponto do livro)
- O “main” (no .NET, normalmente `Program.cs`) é tratado como:
  - lugar de **configuração inicial**,
  - composição de dependências (DI),
  - pipeline/middlewares/fluxo de startup.
- Objetivo: impedir que regras do domínio “conheçam” detalhes de infraestrutura.

## 7) Fábricas (Factory / Factory Method) e criação em tempo de execução
- A aula introduz **Factories** para quando:
  - existem variações (ex.: `ProdutoA`, `ProdutoB`),
  - e a escolha da instância ocorre **em tempo de execução**.

### 7.1 Ideia essencial
- Você evita “espalhar” lógica de criação por todo o sistema.
- Você centraliza a decisão:
  - recebe um **parâmetro/chave**,
  - retorna a instância adequada.

### 7.2 Conexão com DI
- Foi citado que, em cenários reais, você pode usar:
  - o **container de DI** para resolver instâncias,
  - já com dependências injetadas.

## 8) Gestão / Injeção de dependência (DI)
- A DI é apresentada como:
  - base para **testabilidade**,
  - base para **manutenibilidade**,
  - mecanismo para reduzir **acoplamento**.
- Comentário da aula (tom opinativo):
  - “não consigo imaginar escrever código sem DI” — reforçando DI como padrão.
- Observação contextual:
  - no **.NET moderno**, DI virou prática padrão/ecossistema.

## 9) Escalabilidade e arquitetura “distribuível”
- A aula define escalabilidade como necessidade de uma arquitetura que:
  - suporte crescimento,
  - permita distribuição,
  - evite “um componente que faz tudo”.

### 9.1 Exemplo conceitual (não-escalável)
- Um sistema “não escalável”:
  - pega lista de dados,
  - faz varredura,
  - processa item a item dentro do mesmo lugar.
- Problema destacado:
  - **custo computacional** alto,
  - baixa eficiência,
  - difícil manutenção.

### 9.2 Exemplo conceitual (escalável)
- Um sistema “escalável”:
  - **delegação** via interfaces,
  - separação em componentes especializados,
  - foco em manutenção e evolução.

## 10) Preocupações transversais (Cross-cutting concerns)
- A aula inicia um novo tema: **preocupações transversais**.
- Definição prática usada:
  - aspectos que atravessam múltiplos módulos/camadas.
- Exemplos citados:
  - **login**,
  - **segurança/autenticação**,
  - **transações**,
  - **ORM / acesso a banco de dados**,
  - logging.

### 10.1 “A famosa pasta utils” (anti-padrão)
- A aula menciona que muitas aplicações criam uma pasta `utils` que vira “caixa de Pandora”.
- Proposta:
  - tratar cross-cutting como serviços/coisas bem nomeadas,
  - com interfaces e DI,
  - em vez de utilitários genéricos espalhados.

### 10.2 Exemplo citado: serviço de geração de imagem
- Cenário: gerar imagem de certificado ao final do curso.
- Solução sugerida:
  - criar um **serviço de geração de imagem** (com template + dados do aluno),
  - injetar via DI no ponto onde o aluno finaliza.

## 11) Testes de arquitetura (garantir que camadas não “se corrompam”)
- Problema: como garantir que ninguém:
  - coloque dependência de **Infra** dentro do **Domínio**, por exemplo.
- A aula propõe **testar a arquitetura** automaticamente.

### 11.1 Ferramentas citadas
- **xUnit**: executor/estrutura de testes.
- **NetArchTest** (o nome aparece como “NetArcTest/NetArkTest” na transcrição):
  - pacote do ecossistema .NET usado para definir regras de arquitetura.
  - foco em validar dependências/assemblies/namespaces.

### 11.2 Exemplo de regra mencionada
- “Domínio não deve depender de Infraestrutura”.
- Estratégia descrita:
  - selecionar um `Assembly` (por tipo de referência),
  - aplicar regras sobre “tipos” daquele assembly,
  - falhar o teste se houver dependências proibidas.

## 12) Princípios de decisão e “padrões com sabedoria”
- A aula reforça trade-offs de design:
  - simplicidade vs. flexibilidade vs. desempenho vs. custo.
- Alerta sobre uso excessivo de patterns:
  - “**paternite**” = vontade de aplicar patterns em tudo.
- Mensagem: design patterns resolvem problemas **quando aplicados ao problema certo**.

## 13) Linguagem ubíqua (Ubiquitous Language)
- Reforço do conceito: nomes e termos do domínio devem ser:
  - consistentes,
  - sem duplicidade de significado,
  - usados de forma uniforme.
- Benefícios citados:
  - manutenção,
  - comunicação,
  - clareza estrutural.

## 14) Trechos com transcrição confusa / incompleta (para revisão)
Os trechos abaixo aparecem com forte ruído (provável problema de ASR). Recomenda-se revisar o áudio/vídeo para corrigir:
- Intervenções marcadas como “You:” com palavras soltas e sem contexto.
- Partes onde aparecem termos “cortados” (ex.: “MEM”, “prospect”, “isensão de dependência”).
- Nome do pacote: aparece como “NetArcTest/NetArkTest”; o mais provável é **NetArchTest**.

## 15) Pontos que podem melhorar na explicação (sugestões)
1) **Delimitar explicitamente as camadas** no início (ex.: Domínio, Aplicação, Infra, UI) e o que pertence a cada uma.
2) **Mostrar um diagrama simples** (mesmo em texto) conectando:
   - `Program.cs` (composition root)
   - DI container
   - serviços de aplicação
   - domínio
   - infra
3) Quando falar “separar construção do uso”, incluir um exemplo mínimo em .NET:
   - onde registra serviços (`AddScoped`, `AddSingleton`)
   - onde usa (controllers/handlers) sem `new`.
4) No trecho de **Factories**, exemplificar com um caso real:
   - “qual provider usar” (pagamentos, frete, storage, etc.)
   - mostrar como evitar `switch` espalhado.
5) No tópico **escalabilidade**, diferenciar claramente:
   - performance (tempo de execução)
   - escalabilidade vertical vs. horizontal
   - “distribuível” (separação que permite mover partes para outros serviços/hosts)
6) No tópico **cross-cutting**, separar exemplos:
   - o que é transversal “puro” (logging, observabilidade)
   - o que é infra “core” (banco/ORM)
   - o que é concern de produto/negócio (regras) — para evitar misturar camadas.
7) Em **testes de arquitetura**, incluir:
   - um snippet completo de teste (1 regra) e a saída esperada quando falha
   - explicar como isso entra no CI (pipeline), evitando regressão.
8) Padronizar termos:
   - “manutenibilidade” vs. “manutenção”
   - “injeção de dependência” vs. “gestão de dependência”
   - “infra” vs. “cross-cutting” (definir a convenção do projeto).
9) Concluir com um “**checklist prático**” para o aluno aplicar no projeto:
   - Onde colocar a DI?
   - O domínio depende de quê?
   - Que cross-cutting eu tenho?
   - Quais regras de arquitetura eu vou testar?

## 16) Checklist rápido (extra, para aplicar no projeto)
- [ ] Existe um “composition root” (ex.: `Program.cs`) e ele concentra o wiring?
- [ ] Domínio está livre de dependências de infra/framework?
- [ ] Cross-cutting está encapsulado atrás de interfaces e via DI?
- [ ] Existem regras automatizadas (NetArchTest) impedindo violações?
- [ ] Nomes do domínio seguem linguagem ubíqua?

