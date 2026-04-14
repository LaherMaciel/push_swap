# push_swap

[![42](https://img.shields.io/badge/42-Project-blue)](https://42.fr)
[![C](https://img.shields.io/badge/Language-C-green)](https://en.wikipedia.org/wiki/C_(programming_language))

> Sort a stack of integers using two stacks and a limited set of operations, in the minimum number of moves.

## Overview

`push_swap` is a 42 School Rank 2 project. Given a stack of integers as arguments, the program outputs the shortest sequence of operations to sort them in ascending order using two stacks (`a` and `b`).

## Allowed operations

| Operation | Description |
|-----------|-------------|
| `sa` | Swap top two elements of stack a |
| `sb` | Swap top two elements of stack b |
| `ss` | `sa` and `sb` simultaneously |
| `pa` | Push top of stack b to stack a |
| `pb` | Push top of stack a to stack b |
| `ra` | Rotate stack a up (top becomes bottom) |
| `rb` | Rotate stack b up |
| `rr` | `ra` and `rb` simultaneously |
| `rra` | Reverse rotate stack a (bottom becomes top) |
| `rrb` | Reverse rotate stack b |
| `rrr` | `rra` and `rrb` simultaneously |

## Usage

```bash
make
./push_swap 3 1 4 1 5 9 2 6
```

Outputs the list of operations to sort the input.

### Validate with the checker (bonus)

```bash
make bonus
ARG="3 1 4 1 5 9 2 6"
./push_swap $ARG | ./Checker/checker $ARG
# Output: OK
```

## Project structure

```
push_swap/
├── srcs/
│   ├── main.c                   # Entry point and auto_sort
│   ├── push_swap.h              # Header
│   ├── sort.c / sort2.c / sort3.c   # Sorting algorithms
│   ├── sort_conditions.c        # Best move selection
│   ├── sorters.c                # Small stack sorters
│   ├── moviments.c / moviments2.c   # Stack operations
│   ├── find.c / find2.c         # Stack search utilities
│   ├── p_decisions.c            # Push decision logic
│   ├── stack_work.c / stack_work2.c # Stack manipulation
│   ├── error_management*.c      # Input validation
│   └── ft_*.c                   # Custom utility functions
├── Checker/                     # Bonus — validates operation sequences
├── libft/                       # Custom C library
└── Makefile
```

## Algorithm

Uses a **chunk-based approach** combined with a **cost optimisation** strategy:

1. Numbers are divided into value chunks
2. Each chunk is pushed to stack b in an efficient order
3. Stack b is then pushed back to a using the minimum number of rotations per element
4. Final rotation brings the smallest number to the top

## Make targets

| Target | Description |
|--------|-------------|
| `make` | Build `push_swap` |
| `make bonus` | Build the bonus `Checker` |
| `make clean` | Remove object files |
| `make fclean` | Remove object files and binaries |
| `make re` | Rebuild from scratch |
| `make norm` | Run norminette |
| `make run` | Quick test run |
| `make run_checker` | Run and validate with checker |
| `make val` | Run with valgrind |
| `make run_visualizer` | Launch the push_swap visualizer |
| `make run_tester` | Run the automated tester |

## Author

**Laher Maciel**
- GitHub: [@LaherMaciel](https://github.com/LaherMaciel)
- 42 Login: lawences
