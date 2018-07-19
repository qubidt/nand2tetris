Boolean Algebra Cheat Sheet
===========================

Basic operators
---------------

| Name       | Math symbols | Ascii     | Other      |
|------------|--------------|-----------|------------|
| implies    | `⊃` `⇒` `→`  | `->`      |            |
| iff        | `↔` `⇔` `≡`  | `<->`     |            |
| definition | `≡` `≔` `:⇔` | `:=`      |            |
| not        | `¬` (pre)    | `~` (pre) | `'` (post) |
| and        | `∧` `∩` `•`  | `*` `.`   | `&`        |
| or         | `∨` `∪` `+`  | `+`       | `|`        |
| xor        | `⊕` `⊻`      |           | `^`        |

Laws
----

### Basic Principles ###

```text
X + 0 = X
X + 1 = 1
X • 1 = X
X • 0 = 0
```

### Idempotent Law ###

```text
X + X = X
X • X = X
```

### Involution law ###

```text
(X')' = X
```

### Law of complementarity ###

```text
X + X' = 1
X • X' = 0
```

### Commutative law ###

```text
X + Y = Y + X
X • Y = Y • X
```

### Associative law ###

```text
(X + Y) + Z = X + (Y + Z) = X + Y + Z
(XY)Z = X(YZ) = XYZ
```

### Distributive law ###

```text
X(Y + Z) = XY + XZ
X + YZ = (X + Y)(X + Z)
```

### De Morgan's law ###

```text
(X + Y + Z +…)' = X'Y'Z'…
(XYZ…)' = X' + Y' + Z' +…
[f( X,X,…X,0,1,+,•)]' = f( X',X', … X', 1, 0, •,+)
```

### Nonmonotone laws ###

```text
X ∧ X' = 0
X ∨ X' = 1
```

### Duality ###

```text
(X + Y + Z +…)D = XYZ…
(XYZ…)D = X + Y + Z +…
[f(X1,X2,…XN,0,1,+,•)]D = f(X1,X2,…XN,1,0,•,+)
```

### Theorem for multiplying out and factoring ###

```text
(X + Y)(X' + Z) = XZ + X'Y
XY + X'Z  = (X + Z)(X' + Y)
```

### Consensus theorem ###

```text
XY + YZ + X'Z = XY + X'Z
(X + Y)(Y + Z)(X' + Z) = (X + Y)(X' + Z)
```

### Simplification Theorems ###

```text
XY + XY'= X
(X + Y)(X + Y') = X
X + XY = X
X(X + Y) = X
(X + Y')Y = XY
XY'+ Y = X + Y
```

Sources
-------

Based on [duckduckgo's boolean algebra cheat sheet](github.com/duckduckgo/zeroclickinfo-goodies/share/goodie/cheat_sheets/json/boolean-algebra.json)
itself sourced from [wikipedia](https://en.wikipedia.org/wiki/Boolean_algebra)