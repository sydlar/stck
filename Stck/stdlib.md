The STCK 2.0 Standard Library
=============================

Loading the standard library:
#load Stck.Console/Samples/stdlib.stck

Derived stack operators
-----------------------
rot -> ```[[] swap << swap << swap >> app] rot #```
over -> ```[swap dup rot rot] over #```
2dup -> ```[over over] 2dup #```

Booleans
--------
Booleans uses the classic lambda calculus encoding

TRUE = λa . λb . a
FALSE = λa . λb . b

true -> ```[[app .]] true #```
false -> ```[[app swap .]] false #```

From there we can define boolean operators
IF = λp . λt . λe . p t e

if -> ```[[] swap << swap << swap app app] ? #```
not -> ```[[false] [true] if] not #```
and -> ```[[[true] [false] if] swap << [false] if] and #```
or -> ```[not swap not and not] or #```

Implication and equivalence
```[not or] <- #```
```[swap <-] -> #```
```[2dup -> rot rot <- and] <-> #```