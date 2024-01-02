# Prototypes

[![CI](https://github.com/eloualiche/Prototypes.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/eloualiche/Prototypes.jl/actions/workflows/CI.yml)


`Prototypes.jl` is a placeholder package for some functions that I use in julia frequently.

So far the package provides one function to tabulate data in a dataframe

## Installation

`Prototypes.jl` is a not yet a registered package.
You can install it from github  via

```julia
import Pkg
Pkg.add(url="https://github.com/eloualiche/Prototypes.jl")
```

## Examples


### Tabulate data

First import the monthly stock file and the compustat funda file
```julia
using DataFrames
using Prototypes
using PalmerPenguins

df = DataFrame(PalmerPenguins.load())

tabulate(df, :island)
tabulate(df, [:island, :species])
```

### Custom Logging

Here is an example where you can create a custom logger and redirect logging to different files
```julia
custom_logger("file_to_log", output_dir="./log", # where are the files generated
    filter=[:StatsModels], # debug file will not have messages from StatsModels
    log_date_format="yyyy-mm-dd HH:MM:SS", # time stamp for messages
    overwrite=true) # overwrite old log files (with the same name)

# if you have run the previous example
@info tabulate(df, :island)
@warn tabulate(df, :island)
@debug tabulate(df, :island)
```
