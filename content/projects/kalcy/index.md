+++
title = "kalcy"
description = "Arithmetic expression evaluator library, REPL demo."
tags = ["parsing"]
weight = 10
draft = false
+++

```
./kalcy-quickstart
usage: ./kalcy-quickstart [-v] "<expression>"

./kalcy-quickstart 42
42

./kalcy-quickstart -v "1 + 2 * 3 ^ 2"
19
expression      : 1 + 2 * 3 ^ 2
AST             : (1 + (2 * (3 ^ 2)))

./kalcy-quickstart -v "-2.5 * sqrt(pi)"
-4.43113
expression      : -2.5 * sqrt(pi)
AST             : (-2.5 * sqrt(pi))
```

## Source

https://github.com/cpp-gamedev/kalcy

## Features

- Static library.
- Recursive descent parsing.
- Closed-set polymorphism of expression types (using `std::variant`).
- Support for a "read-only" execution environment (constants and pure functions).
