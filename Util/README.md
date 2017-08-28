## Misc utilities library
Extends some of the standard libraries functionality.  
Added ``myString.fun(string_arg, ...)`` methods can be called just like the rest from standard library ``myString_arg:fun(...)`` if you prefer.

### Full interface

| Function(args) | Return type | Return description
| --- | --- | --- |
| ``math.clamp (Number var, Number min, Number max)`` | ``Number`` | 1st argument limited with upper and lower bounds (nil = no bound) |
| ``math.sgn (Number)`` | ``Number`` | 1 if arg positive, -1 if arg negative, 0 if arg equal zero |
| ``math.round (Number var, Number decimals)`` | ``Number`` | 1st argument rounded to given number of decimals (default 1) |
| ``table.empty (Table)`` | ``Bool`` | true if table has no values at all, false otherwise |
| ``table.shallowcopy (Table)`` | ``Table`` | table with all values copied directly from 1st argument |
| ``table.deepcopy (Table)`` | ``Table`` | table with all values copied from original, deeper tables copied recursively inside |
| ``myString:beginswith (String)`` | ``Bool`` | true if myString begins with parameter string (no pattern) |
| ``myString:startswith (String)`` | ``Bool`` | same as myString:beginswith(...) |
| ``myString:endswith (String)`` | ``Bool`` | true if myString ends with parameter string (no pattern) |
| ``myString:contains (String)`` | ``Bool`` | true if myString contains parameter string (no pattern) |
