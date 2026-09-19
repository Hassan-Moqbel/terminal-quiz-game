# Interactive Terminal Quiz Game (C/C++)

![C / C++](https://img.shields.io/badge/Language-C_%2F_C%2B%2B-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![Compiler](https://img.shields.io/badge/Compiler-GCC_%2F_MinGW-A8B9CC?style=for-the-badge)
![CLI Application](https://img.shields.io/badge/Platform-CLI_Application-4B0082?style=for-the-badge)
![Structured Programming](https://img.shields.io/badge/Methodology-Structured_Programming-28A745?style=for-the-badge)
![Memory Safety](https://img.shields.io/badge/Security-Memory_Safety-FF6F00?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

## Executive Overview
Terminal-based applications require highly robust console I/O handling to prevent undefined behavior and catastrophic segmentation faults. This project represents a foundational interactive **Quiz Game** developed natively in **C/C++**. It demonstrates procedural structured programming, control flow logic, state persistence via runtime accumulators, and input sanitization necessary for stable Command Line Interface (CLI) user experiences.

> [!CAUTION]
> **Software Reliability & Memory Safety Callout**
> Capturing input directly from standard input streams (`stdin`) is notoriously volatile. Using legacy unbounded functions like `scanf("%s")` exposes the application to lethal **buffer overflow vulnerabilities** if the user inputs a string larger than the allocated array. Safe C/C++ architecture mandates the use of bounded input functions (like `fgets()`), manual flushing of newline characters in the input buffer, and strict bounds-checking before executing array lookups to ensure deterministic memory allocation.

## System Highlights
- **Interactive Evaluation Engine**: Dynamically renders questions, parses input, and returns real-time feedback.
- **Structured Data Representation**: Groups questions, options, and answers using parallel arrays or foundational `struct` paradigms.
- **Input Validation & Sanitization**: Employs boundary logic to aggressively reject out-of-range user inputs without crashing the main event loop.
- **Performance Metrics**: Accumulates real-time scores and executes final percentage calculations for end-of-game grading.

## Software Architecture Flowchart

mermaid
flowchart TD
    START(["Application Entry: main()"]) --> INIT["Question Bank Initialization"]
    
    INIT --> LOOP_RENDER["Loop: Render Question & Options"]
    LOOP_RENDER --> INPUT["Capture User Input Stream"]
    
    INPUT --> VALIDATE{"Input Validation \n& Sanitization"}
    VALIDATE -->|Invalid| INPUT
    VALIDATE -->|Valid| EVAL{"Conditional Branch: \nCorrect / Incorrect?"}
    
    EVAL -->|Correct| UPDATE_SCORE["Update Score Counter"]
    EVAL -->|Incorrect| SKIP_SCORE["Feedback: Wrong Answer"]
    
    UPDATE_SCORE --> COND
    SKIP_SCORE --> COND
    
    COND{"Loop Condition Met? \nMore Questions?"}
    COND -->|Yes| LOOP_RENDER
    COND -->|No| METRICS["Generate Final Grade Report \n& Performance Metrics"]
    
    METRICS --> EXIT(["Exit 0"])


## Algorithmic & Mathematical Modeling

### 1. Accuracy Evaluation Metric
At the termination of the game loop, the final percentage accuracy ($S$) is calculated using integer/float casted arithmetic:
$$S = \left(\frac{"N_{correct"}}{N_{"total"}}\right) \times 100\%$$

### 2. Algorithmic Complexity
The engine operates predictably across finite sets:
$$\text{"Time Complexity: "} \mathcal{"O"}(N) \quad (\text{"linear traversal across "} N \text{" questions"})$$
$$\text{"Auxiliary Space Complexity: "} \mathcal{"O"}(1) \quad (\text{"static stack-allocated memory footprint"})$$

### 3. State Transition Validation Logic
User input bounds checking is evaluated using strict boolean constraints to filter the character domain:
$$\text{"Input "} c \in \{\text{"'A'"}, \text{"'B'"}, \text{"'C'"}, \text{"'D'"}\} \lor \{\text{"'a'"}, \text{"'b'"}, \text{"'c'"}, \text{"'d'"}\} \implies \text{"Valid"}$$
*(Any character failing this proposition triggers an input loop retry without altering the game state).*

## Build & Compilation Matrix
To compile this project locally on a machine equipped with GCC/MinGW, use the following commands from the project root:

**For Standard C:**
```bash
gcc -O2 src/main.c -o bin/quiz_game.exe
```

**For Standard C++:**
```bash
g++ -O2 "src/PROJECT OF A Quiz Game .cxx" -o bin/quiz_game_cpp.exe
```

## Repository Layout Tree
```text
📦 Quiz Game
 ┣ 📂 src/             # Core C/C++ source code
 ┃ ┣ 📜 main.c
 ┃ ┗ 📜 PROJECT OF A Quiz Game .cxx
 ┣ 📂 docs/            # Engineering documentation & presentations
 ┃ ┣ 📜 Quiz game.pptx
 ┃ ┗ 📜 Tech brochure.pdf
 ┣ 📂 bin/             # Compiled executable binaries (Ignored in Git)
 ┣ 📜 README.md        # This document
 ┣ 📜 LICENSE          # MIT License
 ┗ 📜 .gitignore       # Build artifact exclusions
```

## Authentic Artifacts Catalog
- **Source Code Implementation**: Located in ["`src/`"](src/).
- **Original Project Presentations & Exports**: Securely archived in ["`docs/`"](docs/).

## Engineering Audit & Defensibility
- **Static vs. Dynamic Scalability**: Currently, questions are hardcoded in static arrays within the source files. While highly efficient for $\mathcal{"O"}(1)$ memory constraints on embedded systems, a scalable desktop application should transition to file I/O operations, dynamically parsing `.csv` or `.json` structures into heap-allocated linked lists.
- **Cross-Platform Compatibility**: Formatting terminal output natively via Windows API (`<windows.h>`, `system("cls")`) breaks POSIX compatibility. Abstracting these calls via preprocessor directives (`#ifdef _WIN32`) is recommended to ensure seamless compilation across Linux and macOS environments.

---

**Hassan Moqbel Morshed Ghaleb**
Mechatronics Engineer | Mechanical Design & CAD (SolidWorks & AutoCAD) | Preventive Maintenance & Electromechanical Systems | Industrial Automation, Control Systems, Robotics & Intelligent Machines | CAD/FEA, Embedded Systems, Python & C++
[GitHub](https://github.com/Hassan-Moqbel) · [Facebook](https://www.facebook.com/share/1BqxAgVjHi/) · [LinkedIn](https://www.linkedin.com/in/hassan-moqbel)

## License
This project is licensed under the ["MIT License"](LICENSE).
