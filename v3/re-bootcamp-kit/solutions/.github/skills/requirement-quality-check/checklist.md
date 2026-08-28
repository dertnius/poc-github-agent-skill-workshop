# Requirement quality checklist

## Weak words (not testable)
should, may, could, fast, quickly, slow, easy, user-friendly, intuitive, appropriate,
adequate, sufficient, robust, flexible, efficient, seamless, etc., and/or, some, many,
most, if possible, as needed, normally, usually, depending on the case

## One requirement = one sentence
- Split a sentence with "and" into separate requirements.
- No "and/or". Choose one. Or write two requirements.

## Actor
- Every requirement names who or what does the action. Example: "The customer", "The system".
- "It must be possible to ..." has no actor. Rewrite it.

## Measurable
- Time: give a number and a unit. Example: "within 2 seconds".
- Amount: give a number and a currency. Example: "CHF 5,000".
- Quality words become numbers or a named standard.

## Complete
- Every "if" has an "else". Say what happens in the other case.
- Every error case has a result or a message.

## Consistent
- Terms match the [glossary](../../../samples/glossary.md). One term per concept.
