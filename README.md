# MatchCore

[![Build Status](https://travis-ci.com/thautwarm/MatchCore.jl.svg?branch=master)](https://travis-ci.com/thautwarm/MatchCore.jl)
[![Codecov](https://codecov.io/gh/thautwarm/MatchCore.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/thautwarm/MatchCore.jl)

A minimal implementation of optimized pattern matching.

It is extracted from MLStyle.jl and sightly modified, for users who don't need advanced features like extensible patterns.

It's faster to startup, produce efficient and "runtime free" code equivalent to MLStyle.

MatchCore lacks of many non-primitive patterns, like `Dict`s, ranges, view/active patterns.

However, expression matching is still available:

```julia
julia> @smatch :(a.(b, c)) begin
           :($a.($(bc...))) => (a, bc)
       end
(:a, Any[:b, :c])
```