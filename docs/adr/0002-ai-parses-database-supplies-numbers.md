# The AI parses language; the database supplies the numbers

Food logging happens through conversation, so an LLM interprets what the user
says. Its output is strictly structural — the food identified, the quantity, the
unit — and every Nutrient value is then looked up in a local food database. The
LLM never emits grams or Calories directly.

The reason is that a tracking app's entire value is the user's belief that the
numbers are real. A hallucinated 40g of protein is indistinguishable from a true
one to the user, and one discovered fabrication retroactively poisons every
figure the app has ever shown. Parsing is a language task, which LLMs are good
at; nutrition recall is a database task, which they are bad at.

## Consequences

When no database match is found, the Entry may fall back to an AI estimate, but
it must be visibly marked as estimated and be editable. Silent estimation is
forbidden. This also means the food database, not the model, is the thing whose
coverage determines product quality.
