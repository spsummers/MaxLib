## division
Some implementations of reciprocation algorithms, prioritising low latency.

# reducedLUTDivide
A division based on binomial expansion, requiring a lookup, multiplication and some additional fixed point arithmetic logic.

```
Divider.reducedLUTDivideFloat(DFEVar x, int nLUTBits)
```
Reduced LUT division for floating point numbers.
For `dfeFloat(8, 24)` achieves 20 bits of mantissa precision with one 25x25 multiplier, and two BRAMs, taking 5 clock cycles.
21 bits of mantissa precision can be achieved at the cost of double the BRAM usage.

```
Divider.reducedLUTDivide()
```
Reduced LUT division for fixed point numbers.
The algorithm is mostly the same as for floating point, but requires a shift before and after lookup to make the msb of the denominator '1'.

```
Divider.reducedLUTDivideIgnore()
```
Reduced LUT division for fixed point numbers, with 'ignore' bits. 
When min(x) > lsb(x), the output type of 1/x, defined by max(1/x), can be 1/min(x) rather than 1/lsb(x).
The values min(x) > x > lsb(x) can still be used for extra accuracy on the result.
