# Exemplos Básicos MRSC v4.0

---

## 1. Alternativas na condição com `|`

```
<saudacao>(olá | hi | hello | boa noite) {
    responder "Olá! Como posso ajudar hoje?"
}
```

**Teste:** digite `olá` ou `hi` ou `hello`

---

## 2. Confirmação obrigatória com `?`

```
<limpar?>(limpar regras) [absoluta] {
    apagar todas as regras &&
    responder "✅ Regras limpas!"
}
```

**Teste:** digite `limpar regras` → a IA pede confirmação antes de executar

---

## 3. Desativar e reativar com `~off` / `~on`

```
<pausar>(mensagem contém "pausar saudacao") {
    /off saudacao &&
    responder "Saudação pausada."
}

<reativar>(mensagem contém "ativar saudacao") {
    /on saudacao &&
    responder "Saudação reativada."
}
```

**Teste:** `pausar saudacao` → `olá` não responde → `ativar saudacao` → volta a funcionar

---

## 4. Fluxo condicional com `else if` / `else`

```
<tom>(detectar tom formal) { responder~formal }
else if (tom informal)     { responder~amigavel }
else                       { responder~neutro }
```

> `else if` e `else` herdam a prioridade da regra pai — não precisam declarar a própria.

---

## 5. Múltiplas regras numa linha com `;`

```
<sim>(sim | s | ok) { confirmar }; <nao>(não | n | nope) { negar }
```

**Teste:** `sim` ou `não`

---

## 6. Regra de uso único com `#1x`

```
<boas-vindas>(always) #1x {
    responder "Bem-vindo! Regras carregadas." &&
    listar regras ativas
}
```

> Executa uma vez no primeiro disparo e se apaga automaticamente.

---

## 7. Variável global simples

```
set($tom) = "formal" #global

<responder>(mensagem contém "responda") {
    responder com tom=$tom
}
```

**Teste:** `responda` → resposta no tom definido pela variável

---

## 8. Regra protegida que não pode ser apagada

```
<base>(always) [absoluta, !clear] {
    manter contexto da sessão ativo
}
```

> `!clear` garante que `/clear` não apague esta regra.
