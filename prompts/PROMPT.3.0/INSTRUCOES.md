# HOW TO USE MRSC IN YOUR AI

## Step 1 — Copy the prompt
Open the file `MRSC-prompt-en.md` and copy all its content.

## Step 2 — Paste into your AI
Paste the content into the chat of your preferred AI
(Claude, ChatGPT, Gemini, or any instruction-following model).

## Step 3 — Ask for translation
Type exactly this after pasting:

> "Translate all of this to my language and confirm
> that you understood and are ready to use the MRSC rule system."

## Step 4 — Start declaring rules
Once the AI confirms, you can start declaring rules. Example:

> `<clear>(if I say 'clear') [absolute, !clear] {delete all rules except this one}`

## Step 5 — Save for reuse (optional)
After the AI translates, copy the translated version and
save it in your AI's custom instructions or memory settings.
That way you won't need to paste it every time.

---

## Quick example of rules to try

```
// List all active rules
<status>(if I ask for status) [medium] {list active rules}

// Universal executor — runs any command on any rule
<debug0>(if message contains {@$1:$2}) #global [absolute] {execute $2 on @$1}

// Exit with sarcasm
<exit>(if I say 'exit' | 'quit' | 'q') [low] {respond(tone=sarcastic)~short}
```

---

## About MRSC

MRSC (Model of Rules with Complex System) is a lightweight DSL
designed to give structured, persistent, and prioritized instructions
to AI models — regardless of which AI you use.

GitHub: https://github.com/YOUR-USERNAME/MRSC
Version: 2.3
License: MIT
