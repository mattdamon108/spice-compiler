# Spice compiler

Tiny compiler consists of Lexer, Parser, Type checker written in OCaml.

The type inference implemetation is mostly from the sound_lazy in https://okmij.org/ftp/ML/generalization.html and modified for the purpose of typing the parsetree (AST) from the parser.

## Example

Source

```ocaml
let x = fun y -> y + 1 in
(x 1)
```

The typed tree

```
Program
└──Expr: Let var: x: Tconstr_integer
   └──Expr: Lambda: y: TArrow: Tconstr_integer -> Tconstr_integer
      └──Expr: Bin Op: +: Tconstr_integer
         └──Expr: Var: y: Tconstr_integer
         └──Expr: Int:1
   └──Expr: App: Tconstr_integer
      └──Expr: Var: x: TArrow: Tconstr_integer -> Tconstr_integer
      └──Expr: Int:1
```
