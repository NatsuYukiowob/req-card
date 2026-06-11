# Questioning Discipline (L-flow interviews)

The interview exists to surface hidden assumptions and edge cases — not to
fill a form. Borrowed from interview-me-style "senior architect" interviews.

## Rules

1. **Explore before asking.** Read the relevant files / docs / recent commits
   first. Never ask what the codebase already answers.
2. **One question per message.** Multiple-choice preferred: 3–4 options,
   your recommended option first and marked "(recommended)".
3. **Never ask obvious questions.** A question is obvious if a reasonable
   default exists and getting it wrong is cheap to fix. State such defaults
   as Assumptions on the card instead of asking.
4. **Ask questions that change what you would build:** scope cuts,
   contradictions between stated wishes, edge cases with real cost,
   irreversible or expensive-to-reverse choices.
5. **Hard cap: 7 questions.** Stop earlier the moment every card field is
   solid.
6. **Cap hit with major unknowns left?** Stop anyway. Write the unknowns
   into Assumptions as explicit risks and let the user decide at the
   confirmation gate.
7. **Task turns out small mid-interview?** Close early — fill the card,
   confirm, done. Say you misjudged the tier.

## Litmus test

Before sending a question, ask yourself: "If I guessed instead, would the
user's veto on the card catch a wrong guess cheaply?" If yes — guess, put it
in Assumptions, don't ask.
