# asm_py

`asm_py` is a Python library that simulates basic CPU operations and provides a simple framework for running assembly-like instructions. It is ideal for educational purposes, allowing users to interact with CPU registers, perform memory operations, and execute basic assembly commands in Python.

## Features

- Simulate basic CPU registers (`ax`, `bx`, `cx`, `dx`) with operations like `MOV`, `ADD`, and `SUB`.
- Manipulate simulated memory.
- Run assembly code using NASM and system linkers.
- Use helper functions to work with assembly code.

## Installation

You can install the `asm_py` library directly from PyPI:

```bash
pip install asm_py
```

Alternatively, clone this repository and install manually:

```bash
git clone https://github.com/yourusername/asm_py.git
cd asm_py
python setup.py install
```

## Usage

Here's a basic example of how to use `asm_py` to simulate CPU operations:

```python
from asm_py.core import CPU

def add_registers():
    cpu = CPU()
    cpu.mov('ax', 10)  # Move 10 into AX
    cpu.mov('bx', 5)   # Move 5 into BX
    cpu.add('ax', cpu.registers['bx'])  # Add BX to AX
    cpu.print_registers()

if __name__ == "__main__":
    add_registers()
```

This will output:

```
CPU Registers:
AX: 15
BX: 5
CX: 0
DX: 0
```

### Running Assembly Code

`asm_py` also allows you to run assembly code using NASM and the system linker. Here's an example:

```python
from asm_py.core import run_assembly

asm_code = """
section .text
    global _start
_start:
    mov eax, 1          ; Syscall number for exit
    mov ebx, 0          ; Exit code
    int 0x80            ; Interrupt to make the syscall
"""

run_assembly(asm_code)
```

This example writes, assembles, and runs a simple assembly code to exit a program.

## API Reference

### CPU Class

- `mov(register, value)`: Moves a value into a CPU register.
- `add(register, value)`: Adds a value to a CPU register.
- `sub(register, value)`: Subtracts a value from a CPU register.
- `load_to_memory(address, value)`: Loads a value into a specified memory address.
- `print_registers()`: Prints the current state of the CPU registers.
- `print_memory(start=0, end=10)`: Prints a segment of memory between two addresses.

### run_assembly(assembly_code: str, filename='temp.asm')

Compiles and runs assembly code using NASM and the system linker.

- `assembly_code`: The assembly code to be compiled and executed.
- `filename`: The temporary file where assembly code will be saved.

## Running Tests

Unit tests are provided for the core functionality of the library. You can run the tests using `pytest`:

```bash
pytest tests/
```

## Contributing

Contributions are welcome! Please feel free to submit a pull request or report issues to the repository.

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/feature-name`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/feature-name`).
5. Open a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Happy coding!
```

### What this README includes:
1. **Introduction and Overview**: A quick summary of the library's purpose.
2. **Features**: Bullet points outlining what the library offers.
3. **Installation Instructions**: Explains how to install the library either via PyPI or manually.
4. **Usage Example**: A code snippet demonstrating basic usage.
5. **API Reference**: Describes key classes and methods in the library.
6. **Testing Instructions**: Explains how to run the tests.
7. **Contributing**: Guidelines for contributing to the project.
8. **License**: Information about the license.

You can modify the placeholders such as the GitHub URL or author information according to your specific project. Let me know if you need more details or adjustments!
