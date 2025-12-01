# Human Machine Protocol (HMP)

**Official Website:** [openroko.org](https://www.openroko.org)

---

## 1. Introduction

The Human Machine Protocol (HMP) is a reasoning and execution protocol designed to align humans, machines, and Large Language Models (LLMs) within a structured, deterministic, and secure format. It was created to address two fundamental limitations of LLMs: non-deterministic reasoning that is difficult to verify, and the execution of complex actions without traceability, predictability, or control.

With HMP, AI agents transition from being mere text translators to structured logic processors, following explicit steps defined by macros, tools, and controlled flows. HMP serves as the structured brain behind any intelligent agent.

**Core Characteristics:**

*   **Declarative & Procedural Syntax:** Clear and readable syntax based on natural English.
*   **Deterministic Steps:** Every instruction changes the state in a traceable manner.
*   **Extensible Tools:** A rich set of native and extensible tools for various operations (math, logging, crypto, list manipulation, HTTP, etc.).
*   **Secure Execution:** Isolated context with built-in safety limits.
*   **Transparent Logging:** Structured and transparent logs for "glass-box" execution.
*   **Flow Control:** Support for conditional logic (`IF`), loops (`LOOP`, `WHILE`), and iteration (`FOR EACH`).
*   **Independent Engine:** Runs on a dedicated HMP Engine.

## 2. The Protocol's Nature

HMP is more than a language; it is a **protocol**. Its purpose is to serve as:

*   An internal reasoning language for LLMs.
*   A secure integration layer between humans and machines.
*   A universal system for procedural orchestration.
*   A deterministic representation of thought.

This transforms LLMs into genuine agents that are **predictable**, **auditable**, **secure**, **reusable**, and **scalable**.

## 3. Syntax and Usage

The HMP syntax is designed to be intuitive and powerful, enabling complex logic through simple commands.

### Variables (`SET`)

Used to define variables. Supports strings, numbers, lists, and expressions.

```hmp
# Assign a string
SET name TO "John"

# Assign a number
SET age TO 30

# Assign a list
SET items TO ["apple", "banana", "orange"]

# Use an expression
SET next_age TO ${age + 1}
```

### Tool Calls (`CALL`)

Invokes native HMP tools.

```hmp
# Print a log message
CALL log.print WITH message="Hello, ${name}!"

# Perform a calculation
CALL math.sum WITH a=10, b=5, label="addition_result"

# Access the result
SET result TO ${last_result["addition_result"]}
```

### Conditional Logic (`IF`)

Executes blocks of code based on conditions.

```hmp
IF ${age} >= 18 THEN
    CALL log.print WITH message="User is an adult."
ELSE
    CALL log.print WITH message="User is a minor."
ENDIF
```

### Loops

HMP supports fixed, conditional, and list-based loops.

**Fixed Loop (`LOOP N TIMES`)**

```hmp
LOOP 5 TIMES
    CALL log.print WITH message="Iteration ${loop_index}"
ENDLOOP
```

**Conditional Loop (`WHILE`)**

```hmp
SET counter TO 0
WHILE ${counter} < 5
    CALL log.print WITH message="Counter is ${counter}"
    SET counter TO ${counter + 1}
ENDWHILE
```

**List Iteration (`FOR EACH`)**

```hmp
SET fruits TO ["apple", "banana", "cherry"]
FOR EACH fruit IN ${fruits}
    CALL log.print WITH message="Processing ${fruit}..."
ENDFOR
```

### Parallel Execution (`PARALLEL`)

Executes multiple operations simultaneously for efficiency.

```hmp
PARALLEL
    CALL http.get WITH url="https://api.example.com/data1", label="data1"
    CALL http.get WITH url="https://api.example.com/data2", label="data2"
ENDPARALLEL
```

### Functions (`FUNCTION`)

Defines reusable blocks of code.

```hmp
FUNCTION greet_user(user_name)
    CALL log.print WITH message="Hello, ${user_name}!"
ENDFUNCTION

CALL greet_user WITH user_name="Alice"
```

## 4. License

This project is licensed under the Apache License 2.0. A copy of the license is available in the `LICENSE` file.

Under the terms of this license, you are required to provide attribution if you use, modify, or distribute this software. Please credit the **Human Machine Protocol** and link to the official website at [openroko.org](https://www.openroko.org).
