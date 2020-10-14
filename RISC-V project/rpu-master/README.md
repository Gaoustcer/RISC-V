# Real-Time Processing Unit (RPU) Implementation

## First Step : Environment Setup

### ISA

We design our `RPU` based on `RISC-V` ISA, which is a free and open ISA.

Links you may want.
* [RISC-V Website](https://riscv.org/)

### Core

We use `CV32E40P` as our `RISC-V Core` (or `RISC-V CPU`). `CV32E40P` is 
formerly `RI5CY` written with `SystemVerilog` provided by `PULP`, or `PULP Platform`, which provides a
series of `RISC-V` cores and SoCs. `PULPino` is one of its SoCs supporting
`RI5CY`.

Links you may want.
* [PULP Website](https://pulp-platform.org/)
* [PULPino GitHub](https://github.com/pulp-platform/pulpino)
* [CV32E40P GitHub](https://github.com/openhwgroup/cv32e40p)

### TO-DO

#### Documents about RI5CY
* `docs/figures`: the figures is drawed ib the `draw.io` website.
You may use it to draw your figures in the future.
* `docs/riscv术语.docx`: this document describe some phrase we often use
when we talk about RISC-V.
* `docs/Andreas Traber - pulpino.pdf`: this slides is written by PULP.
You can get some ideas from its design.
* `docs/Pulp RI5CY IF段代码详解.docx`: this document gives a detailed
description about RI5CY IF's code.
* `docs/interrupt`: this folder is some description about RI5CY's 
interrupt written by two PB17 students, and you should check its correctness.
* `docs/RI5CY Rewrite`: this folder contains document about how to crop
a mini RI5CY only contains RISC-V32I ISA, and you may get some infomation
about how to simulate RI5CY using Vivado.

#### Tasks

Later