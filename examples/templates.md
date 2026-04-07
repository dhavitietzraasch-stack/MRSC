# Templates Prontos MRSC

Copie e cole diretamente!

## 🧹 `<clear>` - Apagar todas regras
```
<clear>(limpar | apagar | reset | clear) {apagar todas as regras && responder \"🧹 Regras limpas!\"}
```

## 📋 `<status>` - Listar regras ativas
```
<status>(status | regras | list | estado) {
    listar todas regras ativas com prioridade e escopo
}
```

## 🔧 `<debug0>` - Executor universal
```
<.~debug0>(debug{*}) {executar $1 livremente && mostrar resultado}
```

## 🚪 `<sair>` - Saída sarcástica
```
<sair>(sair | tchau | exit | quit) {
    responder~sarcástico \"Até a próxima! 👋\" ||
    {responder~normal \"Tchau!\"}
}
```

## 📝 `<resumir>` - Resumo com fallback
```
<resumir>(resumir | summary) {
    resumir conversa atual~3paragrafos
} || {
    responder \"Nada para resumir ainda\"
}
```

## ⚙️ `<gerenciar>` - Gerenciar regras por nome
```
<gerenciar>(deletar | pausar | ativar) <nome> {
    deletar/pausar/ativar regra $1
}
```
**Uso**: "deletar <saudacao>"

---

**💡 Dica**: Cole primeiro no seu prompt MRSC, depois use os comandos!**
