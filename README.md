# 🖥️ NAND2Tetris — From NAND Gates to Tetris

> *"What I cannot create, I do not understand."* 

Built a complete computer from a single NAND gate up to a functioning CPU, memory system, and OS —
covering the full hardware-software stack. Built while following the incredible work of Noam Nisan and Shimon Schocken, the creators of the **Nand to Tetris** course (also known as *The Elements of Computing Systems*). This course is a masterpiece of computer science education.

[Coursera - Build a Modern Computer from First Principles: Nand to Tetris](https://www.coursera.org/learn/build-a-computer)

[Book - The Elements of Computing Systems: Building a Modern Computer from First Principles](https://www.amazon.com/Elements-Computing-Systems-Building-Principles/dp/0262640686)
---

## 📁 Project Structure

```
nand2tetris/
│
├── tools/                           # Official Nand2Tetris software suite (included for convenience)
│   ├── HardwareSimulator.bat/sh     # Simulate and test HDL chip designs
│   ├── CPUEmulator.bat/sh           # Run Hack machine-language programs
│   ├── VMEmulator.bat/sh            # Run VM bytecode files
│   ├── Assembler.bat/sh             # Translate .asm → .hack binary
│   ├── JackCompiler.bat/sh          # Compile Jack source code
│   ├── TextComparer.bat/sh          # Compare output files during testing
│   ├── bin/                         # Java binaries powering all the tools
│   ├── builtInChips/                # Pre-built chip definitions used by the simulator
│   ├── builtInVMCode/               # Pre-built VM code for the OS libraries
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
    ├── Week6_Assembler/             # Hack assembler (translates .asm → .hack)
    ├── Week7_Virtual_Machine_I_Stack_arithmetic/   # VM translator — stack ops
    ├── Week8_Virtual_Machine_II_Program_control/   # VM translator — branching & functions
    ├── Week9_High_Level_Language/   # Jack language programs
    ├── Week10_Compiler_I_Syntax_analysis/          # Jack tokenizer & parser
    ├── Week11_Compiler_II_Code_generation/         # Full Jack compiler
    └── Week12_Operating_System/     # Jack OS standard library
```

---

## 🗺️ Course Roadmap
![Courseimage](https://miro.medium.com/max/1400/1*MAeq1jz7XNpWQeJIx7U72Q.png)

| Week | Topic | Key Deliverable |
|------|-------|----------------|
| 1 | Boolean Logic | AND, OR, NOT, MUX, DMUX, … 15 gates |
| 2 | Boolean Arithmetic | Half-adder, Full-adder, ALU |
| 3 | Sequential Logic | Bit, Register, RAM8 → RAM16K, PC |
| 4 | Machine Language | Fill.asm, Mult.asm |
| 5 | Computer Architecture | CPU.hdl, Memory.hdl, Computer.hdl |
| 6 | Assembler | Assembler in a language of your choice |
| 7 | VM I — Stack Arithmetic | VM translator (arithmetic + memory segments) |
| 8 | VM II — Program Control | VM translator (branching + function calls) |
| 9 | High-Level Language | A Jack program of your own |
| 10 | Compiler I — Syntax Analysis | Tokenizer + Parser |
| 11 | Compiler II — Code Generation | Full Jack → VM compiler |
| 12 | Operating System | Jack OS (Math, Screen, Keyboard, …) |


---

### 🧩Project Details

The project is split into two major parts that build on each other:

**Part 1 — Hardware (`Hack_Hardware_Platform/`, Weeks 1–5)**
I design chips using a simple Hardware Description Language (HDL). Starting from a single primitive NAND gate, I build progressively more complex components — logic gates, an Arithmetic Logic Unit (ALU), memory chips, and finally a fully working 16-bit computer called the **Hack computer**. Nothing is "given" to you; every chip is built on top of the previous one.

**Part 2 — Software (`Software_Hierarchy/`, Weeks 6–12)**
I write software that targets the Hack hardware I built. This includes an assembler that translates symbolic assembly code into binary, a virtual machine translator, a compiler for a high-level language called **Jack** (similar to Java), and finally a minimal operating system. By the end, the entire stack — from transistors to Tetris — is something I built yourself.

---

### ⚙️ Hardware Projects — Weeks 1–5

Each week's folder contains `.hdl` files (chip implementations) and `.tst`/`.cmp` files (test scripts and expected outputs provided by the course).

**The workflow for every hardware project:**

 **Read the project spec** — Each week has a PDF specification on the [course website](https://www.nand2tetris.org/course) that describes exactly which chips to build, their truth tables, and the HDL interface.

**What each week builds:**

- **Week 1 — Boolean Logic:** I implement 15 fundamental chips — NOT, AND, OR, XOR, MUX, DMUX, and their multi-bit/multi-way variants — all derived from a single NAND primitive.
- **Week 2 — Boolean Arithmetic:** I build adder chips and the 16-bit **Arithmetic Logic Unit (ALU)**, the heart of any CPU. The ALU can compute 18 different functions on two 16-bit inputs.
- **Week 3 — Sequential Logic:** Using a built-in D flip-flop, I build memory — from a single 1-bit register all the way up to a 16K-word RAM chip — plus the **Program Counter**, which drives instruction sequencing.
- **Week 4 — Machine Language:** I write programs directly in the **Hack assembly language**. This week is about understanding how the machine "thinks" before you build it. Programs include a multiplication routine and a screen-filling graphics demo.
- **Week 5 — Computer Architecture:** I assemble all previous chips into the complete **Hack computer** — a CPU, a memory unit (combining RAM and screen/keyboard I/O), and a top-level `Computer.hdl` chip that ties everything together.

---

### 💾 Software Projects — Weeks 6–12

The software half of the course is implemented in a general-purpose programming language of student choice **(I choose Python)**. Each project produces a tool that translates one layer of abstraction into the next.

**What each week builds:**

- **Week 6 — Assembler:** Translates symbolic Hack assembly (`.asm`) into binary machine code (`.hack`). Handles symbols, labels, and predefined registers. This is your first "real" language tool.
- **Week 7 & 8 — VM Translator:** Translates a stack-based intermediate bytecode (`.vm` files, similar to Java bytecode) into Hack assembly. Week 7 covers arithmetic and memory access commands; Week 8 adds branching, function calls, and the call stack.
- **Week 9 — High-Level Language:** A creative week — I write any program you like in **Jack**, a simple object-based language. This gives me a feel for the language before you build the compiler that processes it.
- **Week 10 — Compiler I (Syntax Analysis):** Built a tokenizer (lexer) and a recursive-descent parser for Jack. The parser outputs an XML parse tree that makes the program's grammatical structure explicit.
- **Week 11 — Compiler II (Code Generation):** Extend the parser into a full compiler, generating `.vm` bytecode from Jack source. This involves a symbol table for variable scoping and code generation for expressions, statements, objects, and arrays.
- **Week 12 — Operating System:** Implement the Jack OS standard library in Jack itself — 8 classes covering math (multiply, divide, square root), memory management (heap allocator), screen drawing, keyboard input, and string/output handling.

**The translation chain, end to end:**

```
Jack source (.jack)
      ↓  [Week 10–11: Compiler]
VM bytecode (.vm)
      ↓  [Week 7–8: VM Translator]
Hack assembly (.asm)
      ↓  [Week 6: Assembler]
Binary machine code (.hack)
      ↓  [Week 5: Hack Computer]
Runs on the hardware you built
```

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

## 🧠 Key Concepts Covered

- **Boolean Algebra** and gate-level design
- **Combinational vs. Sequential** circuits
- **Von Neumann Architecture** — CPU, memory, and I/O
- **Assembly Language** and machine code
- **Stack-based Virtual Machines**
- **Recursive Descent Parsing** and symbol tables
- **Code Generation** and memory management
- **Operating System** services and abstraction layers

---
