# Exemplos Avançados MRSC

## 1. Aninhamento com sub-prioridade
```
<geral>(mansagem @user) [alta] {
    analisar mensagem &&
    (erro crítico) [absoluta] {falar o erro encontrado} &&
    (pergunta técnica sobre * ) [media] {agir como um tecnico sobre $1}
}
```

## 2. Curingas `$1` e `$2` com `*`
```
<pesquisar>(mensagem @user contem pesquisar * sobre *) {
    buscar $1 $2 &&
    responder~detalhado
}
```
**Teste**: "pesquisar Python sobre OOP"

## 3. Padrão `{@$1:$2}` com debug
```
<debug>(mensagem @user contem debug @$1:$2) {
    mostrar regra $1 executando $2 &&
    log interno
}
```
**Teste**: "debug <geral>:status"

## 4. Regra descartável `[-1]` e `#1x`
```
<aviso>(True) [-1] #1x {
    boas-vindas &&
    autodeletar
}
```

## 5. Combinação `!` proteção + `?`
```
<seguranca>(detectar "maldade") [!clear] {
    ativar proteções? &&
    confirmar senha
}
```
**Não pode ser apagada por `<clear>`**
