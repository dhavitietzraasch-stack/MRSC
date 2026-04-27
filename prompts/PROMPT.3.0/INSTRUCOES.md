# HOW TO USE MRSC IN YOUR AI
### MRSC v4.0 — Quick Start Guide

---

## Step 1 — Choose your prompt file

| File | Use when |
|------|----------|
| `MRSC-prompt-en-v4.txt`   | AI set to English |
| `MRSC-prompt-ptbr-v4.txt` | AI set to Portuguese (BR) |

Open the file and copy **all** of its content.

---

## Step 2 — Paste into your AI

Paste the copied content into the chat of your preferred AI
(Claude, ChatGPT, Gemini, or any instruction-following model).

---

## Step 3 — Confirm the AI understood

After pasting, type:

> "Confirm that you understood and are ready to use the MRSC rule system."

The AI will acknowledge and confirm it's listening for rules.

---

## Step 4 — (Optional) Load kernel files

For advanced sessions, paste the kernel files **after** the main prompt:

| File | Purpose |
|------|---------|
| `kernel_AI.txt`       | Core runtime: confidence gate, fallback, checkpoint |
| `kernel_optional.txt` | Security layer: ZTA, silence filter, shutdown mode |

Load `kernel_AI.txt` first. `kernel_optional.txt` is optional — only load it
if you want the full security stack active.

---

## Step 5 — (Optional) Configure your session

Fill in `sys_user.txt` with your preferences (language, name, response style, etc.)
and paste it after the kernel files. The AI will apply those defaults automatically.

---

## Step 6 — Start declaring rules

Once the AI confirms, declare your rules. Examples:

```
// Protected reset rule
<clear>(if I say 'clear') [absolute, !clear] {delete all rules except this one}

// List all active rules
<status>(if I ask for status) [medium] {list active rules}

// Universal executor — runs any command on any rule
<dispatch>(if message contains {@$1:$2}) #global [absolute] {execute $2 on @$1}

// Exit with sarcasm
<exit>(if I say 'exit' | 'quit' | 'q') [low] {respond(tone=sarcastic)~short}

// Capture and reuse wildcard values
<move>(if message contains {move * to *}) {move $1 to $2}

// One-shot disposable rule
<_>(if I say 'ping') #1x {respond "pong"}
```

---

## Step 7 — Save for reuse (optional)

After the AI loads everything, copy the final translated/configured state
and save it in your AI's custom instructions or memory settings.
That way you won't need to paste it every time.

---

## File map

```
MRSC/
├── MRSC-prompt-en-v4.txt       ← Main prompt (English)
├── MRSC-prompt-ptbr-v4.txt     ← Main prompt (Portuguese BR)
├── kernel_AI.txt               ← Core runtime kernel
├── kernel_optional.txt         ← Optional security layer (ZTA)
├── sys_user.txt                ← User session config
├── INSTRUCOES.md               ← This file
└── README.txt                  ← Project overview
```

---

## Loading order (recommended)

```
1. MRSC-prompt-[lang]-v4.txt   ← always first
2. kernel_AI.txt               ← always second (if using kernel)
3. kernel_optional.txt         ← optional, after kernel_AI
4. sys_user.txt                ← optional, last
```

---

## About MRSC

MRSC (Model of Rules with Complex System) is a lightweight DSL
designed to give structured, persistent, and prioritized instructions
to AI models — regardless of which AI you use.

- GitHub: https://github.com/dhavitetzraasch-stack/MRSC
- Version: 4.0
- License: MIT
