# Numerical Coding

A simple python program for encoding and decoding register machine programs (using Goedel Numberings) I made for the second year course Models of Computation at Imperial College London.
### Summray
- Pairs
- Lists
- Register Machine Programs

### The Encoding

There are 2 ways of coding pairs:
- `⟨⟨ x, y ⟩⟩ = 2 ** x  * (2 * y + 1)`
the result in binary would be: y in binary | 1 | x zeros
- `⟨ x, y  ⟩ = 2 ** x * (2 * y + 1) - 1`
where the result is: y in binary | 0 | x ones

With this in mind, we can move onto encoding lists. Let l be a list and enc(l) denote the encoded list. 
- a list ` (x : l)` is encoded as: `⟨⟨ x, enc(l) ⟩⟩`
- and the empty list `[]` as:
`enc([]) = 0`

Register machine instructions
- There are three types of register machine instructions:
1. Rx (+) -> Ry
2. Ri (-) -> Rj, Rk
3. HALT

They are encoded as follows:
1. `⟨⟨ x, y ⟩⟩`
2. `⟨⟨ i, ⟨ j, k ⟩ ⟩⟩`
3. `0`
    
- To encode a register machine R with instructions I1 ... In:
`enc(R) = enc( [ enc(I1), ..., enc(In) ]`
