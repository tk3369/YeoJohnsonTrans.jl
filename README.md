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

julia> histogram(YeoJohnsonTrans.transform(x))

julia> histogram(YeoJohnsonTrans.transform(x))
             ┌────────────────────────────────────────┐ 
   (0.6,0.8] │▇▇ 168                                  │ 
   (0.8,1.0] │▇▇▇▇▇▇▇▇▇▇▇▇ 837                        │ 
   (1.0,1.2] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1586            │ 
   (1.2,1.4] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 2089    │ 
   (1.4,1.6] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 2307 │ 
   (1.6,1.8] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1816        │ 
   (1.8,2.0] │▇▇▇▇▇▇▇▇▇▇▇▇▇ 914                       │ 
   (2.0,2.2] │▇▇▇▇ 253                                │ 
   (2.2,2.4] │ 28                                     │ 
   (2.4,2.6] │ 2                                      │ 
             └────────────────────────────────────────┘ 
```

You can examine the power transform parameter (λ) dervied by the program:
```
julia> YeoJohnsonTrans.lambda(x).value
-0.20252181252892174
```

You can transfrom the data using your own λ:
```
julia> histogram(YeoJohnsonTrans.transform(x, -0.3))
             ┌────────────────────────────────────────┐ 
   (0.6,0.7] │▇ 49                                    │ 
   (0.7,0.8] │▇▇▇▇▇ 204                               │ 
   (0.8,0.9] │▇▇▇▇▇▇▇▇▇▇▇ 427                         │ 
   (0.9,1.0] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 703                   │ 
   (1.0,1.1] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 916             │ 
   (1.1,1.2] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1103        │ 
   (1.2,1.3] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1287   │ 
   (1.3,1.4] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1376 │ 
   (1.4,1.5] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1354  │ 
   (1.5,1.6] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 1125       │ 
   (1.6,1.7] │▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 773                 │ 
   (1.7,1.8] │▇▇▇▇▇▇▇▇▇▇▇ 432                         │ 
   (1.8,1.9] │▇▇▇▇▇ 197                               │ 
   (1.9,2.0] │▇ 45                                    │ 
   (2.0,2.1] │ 8                                      │ 
   (2.1,2.2] │ 1                                      │ 
             └────────────────────────────────────────┘ 
```

