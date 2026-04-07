# Changelog

## v2.3 (Atual)
- Declaração ≠ execução: regras declaradas não executam automaticamente
- Regras fantasma: regras inválidas são registradas e apagadas com aviso
- Prioridade -1: abaixo de [baixa], autodeleta após executar
- Escopo #1x: executa uma vez e se remove
- Apelido descartável `<_>`: convenção para regras temporárias

## v2.2
- `$1 $2`: múltiplos curingas posicionais
- `<...>` apelido puro (sem argumentos)
- `{...}` dentro de `()` condições
- `@`, `*`, `:` como separadores em condições

## v2.1
- `||` fallback em ações
- `#escopo`, `?`, `~off/~on`
- Aninhamento com prioridade relativa
- `else/else if` sem prioridade própria

## v2.0
- Adição de `||`, `#escopo`, `?`, `~off/~on`
- Aninhamento com prioridade relativa
- `else/else if` sem prioridade própria

## v1.0
- Estrutura base: `<apelido>(condição) [prioridade] {ação}`
- Símbolos fundamentais implementados
