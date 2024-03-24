# How rust handles match statement comparing strings

I naively assumed that match statement is some kind of magical thing that compiles rust code into something magically efficient, until I realized that hashmap can be faster.

Take a look at an example below. 
`match` statement is a lot slower compared to hashmap.

# Taking a look at the generated assembly
This is the control flow graph of the assembly code that rust generated.
Compared to the c-code you can tell that it is looks quite different.

So, how are they different?
1. 

How can we improve this?
1. Rust can jump to the next match arm as soon as that comparision yields negative.
2. 
