# Exemplos Básicos MRSC

## 1. Regra com alternativas na condição
```
<saudacao>(olá | hi | hello | boa noite) {responder \"Olá! Como posso ajudar hoje?\"}
```
**Teste**: Digite "olá" ou "hi"

## 2. Regra com confirmação `?`
```
<limpar>(limpar regras ?) {apagar todas as regras && responder \"✅ Regras limpas!\"}
```
**Teste**: Digite "limpar regras" → pede confirmação

## 3. Desativar/Reativar com `~off` e `~on`
```
<pausar>(pausar) ~off <saudacao> {responder \"Saudação pausada\"}
<ativar>(ativar) ~on <saudacao> {responder \"Saudação reativada\"}
```
**Teste**: "pausar" → "olá" não responde → "ativar" → funciona

## 4. Fluxo condicional `else if` / `else`
```
<tom>(tom formal) {responder~formal}
else if (tom informal) {responder~amigavel}
else {responder~neutro}
```

## 5. Múltiplas regras em uma linha com `;`
```
<sim>(sim | s | ok) {confirmar}; <nao>(não | n | nope) {negar}
```
**Teste**: "sim" ou "não"
