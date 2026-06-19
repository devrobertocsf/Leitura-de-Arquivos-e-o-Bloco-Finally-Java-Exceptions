# 📂 Leitura de Arquivos e o Bloco Finally (Java Exceptions)

Este repositório demonstra o uso avançado de blocos de tratamento de erros em Java, com foco na manipulação de arquivos do sistema operacional e na aplicação do bloco `finally` para liberação de recursos em memória.

## 🎯 O Papel do Bloco `finally`

Em Java, o bloco `finally` é uma estrutura acoplada ao `try-catch` cuja principal característica é a **garantia de execução**. Ele será executado obrigatoriamente, independente de o fluxo do código ter seguido pelo caminho feliz (sem erros no `try`) ou ter sido desviado por uma exceção (capturada no `catch`).

É amplamente utilizado para operações de limpeza (*cleanup*), como fechar conexões de bancos de dados, conexões de rede ou streams de arquivos, evitando o temido *Memory Leak* (vazamento de memória).

## 🚀 Detalhes Técnicos Implementados

* **Checked Exception (`FileNotFoundException`)**: Ao instanciar um `Scanner` apontando para um objeto `File`, o compilador Java obriga o desenvolvedor a tratar a possibilidade do arquivo não ser encontrado em tempo de execução.
* **Fechamento Seguro no `finally**`: Como o objeto `Scanner sc` inicia como `null`, o bloco `finally` realiza uma verificação defensiva (`if (sc != null)`) antes de invocar o método `.close()`, prevenindo a ocorrência de um `NullPointerException`.

### Fluxo de Execução com Finally

```text
  [Abertura do Recurso]
            ↓
       [Bloco TRY]
      /           \
 (Sucesso)     (Exceção)
    │              │
    ▼              ▼
[Código]     [Bloco CATCH]
    │              │
    ↳ ───── 向 ────┘
            ↓
     [Bloco FINALLY]  ⬅ (Sempre executa e fecha o recurso)
            ↓
   [Fim do Programa]

```

## 📂 Estrutura do Arquivo

* `execeções1/Programa.java`: Código principal contendo o mapeamento do arquivo físico `in.txt`, lógica de leitura condicional (`hasNextLine()`), captura de erro de arquivo ausente e desalocação do Scanner.

## 💻 Comportamento Esperado no Console

### Cenário 1: Arquivo não encontrado no diretório

```text
Error opening file: C:\temp\in.txt (O sistema não encontrou o caminho especificado)

```

## 📄 Licença

Este projeto está sob a licença MIT.

---

*Projeto prático desenvolvido por Roberto para consolidar os conhecimentos em manipulação de arquivos de texto e robustez de código Java.*

---



