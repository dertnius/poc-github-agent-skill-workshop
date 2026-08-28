# Example of a good user story

US-042 Freeze a card in the app

As a customer,
I want to freeze my card in the app,
so that nobody can use it while I look for it.

## Acceptance criteria

### AC-1: Freeze an active card
Given my card is active
When I tap "Freeze card" and confirm
Then the card status is "Frozen" within 5 seconds
And I see the message "Your card is frozen."

### AC-2: Payment with a frozen card
Given my card is frozen
When a merchant sends a payment request for this card
Then the payment is declined with reason code CARD_FROZEN

### AC-3: Unfreeze
Given my card is frozen
When I tap "Unfreeze card" and confirm with my app PIN
Then the card status is "Active" within 5 seconds

## Open questions
- Q1: Can a joint account holder freeze the other holder's card?
