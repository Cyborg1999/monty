# Monty - Stacks, Queues - LIFO, FIFO

By the end of the project we should be able to decribe:

* What do LIFO and FIFO mean
* What is a stack, and when to use it
* What is a queue, and when to use it
* What are the common implementations of stacks and * queues
* What are the most common use cases of stacks and queues
* What is the proper way to use global variables

## Monty Language

Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it. The goal of this project is to create an interpreter for Monty ByteCodes files

## Requirements

* Allowed editors: `vi`, `vim`, `emacs`
* All your files will be compiled on `Ubuntu 20.04 LTS` using `gcc`, using the options `-Wall -Werror -Wextra -pedantic -std=c89`
* The code should use the Betty style.

## Data Structures and code snippets

The following data structures will be used for this project.

```c
/**
 * struct stack_s - doubly linked list representation of a stack (or queue)
 * @n: integer
 * @prev: points to the previous element of the stack (or queue)
 * @next: points to the next element of the stack (or queue)
 *
 * Description: doubly linked list node structure
 * for stack, queues, LIFO, FIFO
 */
typedef struct stack_s
{
        int n;
        struct stack_s *prev;
        struct stack_s *next;
} stack_t;

```

The opcode structure :

```c
/**
 * struct instruction_s - opcode and its function
 * @opcode: the opcode
 * @f: function to handle the opcode
 *
 * Description: opcode and its function
 * for stack, queues, LIFO, FIFO
 */
typedef struct instruction_s
{
        char *opcode;
        void (*f)(stack_t **stack, unsigned int line_number);
} instruction_t;
```

## The Monty Program

1.Usage: `monty file`

* where file is the path to the file containing Monty byte code

2.If the user does not give any file or more than one argument to your program, print the error message `USAGE: monty file`, followed by a new line, and exit with the status `EXIT_FAILURE`

3.If, for any reason, it’s not possible to open the file, print the error message `Error: Can't open file <file>`, followed by a new line, and exit with the status `EXIT_FAILURE`

* where `<file>` is the name of the file

4.If the file contains an invalid instruction, print the error message `L<line_number>:` unknown instruction `<opcode>`, followed by a new line, and exit with the status `EXIT_FAILURE`

* where is the line number where the instruction appears.
* Line numbers always start at 1

5.The monty program runs the bytecodes line by line and stop if either:

* it executed properly every line of the file
* it finds an error in the file
* an error occured

6.If you can’t malloc anymore, print the error message `Error: malloc failed`, followed by a new line, and exit with status `EXIT_FAILURE.`
7.You have to use `malloc` and `free` and are not allowed to use any other function `from man malloc` (realloc, calloc, …)
