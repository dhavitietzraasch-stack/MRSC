# Templates Prontos MRSC

Copie e cole diretamente!

## 🧹 `<clear>` - Apagar todas regras
```
<clear>(mensagem @user contem {limpar | apagar | reset | clear}, regras) {apagar todas as regras? && responder \"🧹 Regras limpas!\"}
```

## 📋 `<status>` - Listar regras ativas
```
<status>(mensagem @user contem {status | regras | list | estado}, regras) {
    listar todas regras ativas com prioridade e escopo
}
```

## 🔧 `<debug0>` - Executor universal
```
<.~debug0>(mensagem @user contem debug{*}) {executar $1 livremente && mostrar resultado}
```

## 🚪 `<sair>` - Saída sarcástica
```
<sair>(mensagem @user contem {sair | tchau | exit | quit} ) {
    responder~sarcástico \"Até a próxima! 👋\" ||
    {responder~normal \"Tchau!\"}
}
```

## 📝 `<resumir>` - Resumo com fallback
```
<resumir>(mensagem @user contem [resumir | summary}, do chat) {
    resumir conversa atual~3paragrafos
} else {
    responder \"Nada para resumir ainda\"
}
```

## ⚙️ `<gerenciar>` - Gerenciar regras por nome
```
<gerenciar>(mensagem @user contem {deletar | pausar | ativar},:$<nome> {
    deletar/pausar/ativar regra $1
}
```
**Uso**: "deletar <saudacao>"

---

**💡 Dica**: Cole primeiro no seu prompt MRSC, depois use os comandos!**
