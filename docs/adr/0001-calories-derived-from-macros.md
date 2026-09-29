# Calories are derived from Macros, never stored

An Entry stores grams of protein, carbohydrate and fat; Calories are computed
from them (4/4/9) at read time and never persisted as an independent column.
Storing both invites the two to disagree — a corrected macro value with a stale
calorie total is a bug the user sees and cannot explain, and it would destroy
trust in every other number in the app. This is also why the Tuna displays
Calories while the Bubbles display Nutrients: they are different kinds of thing,
and the UI says so.

## Consequences

Foods whose label calories don't match 4/4/9 (rounding, sugar alcohols, fiber
subtraction conventions) will display a calorie figure a few percent off the
package. Accepted: internal consistency matters more than matching a label.
