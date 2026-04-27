# Changelog MRSC

---

## v4.0 (atual)

### Adições
- **Variáveis formais:** `set($nome) = "valor"` com suporte a `#global` e resolução antes da execução
- **Flag `!agora`:** executa a regra imediatamente ao declarar — substitui a string `"execute now"` da v2.3
- **Comandos de controle unificados:** `/list`, `/info`, `/del`, `/off`, `/on`, `/execute`, `/clear`, `/strict`
- **`/strict on|off`:** modo de análise estrita — desativa interpretação de linguagem natural
- **Namespace `.~` formalizado:** nicknames do kernel protegidos por convenção e por regra de sistema
- **`kernel_AI.txt`:** camada de runtime separada (confidence gate, fallback, checkpoint periódico)
- **`kernel_optional.txt`:** camada de segurança ZTA opcional (6 camadas de proteção)
- **`sys_user.txt`:** arquivo de configuração de sessão do usuário
- **Tie-breaking explícito:** em empate de prioridade, `#global` > `#session`; depois ordem de declaração
- **Normalização numérica de prioridade:** `low=100`, `medium=300`, `high=700`, `absolute=1000`

### Melhorias
- Estrutura base documentada de forma mais precisa — obrigatórios vs. opcionais claramente separados
- `else if` / `else` documentados como extensões da regra pai (sem prioridade própria)
- Regras fantasma agora geram aviso antes de serem descartadas (comportamento confirmado)
- Exemplos revisados e expandidos com casos reais de wildcard duplo, variáveis e dispatcher

### Correções
- Título interno corrigido ("party N System" removido de todos os arquivos)
- Metadados `[cite: X]` removidos do prompt principal
- Bloco `<.~000>` / `<.~shutdown>` no kernel_optional corrigido (sintaxe `else` solta eliminada)
- Contadores de tentativas migrados para o sistema de variáveis `$`

---

## v2.3

- Declaração ≠ execução: regras declaradas não executam automaticamente
- Regras fantasma: regras inválidas são registradas e apagadas com aviso
- Prioridade `-1`: abaixo de `[baixa]`, autodeleta após executar
- Escopo `#1x`: executa uma vez e se remove automaticamente
- Apelido descartável `<_>`: convenção para regras temporárias sem conflito

---

## v2.2

- `$1`, `$2`: múltiplos curingas posicionais com captura por ordem
- `<...>` apelido puro — nunca carrega argumentos
- `{...}` dentro de `(...)` — padrão de busca em condições
- `@`, `*`, `:` como operadores de padrão dentro de condições

---

## v2.1

- `||` fallback em ações: `{A && B || C}`
- `#escopo`, `?`, `~off` / `~on`
- Aninhamento com prioridade relativa ao pai
- `else` / `else if` sem prioridade própria — herdam do bloco pai

---

## v2.0

- Adição de `||`, `#escopo`, `?`, `~off` / `~on`
- Aninhamento com sub-prioridade
- `else` / `else if` introduzidos

---

## v1.0

- Estrutura base: `<apelido>(condição) [prioridade] {ação}`
- Símbolos fundamentais: `<>`, `()`, `{}`, `[]`, `#`, `|`, `!`, `&&`
