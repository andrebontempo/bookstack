Na minha empresa temos 44 Unidades , usando o cenário da resposta anterior, como poderíamos fazer para ter artigos específicos para as Unidades?

Esse é um ponto muito importante. Na verdade, a existência de 44 Unidades muda um pouco a estratégia. A primeira pergunta que eu faria é:

> **As Unidades têm processos muito diferentes ou apenas algumas particularidades locais?**

Se a resposta for **"80% é igual para todas as Unidades e 20% são particularidades"** (que é o cenário mais comum), **eu não criaria uma estante para cada Unidade**. Isso geraria uma explosão de conteúdo duplicado e seria muito difícil de manter.

## A estratégia que eu recomendaria

Manteria três estantes principais:

```text
📚 Usuário Final

📚 Equipe de TI

📚 Administração
```

E criaria um quarto espaço para documentação local:

```text
📚 Unidades
```

Dentro dela:

```text
📚 Unidades

📖 Unidade A
    📂 Infraestrutura
    📂 Sistemas Locais
    📂 Procedimentos
    📂 Contatos

📖 Unidade B
    📂 Infraestrutura
    📂 Sistemas Locais
    📂 Procedimentos
    📂 Contatos

...

📖 Unidade 44
```

Assim, tudo o que é **corporativo** continua em **Usuário Final** e **Equipe de TI**, enquanto as exceções ficam na estante **Unidades**.

* * *

## Exemplo prático

### Artigo corporativo

```text
📚 Usuário Final

📖 VPN

📂 Procedimentos

📄 Como instalar a VPN
```

Vale para todas as unidades.

* * *

### Artigo específico

```text
📚 Unidades

📖 Embrapa Gado de Corte

📂 VPN

📄 Configuração da VPN da Unidade
```

Esse artigo existe apenas porque aquela Unidade possui uma configuração diferente.

* * *

## Outra possibilidade (que eu gosto ainda mais)

Se as diferenças forem pequenas, **nem criaria uma estante "Unidades"**.

Criaria um capítulo chamado **Particularidades das Unidades** dentro do livro correspondente.

Exemplo:

```text
📚 Equipe de TI

📖 Google Workspace

📂 Administração

📂 Procedimentos

📂 Particularidades das Unidades

    📄 Unidade A

    📄 Unidade B

    📄 Unidade C
```

Isso evita espalhar a documentação.

* * *

# Pensando na IA

Eu adicionaria metadados durante a indexação.

Exemplo:

```json
{
  "audience": "ti",
  "scope": "corporativo"
}
```

Outro artigo:

```json
{
  "audience": "ti",
  "scope": "unidade",
  "unit": "Embrapa Gado de Corte"
}
```

Então o chatbot poderia filtrar automaticamente.

Usuário informa:

> Sou da Embrapa Gado de Corte.

A IA primeiro procura artigos da Unidade e, se não encontrar, usa os artigos corporativos.

* * *

# Um fluxo inteligente

```text
Pergunta do usuário

        │

Qual Unidade?

        │

        ▼

Procura artigo da Unidade

        │

Encontrou?

   │           │

 Sim         Não

   │           │

Resposta     Procura na Base Corporativa
```

Assim, a documentação corporativa continua sendo a "fonte oficial", e cada Unidade documenta apenas o que realmente é diferente.

* * *

## Minha recomendação para uma empresa com 44 Unidades

Eu adotaria um modelo de **conhecimento em duas camadas**:

1.  **Base Corporativa** (cerca de 90% dos artigos): procedimentos, sistemas, normas e tecnologias comuns a toda a organização.
    
2.  **Base das Unidades** (cerca de 10% dos artigos): apenas exceções, particularidades locais, contatos, infraestrutura específica e sistemas exclusivos.
    

Essa abordagem evita duplicação, facilita a manutenção e é excelente para um sistema de RAG. O chatbot pode priorizar os artigos da Unidade do usuário e, na ausência deles, recorrer automaticamente à base corporativa. Você mantém uma única fonte de verdade para o conhecimento comum e documenta localmente apenas o que realmente varia entre as 44 Unidades.