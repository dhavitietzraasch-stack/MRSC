# Exemplos Avançados MRSC

## 1. Aninhamento com sub-prioridade
```
<geral>(mensagem qualquer) [alta] {
    analisar mensagem &&
    (erro crítico) [absoluta] {emergencia} &&
    (pergunta técnica) [media] {tecnico}
}
```

## 2. Curingas `$1` e `$2` com `*`
```
<pesquisar>{pesquisar * sobre *} {
    buscar $1 $2 &&
    responder~detalhado
}
```
**Teste**: "pesquisar Python sobre OOP"

## 3. Padrão `{@$1:$2}` com debug
```
<debug>{debug @$1:$2} {
    mostrar regra $1 executando $2 &&
    log interno
}
```
**Teste**: "debug <saudacao>:responder"

## 4. Regra descartável `[-1]` e `#1x`
```
<aviso>(primeiro uso) [-1] #1x {
    boas-vindas &&
    autodeletar
}
```

## 5. Combinação `!` proteção + `?`
```
<seguranca>(segurança total ?) [!clear] {
    ativar proteções &&
    confirmar senha
}
```
**Não pode ser apagada por `<clear>`**
