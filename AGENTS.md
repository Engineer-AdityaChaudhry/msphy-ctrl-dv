# AGENTS.md

## Project

This repository is `msphy-ctrl-dv`: an open-source digital verification project for an APB-based mixed-signal PHY controller.

The project models the digital control logic around mixed-signal PHY IP used in SerDes/DDR/PLL-style systems.

## Goal

Build a clean, educational, synthesizable SystemVerilog RTL design and an open-source verification environment using Verilator, cocotb, pyuvm-style structure, assertions, coverage planning, and regression automation.

## Role Alignment

This project is designed to showcase skills relevant to a Mixed-Signal Design Verification Engineer role:
- APB/SoC IP register interface
- PLL lock sequencing
- calibration sequencing
- lane bring-up
- low-power entry/exit
- interrupts and sticky status bits
- assertions
- functional coverage
- constrained-random verification
- regression automation
- RTL/debug documentation

## Coding Rules

- Use SystemVerilog for RTL.
- Keep RTL synthesizable unless the file is clearly in `models/` or `dv/`.
- Do not create overly complex designs.
- Prefer clarity over cleverness.
- Use active-low reset named `presetn`.
- Use APB naming: `pclk`, `presetn`, `psel`, `penable`, `pwrite`, `paddr`, `pwdata`, `prdata`, `pready`, `pslverr`.
- Use 32-bit data width and 12-bit address width by default.
- Add comments explaining design intent.
- Keep each module focused and small.
- Do not silently remove files.
- Update documentation when changing behavior.

## Verification Rules

- Use cocotb for tests.
- Prefer simple reusable APB read/write helper functions first.
- Add pyuvm-style structure later.
- Every feature should have a directed test before random testing.
- Tests should be runnable with `make test`.
- Waveform generation should be optional.
- Do not fake passing tests.
- If a tool cannot run, document the limitation clearly.

## First Milestone

Implement only Milestone 1:
- APB register access
- `PLL_CTRL`
- `PLL_STATUS`
- `pll_enable` output
- external `pll_lock` input
- basic cocotb test proving APB write/read works

Do not implement calibration, lane, low-power, interrupts, formal, or coverage yet.
