# Modularity

| Name                      | Grow Gracefully? | Control Combo Impls? | Statically Detect Bad Combos? | Subtype-Polymorphic on Both Sides? | Share Common Code? | Less Chance of Name Conflicts? |
|---------------------------|-------------|----|----|----|----|----|
| Bridge (i.e. composition) | ./<br>(N+M) | -- | -- | -- | ./ | ./ |
| Nested Inheritance        | --<br>(N×M) | ./ | ./ | -- | -- | -- |
| Multiple Inheritance      | --<br>(N×M) | ./ | ./ | ./ | ./ | -- |

Maintenance considerations:

1. How fast is the number of subtypes of each side going to grow?
2. Does it need different algorithms for the different combinations?
3. Could it need different algorithms in the future?
   - You could break the DRY principle at this point
   - If you cannot anticipate a point at which it would not be breaking the DRY principle, then DO NOT break it now
4. Could it use the same algorithm in the future?
   - Use an architecture that would allow you to conform with the DRY principle when merging algorithms in the future

Semantic considerations:

1. Are any nonsensical combinations? Are you willing to implement combo restrictions in runtime code?
2. Do you need a polymorphic type for both sides?
