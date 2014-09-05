# VennDiagrams

Generate Venn diagrams in Julia. Uses the excellent 
[Compose](https://github.com/dcjones/Compose.jl) package.

## Usage

```julia
using VennDiagrams

c1 = [0:5] # Can be any iterable
c2 = [3:10]

p = venn(c1, c2)
draw(PDF("beaut1.pdf", 8cm, 10cm), p)

c3 = [0:2:12]

p = venn(c1, c2, c3, proportional=false)
draw(PDF("beaut3.pdf", 8cm, 10cm), p)
```

## Reference

```
venn(xs::Union(AbstractArray,Set)...;
proportional::Bool = true,
labels=Union(Bool,Vector{String}), 
colors=Union(Bool,Vector{ColorValue},Vector{AlphaColorValue}))
```

Simply enough, everything is accessible through the ``venn`` function, with 
optional selection of proportinality, labels, and colors.

For more control of stroke, linewidth, font size/type, etc... use the 
``compose`` function to modify the venn diagram before plotting:

```julia
using Compose

compose(p, stroke("black"), linewidth(2mm))
```
