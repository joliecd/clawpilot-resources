# Prompt: Log Hours in ESXP

**Best for:** Adding labor hours for one or more customers to your ESXP weekly time entry — saves as draft for your review before submitting.

_Credit: Ryan Otis_

---

## Prompt

```
Are you able to access my Labor Entry on the ESXP CSA dashboard?
Here is the URL: https://esxp.microsoft.com/#/time/weekview

Please add [NUMBER] hour(s) for [CUSTOMER NAME] on [DAY, e.g. Friday May 8] and save as draft.
```

---

## Notes

- Clawpilot saves as **draft only** — you must submit yourself via "Agree & Submit All"
- After it confirms, verify: row total for the customer, the day-header hours, and the week total
- You can chain multiple customers in one prompt: "Add 1 hour for [CUSTOMER A] on Wednesday and 2 hours for [CUSTOMER B] on Thursday"
- The "Save As Draft" button greys out once the draft is committed — that's expected and means it worked
