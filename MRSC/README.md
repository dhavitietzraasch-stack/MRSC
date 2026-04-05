# MRSC - Modelo de Regras com Sistema Complexo ![v2.3](https://img.shields.io/badge/version-v2.3-blue.svg)

## O que é MRSC?

MRSC (Modelo de Regras com Sistema Complexo) é uma DSL leve e poderosa inspirada em Python, JavaScript e sistemas de regras de produção como CLIPS e Prolog. Projetada especificamente para instruir modelos de IA com regras estruturadas de forma intuitiva e progressiva.

Com MRSC, você declara regras simples no formato:  
**`<apelido>(condição) [prioridade] #escopo {ação}`**

A IA interpreta essas regras em tempo real durante a conversa, criando um sistema de comportamento dinâmico e controlável.

## Por que usar MRSC?

- **Modelo-agnóstico**: Funciona com qualquer IA que siga instruções
- **Progressivo**: Comece simples, evolua para regras complexas
- **Extensível**: Sintaxe cresce organicamente com a comunidade
- **Leve**: Zero dependências, apenas texto estruturado
- **Debugável**: Transparente e fácil de gerenciar

## Exemplo Rápido

```
<saudacao>(olá | hi | hello) {responder \"Olá! Como posso ajudar?\"}
<clear>(limpar | apagar regras) {apagar todas as regras && responder \"Regras limpas!\"}
```

## Como Usar (3 passos)

1. **Copie o prompt** do seu idioma: [Português](prompts/MRSC-pt-BR.md) | [English](prompts/MRSC-en.md) | [Español](prompts/MRSC-es.md)
2. **Cole na IA** e confirme que ela entendeu o MRSC
3. **Declare suas regras** - a IA executará automaticamente!

## Exemplos Prontos

Veja exemplos práticos em [exemplos básicos](examples/basico.md), [avançados](examples/avancado.md) e [templates prontos](examples/templates.md).

## Contribuição

Quer melhorar o MRSC? Veja [como contribuir](CONTRIBUTING.md).

## Licença

[MIT License](LICENSE) - © MRSC Project / Comunidade Aberta
