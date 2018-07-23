Project 1: Elementary Logic Gates
=================================

Chip Implementations
--------------------

| Chip      | Components            | Total Nand    |
|-----------|-----------------------|---------------|
| Not       | 1 Nand                | 1             |
| And       | 1 Nand; 1 Not         | 2             |
| Or        | 1 Nand; 2 Not         | 3             |
| Xor       | 1 Nand; 1 Or; 2 And   | 6             |
| Mux       | 1 Not; 2 And; 1 Or    | 8             |
| DMux      | 1 Not; 1 Nand; 1 And  | 4             |
| Not16     | 16 Not                | 16            |
| And16     | 16 And                | 32            |
| Or16      | 16 Or                 | 48            |
| Mux16     | 16 Mux                | 128           |
| Or8Way    | 7 Or                  | 21            |
| Mux4Way16 | 3 Mux16               | 384           |
| Mux8Way16 | 2 Mux4Way16, 1 Mux16  | 896           |
| DMux4Way  | 3 DMux                | 12            |
| DMux8Way  | 2 DMux4Way, 1 Dmux    | 28            |

Helper Chips
------------

| Chip      | Components            | Total Nand    |
|-----------|-----------------------|---------------|
| Nor       | 1 Or; 1 Not           | 4             |