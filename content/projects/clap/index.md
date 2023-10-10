+++
title = "clap"
description = "Command line argument parser."
draft = false
+++

**A lightweight Command Line Argument Parser library using C++20.**

## Source

https://github.com/karnkaul/clap

## Features

Options are set up by passing a binding reference and the relevant metadata. Bindings are set as options are encountered during parsing. Positional arguments are supported.

```cpp
struct {
  bool debug{};
  int log_level{3};

  struct {
    std::string field{"name"};
    bool enabled{};
  } sort{};

} input{};

options
  // bind an option that's a boolean flag
  .flag(input.debug, "d,debug", "enable debugging")
  // bind an option that requires an int argument
  .required(input.log_level, "log-level", "set the log level", "3")
  // bind an option that takes an optional string argument
  .optional(input.sort.field, input.sort.enabled, "s,sort",
            "sort by", "name|date");

auto result = options.parse(argc, argv);

if (clap::should_quit(result)) { 
  return clap::return_code(result);
}
```