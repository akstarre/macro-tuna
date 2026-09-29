# Targets use Katch-McArdle when body fat is known, Mifflin-St Jeor otherwise

Basal metabolic rate is calculated from lean body mass via Katch-McArdle when the
Profile carries a body fat percentage, and from total bodyweight via
Mifflin-St Jeor when it does not. Total daily energy expenditure is that figure
times an activity multiplier. Goal then applies a 20% deficit for weight loss, a
10% surplus for weight gain or muscle gain, and no change for maintenance.
Protein is set from 1.6 to 2.2 g per kg — of lean mass when known, total mass
otherwise — with fat at 25% of calories and carbohydrate taking the remainder.

Katch-McArdle is more accurate than Mifflin-St Jeor when lean mass is genuinely
known, because two people at the same weight with different body composition have
materially different metabolic rates. But it is *less* accurate when the body fat
figure is bad, and consumer scales and visual estimates are bad. Choosing per
Profile rather than picking one formula globally gets the accuracy when the input
justifies it and degrades safely when it doesn't. Mifflin-St Jeor is the fallback
rather than Harris-Benedict because it is the better-validated of the
weight-based equations.

## Consequences

The formula used is recorded on the Target Set, so a user who later adds a body
fat percentage can see why their numbers moved. Body fat percentage must be
optional everywhere, and an obviously implausible value should be challenged
rather than silently fed into the equation. The 20%/10% rates and the protein
range are deliberately conservative defaults, not claims of optimality — the
override exists because individual variation exceeds the precision of any of
these formulas.
