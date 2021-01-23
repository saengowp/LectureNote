# Sorting

## Stable Marriage Problem

Let there be n men and women.

each person has a rank of preference of all opposite gender

The marriage will *not* be stable if all these condition is met

- i-th man and j-th woman are not married
- i-th man like j-th woman more than his current partner
- j-th woman like i-th man more than her current partner

### Solution

for each men, go through the ranked list of women he preferred and eliminate
"incompatible women" (women who is already paired to the partner she ranked better than this man)

Once we found our first non-incompatible women, unpair her partner and eliminate her from her partner's list (if she has any) and pair with her.

First, we show that elimination is correct. Suppose we somehow pair with the incompatible woman,
That mean we are ranked lower than her current partner by her and since her partner ranked her best in the list
because all his better ranked women are eliminated (or because she is the first ranked for base case). Then pairing her and her partner
is more stable. So we can't really pair with an incompatible woman.

Second, we show that in the end, everyone is paired. Suppose there're an unpaired man. We know that every woman must be paired
because otherwise they could have just pair with this man at some point. But there must be unpaired woman for every unpaired man.
A contradiction.

The algorithm halt in atmost $n^2$ step beacuse each step eliminate a women in a list of some man.

### Discussion

#### Symmetry of the solution

For men, this solution produce the best possible pairing that is stable. 
For women, all the men who ranked lower than the final pairing have eliminate her from their list because pairing with her final partner is more stable than with them. In other words, she got the lowest ranked man who is not incompatible as her partner. A situation inverse of that of men. A worse possible pairing.


[TODO]
[Sorting]
