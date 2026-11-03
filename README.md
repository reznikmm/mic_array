Mic_Array
========

[![Build with Alire](https://github.com/reznikmm/mic_array/actions/workflows/alire.yml/badge.svg)](https://github.com/reznikmm/mic_array/actions/workflows/alire.yml)
[![REUSE status](https://api.reuse.software/badge/github.com/reznikmm/mic_array)](https://api.reuse.software/info/github.com/reznikmm/mic_array)

Ada project mic_array packaged as an Alire crate.

## Hardware

* 4 INMP411
* WiFi MCU: EMW3165 (STM32F411 with BCM43362 onboard)

### Available WiFi MCU pins:

* PA: 0-5, 7, 10-15
* PB: 0-4, 6, 8-10, 12, 13
* PC: 13

### I2S busses

* CK(4) PB13 D12 PIN 10
* WS(4) PB12 D4  PIN 13
* CK(4) PA4  D17 PIN 3

* CK(5) PB0  D16 PIN 4
* WS(5) PB1  D15 PIN 7
* SD(5) PA10 D8  PIN 14

```
    SD   WS   CK
1   PA7  PA5  PA4
         ^^^  ^^^
4   PA1  PB12 PB13
    ^^^  ^^^^ ^^^^
5   PA10 PB1  PB0
    ^^^^ ^^^  ^^^

PA1: SD (4)    +++++
PA4: WS (1,3)  +++++
PA5: CK (1)    +++++
PA7: SD (1)     ------
PA10: SD (5)   +++++
PA15: WS (1,3)  ------
PB0: CK (5)     ++++++
PB1: WS (5)     +++++
PB3: CK (1,3)   ------
pb5: SD (1,3) - N/A
PB8: SD (5)     +++++
PB9: WS (2)     +++++
PB10: CK (2)    +++++
PB12: WS (2,4)  +++++
PB13: CK (2,4)  +++++
```

Key directories and files:

- `source/` - library units (`Mic_Array` package)
- `mic_array.gpr` - root GPR project file for the library
- `alire.toml` - root crate metadata and test action
- `testsuite/` - separate Alire crate for tests
- `AGENTS.md` - repository-specific instructions for coding agents

## Requirements

- [Alire](https://alire.ada.dev/)
- GNAT toolchain compatible with Ada 2022

## Build And Test

From repository root:

```sh
alr build
```

<!---
Run testsuite crate directly:

```sh
alr -C testsuite run
```
--->

## Using This Mic_Array

1. Create a new repository from this mic_array.
2. Run `./rename.sh <your_project_name>` to rename `mic_array`/`Mic_Array`/`MIC_ARRAY` identifiers.
3. Adjust crate metadata in `alire.toml`.
4. Replace `source/mic_array.ads` with your actual library units.

Use `./rename.sh --dry-run <your_project_name>` to preview changes.

## Maintainer

[Max Reznik](https://github.com/reznikmm)

## License

Licensed under Apache-2.0 WITH LLVM-exception. See `LICENSES/` and `REUSE.toml`.

