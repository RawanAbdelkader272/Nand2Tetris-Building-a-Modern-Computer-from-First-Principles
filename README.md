# NAND2Tetris — Building a Modern Computer from First Principles

> *"What I cannot create, I do not understand."* 

A complete computer built from scratch — starting from a single NAND gate and ending with a functioning CPU, memory system, assembler, compiler, and operating system. This project follows the **Nand to Tetris** course by Noam Nisan and Shimon Schocken (*The Elements of Computing Systems*), one of the finest computer science courses ever made.

**Courses:** [Part I — Hardware](https://www.coursera.org/learn/build-a-computer) · [Part II — Software](https://www.coursera.org/learn/nand2tetris2)  
**Book:** [The Elements of Computing Systems](https://mitpress.mit.edu/9780262539807/the-elements-of-computing-systems/)

---

## Project Structure

```
nand2tetris/
│
├── tools/                           # Official Nand2Tetris software suite
│   ├── HardwareSimulator.bat/sh     # Simulate and test HDL chip designs
│   ├── CPUEmulator.bat/sh           # Run Hack machine-language programs
│   ├── VMEmulator.bat/sh            # Run VM bytecode files
│   ├── Assembler.bat/sh             # Translate .asm → .hack binary
│   ├── JackCompiler.bat/sh          # Compile Jack source code
│   └── OS/                         # Jack OS source files
│
├── Hack_Hardware_Platform/          # Hardware projects (Weeks 1–5)
│   ├── Week1_Boolean_Logic/         # Elementary logic gates from NAND
│   ├── Week2_Boolean_Arithmetic/    # ALU and arithmetic chips
│   ├── Week3_Sequential_Logic/      # Registers, RAM, and the Program Counter
│   ├── Week4_Machine_Language/      # Hack assembly programming
│   └── Week5_Computer_Architecture/ # The Hack computer (CPU + Memory + ROM)
│
└── Software_Hierarchy/              # Software projects (Weeks 6–12)
    ├── Week6_Assembler/             # Hack assembler (.asm → .hack)
    ├── Week7_VM_I_Stack_Arithmetic/ # VM translator — stack ops
    ├── Week8_VM_II_Program_Control/ # VM translator — branching & functions
    ├── Week9_High_Level_Language/   # Jack language programs
    ├── Week10_Compiler_I_Syntax/    # Jack tokenizer & parser
    ├── Week11_Compiler_II_Codegen/  # Full Jack compiler
    └── Week12_Operating_System/     # Jack OS standard library
```

---

## Course Roadmap

![Course overview](https://miro.medium.com/max/1400/1*MAeq1jz7XNpWQeJIx7U72Q.png)

| Week | Topic | Key Deliverable |
|------|-------|-----------------|
| 1 | Boolean Logic | NOT, AND, OR, XOR, MUX, DMUX — 15 gates total |
| 2 | Boolean Arithmetic | Half-adder, Full-adder, 16-bit ALU |
| 3 | Sequential Logic | Bit, Register, RAM8 → RAM16K, Program Counter |
| 4 | Machine Language | `Mult.asm`, `Fill.asm` |
| 5 | Computer Architecture | `CPU.hdl`, `Memory.hdl`, `Computer.hdl` |
| 6 | Assembler | Python assembler: symbols, labels, predefined registers |
| 7 | VM I — Stack Arithmetic | VM translator: arithmetic + memory segments |
| 8 | VM II — Program Control | VM translator: branching + function calls |
| 9 | High-Level Language | An original program written in Jack |
| 10 | Compiler I — Syntax Analysis | Tokenizer + recursive-descent parser |
| 11 | Compiler II — Code Generation | Full Jack → VM compiler with symbol tables |
| 12 | Operating System | Jack OS: math, memory, screen, keyboard, strings |

---

## The Full Stack

Everything connects. Here is the complete translation chain from source code down to hardware:

```
Jack source (.jack)
      ↓  Weeks 10–11 — Compiler
VM bytecode (.vm)
      ↓  Weeks 7–8  — VM Translator
Hack assembly (.asm)
      ↓  Week 6     — Assembler
Binary machine code (.hack)
      ↓  Week 5     — Hack Computer (built in HDL)
Runs on hardware you designed from NAND gates
```

---

## Part 1 — Hardware (Weeks 1–5)

Chips are implemented in a simple Hardware Description Language (HDL) and tested using the course's hardware simulator. Every chip is built on top of the previous one — nothing is given for free.

**Week 1 — Boolean Logic:** 15 fundamental gates (NOT, AND, OR, XOR, MUX, DMUX, and their multi-bit/multi-way variants), all derived from a single NAND primitive.

**Week 2 — Boolean Arithmetic:** Adder chips and the 16-bit **ALU** — the heart of the CPU. The ALU computes 18 different functions on two 16-bit inputs, controlled by six flag bits.

**Week 3 — Sequential Logic:** Using a built-in D flip-flop as the only primitive, I build memory from a single 1-bit register up to a 16K-word RAM, plus the **Program Counter** that drives instruction sequencing.

**Week 4 — Machine Language:** Assembly programming on the Hack platform before building the hardware that runs it. Programs include a multiplication routine and a screen-filling graphics demo.

**Week 5 — Computer Architecture:** All previous chips assembled into the complete **Hack computer** — a CPU, a unified memory unit (RAM + screen/keyboard I/O), and a top-level `Computer.hdl` that ties everything together.

---

## Part 2 — Software (Weeks 6–12)

The software stack is implemented in **Python**. Each project produces a tool that translates one layer of abstraction into the next.

**Week 6 — Assembler:** Translates symbolic Hack assembly (`.asm`) into binary machine code (`.hack`). Handles symbols, labels, and predefined registers.

**Weeks 7 & 8 — VM Translator:** Translates stack-based VM bytecode (`.vm`) into Hack assembly. Week 7 handles arithmetic and memory access; Week 8 adds branching, function calls, and the full call stack.

**Week 9 — High-Level Language:** A creative week — write any program in **Jack**, a simple object-based language similar to Java, before building the compiler that processes it.

**Week 10 — Compiler I (Syntax Analysis):** A tokenizer (lexer) and recursive-descent parser for Jack. The parser outputs an XML parse tree that makes the program's grammatical structure explicit.

**Week 11 — Compiler II (Code Generation):** The parser extended into a full compiler, generating `.vm` bytecode from Jack source. Covers symbol tables, variable scoping, expression evaluation, objects, and arrays.

**Week 12 — Operating System:** The Jack OS standard library implemented in Jack itself — 8 classes covering integer math (multiply, divide, square root), heap memory management, screen drawing, keyboard input, and string handling.

---

## Running the Projects

All tools are in the `tools/` directory. On macOS/Linux use the `.sh` scripts; on Windows use `.bat`.

```bash
# Test a hardware chip
./tools/HardwareSimulator.sh

# Run a compiled .hack program
./tools/CPUEmulator.sh

# Translate .asm → .hack
./tools/Assembler.sh path/to/program.asm

# Run VM bytecode
./tools/VMEmulator.sh

# Compile Jack source
./tools/JackCompiler.sh path/to/MyProgram/
```

For the Python software projects (Weeks 6–12), each week's folder contains a runnable script. Example:

```bash
# Week 6 — Assembler
python3 Week6_Assembler/assembler.py path/to/program.asm

# Week 7/8 — VM Translator
python3 Week7_VM_I/vm_translator.py path/to/program.vm
```

---

## Key Concepts Covered

- **Boolean algebra** and gate-level design
- **Combinational vs. sequential** circuits
- **Von Neumann architecture** — CPU, memory, and I/O
- **Assembly language** and machine code
- **Stack-based virtual machines**
- **Recursive-descent parsing** and symbol tables
- **Code generation** and memory management
- **Operating system** services and abstraction layers

---
---

## 📚 Resources

- 🌐 [Nand2Tetris Official Website](https://www.nand2tetris.org/) — course materials, software, and project specs
- 📖 [The Elements of Computing Systems (Book)](https://mitpress.mit.edu/9780262539807/the-elements-of-computing-systems/) — the companion textbook by Noam Nisan & Shimon Schocken
- 🎓 [Coursera — Part I (Hardware)](https://www.coursera.org/learn/build-a-computer) — Boolean Logic → Computer Architecture
- 🎓 [Coursera — Part II (Software)](https://www.coursera.org/learn/nand2tetris2) — Assembler → Operating System

### HDL & Tools Reference

- 📄 [HDL Survival Guide](https://www.nand2tetris.org/software) — tips for writing HDL files
- 📄 [Hack Assembly Language Reference](https://www.nand2tetris.org/project04) — full instruction set reference
- 📄 [Jack Language Specification](https://www.nand2tetris.org/project09) — syntax and semantics guide

---
## Resources

| Resource | Link |
|----------|------|
| Official website | [nand2tetris.org](https://www.nand2tetris.org/) |
| Companion textbook | [The Elements of Computing Systems](https://mitpress.mit.edu/9780262539807/) |
| Coursera Part I | [Build a Modern Computer — Hardware](https://www.coursera.org/learn/build-a-computer) |
| Coursera Part II | [Build a Modern Computer — Software](https://www.coursera.org/learn/nand2tetris2) |
| HDL Survival Guide | [nand2tetris.org/software](https://www.nand2tetris.org/software) |
| Hack Assembly Reference | [nand2tetris.org/project04](https://www.nand2tetris.org/project04) |
| Jack Language Spec | [nand2tetris.org/project09](https://www.nand2tetris.org/project09) |
