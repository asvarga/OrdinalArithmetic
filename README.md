# OrdinalArithmetic

An Arend implementation of ordinal arithmetic. 

Ported from a Liquid Haskell implementation here: https://github.com/asvarga/ordinal-arithmetic

## TODO

- implement ordinals as both `ω^a * n + b` and `ω^a + b`
- implement operations on both
- prove properties about the second
    - this will probably be simpler and use `<=` instead of `<`
- prove equivalence between them and transport across

See: https://www.youtube.com/watch?v=Rt2OrG3IHkU

## Files

Here are some failed attempts:

#### Ordinals.ard 

- An `Ord'` datatype that represents ordinals
- An `Ord` record that wraps and `Ord'` and a proof that it is in Cantor Normal Form (`nf`)
- Successor function on `Ord`, with proof that it preserves nf
- Addition on `Ord'`, but without proof that it preserves nf

I've failed to prove that addition preserves cnf. Combining the 3 cases involved in addition with the 3 cases involved in `nf` of each of the 2 arguments has led to an explosion in cases that I can't reconcile. The real problem stems from the fact that once I've pattern `\elim`-ed on `(x, nfx)` as `(ord xa xn xb, nfx)`, I can't further refine `(xa, xb)` and update what I know about `nfx`.

#### Ordinals2.ard

Trying to directly fold proof on normal form into `Ord`, without an extraneous `Ord'` type. This gives me the error: `Cannot infer the sort of a recursive data type`

#### Ordinals3.ard

Tried another representation of `nf` with only 2 constructors, but it still leads to the same amount of case analysis later.

#### CaseTest.ard

A simpler/similar example proving a proposition about the result of a function. Had to use this trick: https://arend-lang.github.io/documentation/tutorial/PartI/case#elim-in-case


<!--
## Questions

One over-arching question I have is about when to use recursion vs induction. For example, instead of implementing addition as a function `\func + (x y : Ord) : Ord => ...`, would I have more luck axiomatizing it as a datatype like: 

```arend
\data _+_=_ (x y z : Ord') \elim x, y, z
  | zero, y, y => left-id
  | x, zero, x => right-id
  | ord xa xn xb, ord ya yn yb, ord za zn zb => ...
```

and then proving it decidable?
-->

