# OrdinalArithmetic

An Arend implementation of ordinal arithmetic


### Status

All I've got working is:

- An Ord' datatype that represents ordinals
- An Ord record that wraps and Ord' and a proof that it is in Cantor Normal Form
- Successor function on Ord, with proof that it preserves nf
- Addition on Ord', but without proof that it preserves nf

I've failed to prove that addition preserves cnf. It has devolved into a nightmarish case analysis. Combining the 3 cases involved in addition with the 3 cases involved in nf of each of the 2 arguments has led to an explosion in cases that I can't reconcile.

The real problem stems from the fact that once I've pattern \elim-ed on (x, nfx) as (ord x a xn xb, nfx), I can't further refine (xa, xb) and update what I know about nfx.

### Try

Next I'll try changing my representation of ordinals to use lists of (Pos, Ord) that are sorted based on the Ord. Look into the tutorial's handling of sorted lists.






