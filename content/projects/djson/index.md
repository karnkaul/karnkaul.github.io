+++
title = "djson"
description = "JSON input / output library."
tags = ["parsing"]
weight = 10
draft = false
+++

**A lightweight JSON parser library using C++20.**

## Source

https://github.com/karnkaul/djson

## Features

- First-in/first-out object maps
- Fast conversion of strings to numbers using `std::from_chars`
- Copiable `Json` objects
- Proxy containers for array/object iteration
- `std::string_view` interface to minimize redundant `std::string` copies
- Heterogenous arrays
- Escaped text (`\\`, `\"`, `\b`, `\t`, `\n`)
- Implicit construction for nulls, booleans, numbers, strings
- Serialization, pretty-print (default)
- Customization points for `from_json` and `to_json`
- Build tree from scratch
