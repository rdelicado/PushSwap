# 🔢 Push_swap

[![Language](https://img.shields.io/badge/Language-C-blue.svg)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Algorithm](https://img.shields.io/badge/Algorithm-Sorting-green.svg)](https://en.wikipedia.org/wiki/Sorting_algorithm)
[![Data Structure](https://img.shields.io/badge/Data_Structure-Stack-red.svg)](https://en.wikipedia.org/wiki/Stack_(abstract_data_type))
[![42 School](https://img.shields.io/badge/42-School_Project-purple.svg)](https://42.fr/)

## 📋 Description

**Push_swap** es un algoritmo de ordenamiento eficiente que utiliza dos stacks (A y B) y un conjunto limitado de operaciones para ordenar una serie de números enteros. Este proyecto demuestra el dominio de algoritmos de ordenamiento, optimización de movimientos, análisis de complejidad y estructuras de datos.

El objetivo es ordenar el stack A en orden ascendente usando el menor número posible de operaciones, desarrollando un algoritmo que sea eficiente tanto en términos de movimientos como de complejidad temporal.

## 🚀 Features

### Core Operations
- **sa/sb**: Intercambiar los dos primeros elementos del stack
- **pa/pb**: Mover el primer elemento de un stack al otro
- **ra/rb**: Rotar hacia arriba (primer elemento va al final)
- **rra/rrb**: Rotar hacia abajo (último elemento va al principio)
- **ss/rr/rrr**: Ejecutar operaciones en ambos stacks simultáneamente

### Algorithm Features
- **Smart Sorting**: Algoritmo optimizado basado en el tamaño del stack
- **Cost Analysis**: Cálculo del costo mínimo para cada movimiento
- **Median Strategy**: División del stack usando la mediana para optimizar
- **Target Finding**: Búsqueda eficiente de posiciones objetivo
- **Move Optimization**: Minimización de operaciones redundantes

### Performance Targets
- **3 números**: ≤ 3 operaciones
- **5 números**: ≤ 12 operaciones  
- **100 números**: ≤ 700 operaciones
- **500 números**: ≤ 5500 operaciones

## 🛠️ Installation

### Prerequisites
```bash
# Standard C development tools
sudo apt-get install build-essential
```

### Compilation
```bash
git clone https://github.com/rdelicado/PushSwap.git
cd PushSwap
make
```

## 🚀 Usage

### Basic Examples
```bash
# Simple sorting
./push_swap 3 2 1
# Output: sa

# Medium complexity
./push_swap 4 3 2 1 5
# Output: pb ra pb ra sa ra pa pa

# Random numbers
./push_swap 42 17 89 3 56 21
```

### Testing Performance
```bash
# Generate random numbers and test
ARG=$(shuf -i 1-100 -n 5 | tr '\n' ' '); ./push_swap $ARG

# Count operations
./push_swap 5 2 3 1 4 | wc -l

# Verify sorting correctness
ARG="4 67 3 87 23"; ./push_swap $ARG | ./checker $ARG
```

### Using with Checker
```bash
# Test if sequence sorts correctly
echo -e "sa\nra\npb" | ./checker 3 2 1

# Pipeline test
./push_swap 3 2 5 1 4 | ./checker 3 2 5 1 4
# Output: OK (if correctly sorted)
```

## 📁 Project Structure

```
PushSwap/
├── Makefile
├── push_swap.c                  # Main program
├── push_swap.h                  # Headers and structures
├── libft/                       # Custom C library
├── utils_algorithm.c            # Core sorting algorithms
├── utils_cost.c                 # Cost calculation
├── utils_cost1.c                # Cost optimization
├── utils_move*.c                # Movement operations
├── utils_nodes.c                # Node management
├── utils_push.c                 # Push operations (pa/pb)
├── utils_rotate.c               # Rotate operations (ra/rb)
├── utils_reverse.c              # Reverse rotate (rra/rrb)
├── utils_swap.c                 # Swap operations (sa/sb)
├── utils_split_*.c              # Stack splitting logic
├── utils_stacks.c               # Stack utilities
├── utils_towers.c               # Two towers algorithm
├── python_visualizer.py         # Algorithm visualizer
└── push_swap_tester-main/       # Testing framework
```

## 🧠 Algorithm Strategy

### Size-Based Approach
```bash
# Small stacks (≤3): Direct sorting
./push_swap 3 1 2
# Uses optimized tiny_sort()

# Medium stacks (4-5): Manual optimization  
./push_swap 5 2 3 1 4
# Strategic use of stack B

# Large stacks (>5): Two towers algorithm
./push_swap $(shuf -i 1-100 -n 20 | tr '\n' ' ')
# Median-based splitting and cost analysis
```

### Core Algorithm Phases

1. **Input Validation**: Check for duplicates and valid integers
2. **Size Analysis**: Choose algorithm based on stack size
3. **Stack Splitting**: Divide elements using median strategy
4. **Cost Calculation**: Analyze movement cost for each element
5. **Optimal Moves**: Execute minimum cost operations
6. **Final Sorting**: Return all elements to stack A in order

## 🧪 Testing

### Performance Testing
```bash
# Test with random numbers
for i in {1..10}; do
  ARG=$(shuf -i 1-100 -n 5 | tr '\n' ' ')
  echo "Test $i: $(./push_swap $ARG | wc -l) operations"
done

# Stress test with large numbers
ARG=$(shuf -i 1-500 -n 100 | tr '\n' ' ')
./push_swap $ARG | wc -l
```

### Correctness Verification
```bash
# Basic correctness
./push_swap 3 2 1 | ./checker 3 2 1

# Edge cases
./push_swap 1        # Already sorted
./push_swap 2 1      # Simple swap
./push_swap          # No arguments
```

### Visualization
```bash
# Use Python visualizer
python3 python_visualizer.py
# Interactive visualization of sorting process
```

## 🚨 Common Issues

### Invalid Arguments
```bash
# These will show "Error"
./push_swap abc      # Non-numeric
./push_swap 1 2 1    # Duplicates  
./push_swap "1 2"    # Needs proper parsing
```

### Memory Management
El programa gestiona correctamente la memoria para evitar leaks:
- Stack creation and destruction
- Split string memory cleanup
- Linked list node management

### Performance Optimization
- Minimize redundant operations (e.g., ra followed by rra)
- Use simultaneous operations (rr, rrr, ss) when possible
- Calculate minimum cost paths between stacks

## 📊 Performance Analysis

### Operation Efficiency
- **Simple cases** (≤3): Direct pattern matching
- **Small stacks** (4-5): Optimized manual sorting
- **Large stacks** (>5): Cost-based algorithm with O(n²) complexity

### Benchmark Results
| Stack Size | Max Operations | Typical Performance |
|------------|----------------|-------------------|
| 3 numbers  | 3              | 0-2 operations    |
| 5 numbers  | 12             | 8-12 operations   |
| 100 numbers| 700            | 500-650 operations |
| 500 numbers| 5500           | 4500-5200 operations |

### Algorithm Complexity
- **Time**: O(n²) for large inputs
- **Space**: O(n) for stack storage
- **Operations**: Optimized for minimum moves

## 🎯 Key Algorithms

### Tiny Sort (≤3 elements)
Handles all possible combinations of 3 or fewer elements with optimal moves.

### Two Towers Algorithm
1. Calculate median of all numbers
2. Push smaller half to stack B
3. Find optimal insertion points
4. Calculate movement costs
5. Execute minimum cost operations
6. Push everything back to A in sorted order

### Cost Calculation
For each element in stack B:
- Calculate cost to move to top of B
- Find target position in stack A  
- Calculate total movement cost
- Choose minimum cost element to move

## 👨‍💻 Authors

- **Rubén Delicado** - [@rdelicado](https://github.com/rdelicado)

*42 Málaga - Algorithm & Data Structures Project*

## 📜 License

This project is part of the 42 School curriculum. Educational use only.

---

*An efficient sorting algorithm using dual stacks, demonstrating advanced algorithmic thinking and optimization techniques.*