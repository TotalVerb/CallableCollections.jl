# CallableCollections

[![Build Status](https://travis-ci.org/TotalVerb/CallableCollections.jl.svg?branch=master)](https://travis-ci.org/TotalVerb/CallableCollections.jl)

This is just a fun experiment for callable collections in Julia.

Sets behave like functions that return booleans:

```julia
julia> prime = IntSet([2, 3, 5, 7, 11])
IntSet([2, 3, 5, 7, 11])

julia> map(prime, 1:10)
10-element Array{Bool,1}:
 false
  true
  true
 false
  true
 false
  true
 false
 false
 false
```

Arrays and dictionaries behave like functions that map key to value:

```julia
julia> square = [1, 4, 9, 16]

julia> square(3)
9
```

The union (∪) and intersection (∩) operations from are generalized to functions
that return booleans:

```julia
julia> isprimeoreven = isprime ∪ iseven
(anonymous function)

julia> filter(isprimeoreven, 1:10)
8-element Array{Int64,1}:
  2
  3
  4
  5
  6
  7
  8
 10

julia> isasciiupper = isascii ∩ isupper
(anonymous function)
```

Some abstract array or list higher-order functions can be generalized to
functions too. `map`, for example, is a bit like multi-argument compose:

```julia
julia> sqrtpluscbrt = map(+, sqrt, cbrt)
(anonymous function)

julia> sqrtpluscbrt(64)
12.0
```
