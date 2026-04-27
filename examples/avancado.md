# Exemplos Avançados MRSC v4.0

---

## 1. Aninhamento com sub-prioridade

Sub-prioridades são relativas ao pai — `[absoluta]` aqui significa máximo *dentro* do contexto pai, não globalmente.

```
<geral>(mensagem @user) [alta] {
    analisar mensagem &&
    (se erro crítico) [absoluta] {
        explicar erro encontrado &&
        alertar@user
    } &&
    (se pergunta técnica sobre *) [média] {
        agir como especialista em $1 &&
        responder~detalhado
    }
}
```

**Teste:** "explique erro de segmentação" → ativa sub-regra técnica com $1 = "erro de segmentação"

---

## 2. Curingas `$1` e `$2` com `*`

```
<pesquisar>(mensagem contém {pesquisar * sobre *}) {
    buscar $2 relacionado a $1 &&
    responder~detalhado
}
```

**Teste:** `pesquisar Python sobre OOP`
→ $1 = `Python`, $2 = `OOP`

---

## 3. Padrão `{@$1:$2}` — dispatcher de regras

```
<dispatch>(mensagem contém {@$1:$2}) #global [absoluta] {
    executar $2 em @$1
}
```

**Teste:** `<saudacao>:pausar` → executa `pausar` na regra `<saudacao>`

---

## 4. Gerenciamento de regras via wildcard

```
<gerenciar>(mensagem contém {@$1:deletar}) { /del @$1 }
else if (mensagem contém {@$1:pausar})     { /off @$1 }
else if (mensagem contém {@$1:ativar})     { /on  @$1 }
else if (mensagem contém {@$1:info})       { /info @$1 }
```

**Teste:** `<saudacao>:pausar` → desativa `<saudacao>` sem apagar

---

## 5. Regra descartável com `[-1]` e `#1x`

Ambas as formas são equivalentes — escolha a mais legível:

```
// Forma 1 — prioridade autodeletável
<aviso>(always) [-1] {
    responder "Bem-vindo! Esta mensagem aparece uma vez." &&
    listar regras ativas
}

// Forma 2 — escopo explícito
<aviso>(always) #1x {
    responder "Bem-vindo! Esta mensagem aparece uma vez." &&
    listar regras ativas
}
```

---

## 6. Proteção `!clear` combinada com confirmação `?`

```
<seguranca?>(detectar {ameaça | ataque | injeção}) [absoluta, !clear] {
    alertar@user &&
    ativar modo seguro &&
    registrar incidente
}
```

> `!clear` → não pode ser apagada por `/clear`
> `?` → pede confirmação antes de executar
> Juntos: proteção máxima com controle do usuário

---

## 7. Sequência com fallback `&&` / `||`

```
<resumir>(mensagem contém "resumir") [média] {
    resumir conversa &&
    listar pontos principais &&
    concluir~curto
    || avisar "Não foi possível resumir. Tente novamente."
}
```

> Se qualquer etapa do bloco `&&` falhar, o `||` executa o fallback.

---

## 8. Variáveis dinâmicas entre regras

```
set($nivel) = "iniciante" #global

<ajustar>(mensagem contém "modo *") {
    set($nivel) = $1 &&
    responder "Modo ajustado para: $1"
}

<explicar>(mensagem contém "explique *") {
    explicar $1 para nível=$nivel
}
```

**Teste:** `modo avançado` → `explique recursão` → explica em nível avançado

---

## 9. Execução imediata na declaração com `!agora`

```
<hello>(mensagem contém "oi", !agora) {
    responder "Olá! Sistema MRSC carregado e pronto."
}
```

> `!agora` faz a regra disparar no momento da declaração, sem esperar a condição ser acionada pelo usuário.

---

## 10. Bloco de múltiplas regras relacionadas

```
<sim>(sim | s | ok)     { confirmar };
<nao>(não | n | nope)   { cancelar };
<talvez>(talvez | quem sabe) {
    perguntar "Quer que eu decida por você?" &&
    aguardar resposta
}
```
