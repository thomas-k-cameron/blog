# How rust handles match statement comparing strings

I naively assumed that match statement is some kind of magical thing that compiles rust code into something magically efficient, until I realized that hashmap can be faster.

I present you few trivial examples to understand how Rust's assembly code 
Take a look at an example below. 
`match` statement is a lot slower compared to hashmap.

## 

```
cmp     dword ptr [rdi], 829256289
```
MOV instruction puts a piece of data onto CPU's register, data usually comes from RAM or register. It could be cached in a CPU cache.

Rust's assembly loads string to register everytime it compares the string against the match arm, while 

## 

1. Rust will always use `MOV` instruction to load every byte of the string to compare against the match arms.
2. C will only compare byte 

How can we improve this?
1. Rust can jump to the next match arm as soon as that comparision yields negative.
2. 
