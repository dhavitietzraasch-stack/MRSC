# Como Contribuir com o MRSC

O MRSC é um projeto aberto. Toda contribuição — seja sintaxe nova, correção de bug, tradução ou exemplo — é bem-vinda.

---

## Tipos de contribuição

### 🆕 Sugerir nova sintaxe

1. Crie um exemplo prático mostrando o **problema atual** (o que não é possível fazer hoje)
2. Proponha a nova sintaxe com **3–5 casos de uso reais**
3. Explique o **impacto em regras existentes** (é breaking change?)
4. Abra uma **Discussion** no GitHub antes de abrir um PR

### 🐛 Reportar ambiguidade ou bug

Use este formato:

```
Problema:             [descreva a ambiguidade ou comportamento inesperado]
Regra que falha:      [exemplo mínimo reproduzível]
Comportamento atual:  [o que acontece]
Comportamento esperado: [o que deveria acontecer]
IA testada:           [Claude | ChatGPT | Gemini | outra]
```

### 🌍 Submeter tradução

- Arquivos de prompt ficam em `prompts/`
- Mantenha **fidelidade técnica exata** — não adapte operadores ou nomes de símbolos
- Teste colando o prompt traduzido em pelo menos uma IA antes de submeter
- Inclua no PR: qual IA foi usada no teste e o resultado da confirmação

### 📝 Adicionar exemplos

- Exemplos básicos → `basico.md`
- Exemplos avançados → `avancado.md`
- Templates prontos → `templates.md`
- Todo exemplo deve ter: código funcional + caso de teste + resultado esperado

---

## Regras para Pull Requests

✅ **Obrigatório:**
- Exemplo funcional incluído
- Justificativa clara (por que essa mudança é necessária?)
- Impacto em versões anteriores declarado (breaking? additive?)
- Testado em pelo menos 2 IAs diferentes
- CHANGELOG.md atualizado

❌ **Evite:**
- Mudanças que quebrem sintaxe existente sem justificativa forte
- Sintaxes que aumentem ambiguidade de parsing
- Sugestões sem exemplo prático e testado
- PRs que misturem múltiplas features sem relação

---

## Como testar antes de submeter

```
1. Cole o prompt principal (MRSC-prompt-en-v4.txt ou ptbr) na IA
2. Declare 5–10 regras variadas cobrindo o que seu PR muda
3. Teste todos os cenários descritos no seu PR
4. Confirme que regras das versões anteriores continuam funcionando
5. Documente o resultado dos testes no PR (IA usada + comportamento observado)
```

---

## Estrutura do repositório

```
MRSC/
├── MRSC-prompt-en-v4.txt       Prompt principal (EN)
├── MRSC-prompt-ptbr-v4.txt     Prompt principal (PT-BR)
├── kernel_AI.txt               Runtime core
├── kernel_optional.txt         Camada de segurança ZTA
├── sys_user.txt                Config de sessão do usuário
├── basico.md                   Exemplos básicos
├── avancado.md                 Exemplos avançados
├── templates.md                Templates prontos para uso
├── CHANGELOG.md                Histórico de versões
├── CONTRIBUTING.md             Este arquivo
├── INSTRUCOES.md               Guia de uso rápido
└── README.txt                  Visão geral do projeto
```

---

**Obrigado por tornar o MRSC melhor! 🚀**

GitHub: https://github.com/dhavitetzraasch-stack/MRSC
License: MIT
