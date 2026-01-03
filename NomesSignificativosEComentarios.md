# Fundamentos de Clean Code: Nomenclatura e Comentários

Este documento resume as melhores práticas de programação profissional abordadas no módulo de "Nomes e Comentários". O objetivo é escrever código que seja legível, sustentável e que comunique sua intenção claramente, evitando confusão para quem for mantê-lo no futuro (incluindo você mesmo).

---

## 1. A Importância da Nomenclatura

Dar nomes às coisas é uma das tarefas mais difíceis e importantes no desenvolvimento de software. Nomes ruins causam confusão histórica (como a sequência de versões do Windows: 98, 2000, XP, Vista, 7, 8, 10...), enquanto nomes bons comunicam propósito.

### Princípios Básicos de Nomenclatura

#### 1.1. Revele a Intenção
O nome deve explicar **o que** a variável/método faz e **por que** existe, sem necessidade de comentários extras.

*   ❌ **Ruim:** `int d; // dias desde o início`
*   ✅ **Bom:** `int diasDesdeInicioProjeto;`

#### 1.2. Evite Desinformação
Não use nomes que induzam ao erro ou que tenham significados ambíguos.

*   ❌ **Ruim:** `var resultados;` (Muito genérico)
*   ✅ **Bom:** `var numeroDePedidos;` (Específico)

#### 1.3. Faça Distinções Significativas
Se você tem duas variáveis diferentes, os nomes devem refletir a diferença real entre elas. Evite sequências numéricas sem sentido.

*   ❌ **Ruim:** `valor1`, `valor2`
*   ✅ **Bom:** `precoProduto`, `quantidadeProduto`

#### 1.4. Use Nomes Pronunciáveis
O código é discutido verbalmente por equipes. Se você não consegue pronunciar o nome da variável, a comunicação falha.

*   ❌ **Ruim:** `var nmProd;` (Ninguém fala "ene eme prod")
*   ✅ **Bom:** `var nomeProduto;`

#### 1.5. Use Nomes Pesquisáveis
Evite variáveis de uma letra (exceto talvez em loops pequenos), pois são impossíveis de buscar em um projeto grande.

*   ❌ **Ruim:** `var ic;`
*   ✅ **Bom:** `var idadeCliente;`

#### 1.6. Evite Codificações e Notação Húngara
Não inclua o tipo da variável ou prefixos desnecessários no nome. As IDEs modernas já mostram o tipo.

*   ❌ **Ruim:** `iContador`, `strNome`
*   ✅ **Bom:** `contador`, `nome`

#### 1.7. Evite Mapeamento Mental
O leitor do código não deve ter que traduzir mentalmente o que uma variável significa.

*   ❌ **Ruim:** `var lrv;` (O leitor tem que lembrar que isso é "Lista de Referência de Vendas")
*   ✅ **Bom:** `var listaVendas;`

---

## 2. Nomes em Contextos Específicos

Regras para aplicar dependendo se você está nomeando uma classe, um método ou lidando com o domínio do negócio.

### Classes vs. Métodos
*   **Classes:** Devem ser **Substantivos**.
    *   Ex: `Validador`, `Processador`, `Cliente`.
    *   Evite nomes vagos como `GerenciadorDeDados` (se ele faz tudo).
*   **Métodos:** Devem ser **Verbos/Ações**.
    *   Ex: `ProcessarPagamento()`, `ObterCliente()`.
    *   Evite nomes "engraçadinhos" ou coloquiais (ex: `VaiQueDa()`, `Detonar()`). Seja profissional.

### Consistência (Uma palavra por conceito)
Escolha um termo para uma ação e use-o em todo o projeto. Não misture sinônimos.
*   ❌ **Inconsistente:** `ObterCliente()`, `BuscarUsuario()`, `GetPedido()`.
*   ✅ **Consistente:** `ObterCliente()`, `ObterUsuario()`, `ObterPedido()`.

### Contexto de Domínio (DDD)
Use a linguagem onipresente (Ubiquitous Language). O código deve refletir o negócio.
*   **Domínio da Solução:** Termos técnicos conhecidos por programadores (ex: `CarrinhoDeCompras`, `FabricaDeContas`).
*   **Domínio do Problema:** Termos que o especialista de negócio usa (ex: `Sinistro`, `Apolice`, `CheckIn`).

### Contexto Desnecessário
Não repita o nome da classe dentro dos métodos ou propriedades se o contexto já for óbvio.
*   ❌ **Ruim:** Classe `Usuario` com método `AdicionarUsuario()`.
*   ✅ **Bom:** Classe `Usuario` com método `Adicionar()`.

---

## 3. Comentários: O Bem, o Mal e o Feio

A regra de ouro é: **Comentários não compensam código ruim.** Se você sente necessidade de explicar o que o código faz, provavelmente deveria refatorar o código para que ele se explique sozinho.

### ✅ Bons Comentários (Quando usar)
1.  **Informativos:** Explicam algo que não é óbvio no código (ex: "Este método usa o algoritmo Dijkstra").
2.  **Explicação de Intenção:** O *porquê* de uma decisão técnica (ex: "Usamos essa abordagem para garantir complexidade O(1)").
3.  **Avisos de Consequências:** Alertas importantes (ex: "Não altere este caminho, é uma dependência externa").
4.  **TODOs:** Lembretes de tarefas futuras ou dívidas técnicas (ex: `// TODO: Implementar verificação de segurança`).
5.  **Direitos Autorais/Licenças:** Cabeçalhos legais obrigatórios.

### ❌ Comentários Ruins (Evite a todo custo)
1.  **Murmúrios/Óbvios:** Explicar o que o código já diz claramente.
    ```csharp
    i++; // Incrementa i
    ```
2.  **Enganosos:** Comentários que dizem uma coisa, mas o código faz outra (geralmente porque o código mudou e o comentário foi esquecido).
3.  **Código Comentado:** Polui a leitura. Se não serve mais, **apague**. O Git (controle de versão) serve para recuperar código antigo se necessário.
4.  **Diário/Jornal:** Não use comentários para listar quem alterou o arquivo e quando. O Git já faz isso muito melhor.
5.  **Marcadores de Posição/Fechamento:**
    ```csharp
    } // Fim do if
    ```
    Se o bloco é tão grande que precisa disso, ele deveria ser refatorado em métodos menores.
6.  **Informação não local:** Comentários que falam sobre partes do sistema que não estão ali perto.
7.  **Atribuições:** `// Feito por João`. Desnecessário com uso de Git.

---

## 4. Resumo e Pontos Chave

*   **Legibilidade é prioridade:** O código é lido muito mais vezes do que é escrito.
*   **Refatore antes de comentar:** Antes de escrever um comentário explicando uma lógica complexa, tente extrair essa lógica para um método com um nome descritivo.
*   **Profissionalismo:** Evite piadas, trocadilhos ou nomes ofensivos no código.
*   **Limpeza:** Remova código morto, código comentado e comentários desatualizados periodicamente.

> *"O código limpo deve parecer que foi escrito por alguém que se importa."*
