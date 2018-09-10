# YeoJohnsonTrans.jl

[![Build Status](https://travis-ci.org/tk3369/YeoJohnsonTrans.jl.svg?branch=master)](https://travis-ci.org/tk3369/YeoJohnsonTrans.jl)
[![codecov](https://codecov.io/gh/tk3369/YeoJohnsonTrans.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/tk3369/YeoJohnsonTrans.jl)
[![Coverage Status](https://coveralls.io/repos/github/tk3369/YeoJohnsonTrans.jl/badge.svg?branch=master)](https://coveralls.io/github/tk3369/YeoJohnsonTrans.jl?branch=master)

This package provides an implementation of Yeo Johnson transformation.
See [Wikipedia - Power Transform](https://en.wikipedia.org/wiki/Power_transform)
for more information.

Requires Julia 0.7/1.0.

## Installation

```
] add https://github.com/tk3369/YeoJohnsonTrans.jl
```

## Usage

The simplest way is to just call the `transform` function with an array of numbers.

```
julia> using Distributions, UnicodePlots, YeoJohnsonTrans

julia> x = rand(Gamma(2,2), 10000) .+ 1;

TBD

julia> histogram(YeoJohnsonTrans.transform(x))

TBD

You can examine the power transform parameter (λ) dervied by the program:
```
julia> YeoJohnsonTrans.lambda(x).value
0.013544484565969775
```

You can transfrom the data using your own λ:
```
julia> histogram(YeoJohnsonTrans.transform(x, 0.01))

TBD
```

There's an option to scale the results by the geometric mean.
```
julia> histogram(YeoJohnsonTrans.transform(x; scaled = true))

TBD
```
