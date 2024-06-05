# Error Code System

Each error code is a number in hex.

This number can be represented as binary.

The first 3 bits are for what component caused it.

- `000`: Tokenizer
- `001`: Parser
- `010`: Analyzer
- `011`: Optimizer

The rest are reserved for the compiler backend.

Then there will always be a 1.

the next 12 bits are to encode the line number where the error was called from.

Then there is a 1 byte counter to show what file it was called from. Each file has it's own number that will be at the top of the file in both binary and in decimal.

## example

Here is an example of a error code: 

`302801`

This works out to the binary

`001100000010100000000001`

So we can split that up into:

3 bits: Component: `001` - Parser
1 bit: always a one
12 bits: line number: `000000101000` - 40
8 bits: file number: `00000001` - 1

So then we know that it was an error in the parser on line 40 in the file associated with the pasrer with the id 1.
