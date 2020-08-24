# Javascript Types

### Falsy Values

- the number 0
- the BigInt 0n
- null
- undefined
- the boolean false
- the number NaN
- the empty string "" (equivalent to '' or ``)

### Truthy Values:

- '0'
- 'false'
- []
- {}
- function () {}

Null is an Object in Javascript!

Nan is not equivalent to Nan!

### Equivalence check for floats:

```sql
0.1 + 0.2 = 0.30000000000000004
```

```sql
function areTheNumbersAlmostEqual(num1, num2) {
	return Math.abs( num1 - num2 ) < Number.EPSILON;
}

console.log(areTheNumbersAlmostEqual(0.1 + 0.2, 0.3));
```