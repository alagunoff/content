---
title: Wrap
slug: WebAssembly/Reference/Numeric/Wrap
page-type: webassembly-instruction
sidebar: webassemblysidebar
---

The **`wrap`** instruction, is used to convert numbers of type `i64` to type `i32`. If the number is larger than what an `i32` can hold this operation will wrap, resulting in a different number.

One can think of wrap either as reducing the value [mod](https://en.wikipedia.org/wiki/Modular_arithmetic) 2<sup>32</sup>, or as discarding the high 32 bits to produce a value containing just the low 32 bits.

{{InteractiveExample("Wat Demo: wrap", "tabbed-taller")}}

```wat interactive-example
(module
  (import "console" "log" (func $log (param i32)))
  (func $main

    i64.const 10 ;; push an i64 onto the stack

    i32.wrap_i64 ;; wrap from i64 to i32

    call $log ;; log the result
  )
  (start $main)
)
```

```js interactive-example
const url = "{%wasm-url%}";
await WebAssembly.instantiateStreaming(fetch(url), { console });
```

## Syntax

```wat
;; push an i64 onto the stack
i64.const 10

;; wrap from i64 to i32
i32.wrap_i64

;; the top item on the stack will now be the value 10 of type `i32`
```

| Instruction    | Binary opcode |
| -------------- | ------------- |
| `i32.wrap_i64` | `0xa7`        |
