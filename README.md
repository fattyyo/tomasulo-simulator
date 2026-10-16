# Tomasulo Out-of-Order Pipeline Simulator

A cycle-by-cycle C++ simulator of **Tomasulo's algorithm**, written for a Computer Organization course (Spring 2022).

## What it models
- **5 reservation stations** feeding two functional units: ADD/SUB (also `ADDI`) and MUL/DIV
- **Register Alias Table (RAT)** for register renaming over registers F1–F5
- **Issue → Execute → Write-back** with per-operation latencies: ADD/SUB 2 cycles, MUL 10, DIV 40
- **Result broadcast**: when a unit finishes, its value is forwarded to every reservation station waiting on it and the RAT entry is cleared
- RAW hazards are resolved by waiting on tags, and WAR / WAW hazards by renaming

## Run
```bash
g++ -std=c++17 -o tomasulo 1093343prog3.cpp
./tomasulo < input.txt
```
The program prints the register file, RAT, and reservation-station contents as the simulation advances.
