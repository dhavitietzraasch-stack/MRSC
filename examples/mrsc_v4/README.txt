━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MRSC — Model of Rules with Complex System
Version 4.0  |  License: MIT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

MRSC is a lightweight DSL (domain-specific language) that gives
structured, persistent, and prioritized behavioral instructions
to AI models — regardless of which AI you use.

The AI executes     → interprets intent, bridges natural language
                      and formal syntax, transforms it into commands.
The MRSC communicates → organizes interaction, applies defined rules,
                        and structures the conversation layer.
The user controls   → writes rules once; the system applies always.

Think of MRSC as the traffic manual and the AI as the driver:
the manual defines the rules, but the driver reads signs, gestures,
and spoken words to apply them. Natural language and formal syntax
coexist — the AI resolves both without losing consistency.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. BASIC RULE STRUCTURE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

<nickname>(condition) [priority] #scope {action}

  <nickname>   Unique rule identifier (word, number, emoji — anything).
  (condition)  What triggers the rule.
  [priority]   low | medium | high | absolute  (default: low)
  #scope       #session (default) | #global | #1x
  {action}     What the AI does when triggered.

Only <nickname>, (condition), and {action} are required.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
2. MANAGING RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  /list              → show all active rules
  /off <nickname>    → pause a rule without deleting it
  /on  <nickname>    → resume a paused rule
  /del <nickname>    → permanently delete a rule
  /clear             → delete all non-protected rules
  /execute <nickname> → manually trigger a rule
  /info <nickname>   → show full details of a rule
  /strict on|off     → enable/disable strict syntax mode

  One-time rules:    use #1x or priority [-1]
  Confirmation gate: add ? to nickname  →  <delete?>
  Protection:        add !clear inside priority  →  [absolute, !clear]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
3. KEY OPERATORS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  |    OR in conditions:     (if 'hi' | 'hello')
  !    NOT in conditions:    (if !error)
  &&   AND / sequence:       {task A && task B}
  ||   Fallback:             {A && B || C} — runs C if A→B fails
  *    Wildcard — captures:  first * → $1, second → $2
  @    Target:               {alert@user}  {delete @$1}
  ~    Modifier:             {respond~short}
  =    Parameter:            {respond(tone=sarcastic)}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
4. VARIABLES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  set($name) = "value"           → session scope
  set($name) = "value" #global   → persists across conversations
  $name                          → reads the stored value

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
5. SYSTEM NAMESPACE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  Never use nicknames starting with  .~
  These are reserved for the core kernel (e.g. <.~PROTECT-CORE>).
  Any attempt to declare them as a user rule will be blocked.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
6. QUICK EXAMPLES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

// Simple greeting response
<hi>(if I say 'hello') { respond~short }

// Save a reminder from wildcard capture
<note>(if message contains {remind me to *}) { save $1 }

// Full reset (protected — cannot be cleared)
<reset>(if I say 'reset total') [absolute, !clear] { delete all rules }

// Status check with conditional flow
<status>(if I ask for status) [medium] { list active rules }
else if (no active rules) { inform "no active rules" }
else { show count }

// Universal rule dispatcher
<dispatch>(if message contains {@$1:$2}) #global [absolute] {
    execute $2 on @$1
}

// One-shot disposable
<_>(if I say 'ping') #1x { respond "pong" }

// Move with two captured values
<move>(if message contains {move * to *}) { move $1 to $2 }

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
7. FILE MAP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  MRSC-prompt-en-v4.txt       Main prompt (English)
  MRSC-prompt-ptbr-v4.txt     Main prompt (Portuguese BR)
  kernel_AI.txt               Core runtime kernel
  kernel_optional.txt         Optional security layer (ZTA)
  sys_user.txt                User session config
  INSTRUCOES.md               Step-by-step setup guide
  README.txt                  This file

Loading order (recommended):
  1. MRSC-prompt-[lang]-v4.txt
  2. kernel_AI.txt
  3. kernel_optional.txt  (optional)
  4. sys_user.txt         (optional)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

GitHub:  https://github.com/dhavitetzraasch-stack/MRSC
Version: 4.0
License: MIT

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
