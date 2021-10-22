# Doc for PyPortal Output Data

## Directory structure

PyPortal

|---cpython-3.7.11

​      |---python (execution)

|---test

​      |---Electrum-4.1.5

## Input

Format:

```
sudo -E ./python -X PTTrace=@total_method_name @relative_path_to_python
```

Example:

1. specific-trace mode:

```
sudo -E ./python -X PTTrace=../test/Electrum-4.1.5/packages/aiorpcx/curio.spawn_sync ../test/Electrum-4.1.5/run_electrum
```

2. all-trace mode:

```
sudo -E ./python -X PTTrace=all ../test/Electrum-4.1.5/run_electrum
```

## Output after Decode

Output is stored in tid-all.out

Format:

1. one line "**tid-xxx**" (xxx is system_tid)
2. mutiple lines of traced branch **bytecode id** and **if_taken** flag
3. (only record **POP_JUMP_IF_FALSE**, **POP_JUMP_IF_TRUE**, **JUMP_IF_TRUE_OR_POP**, **JUMP_IF_FALSE_OR_POP**, **FOR_ITER**)

Example: (114 means POP_JUMP_IF_FALSE)

```
tid-xxx
114 0 <-- sequence of branch bytecode id and if_taken, can be empty
114 1
...
tid-xxx
...
```

## Baseline

Stores in baseline.out, **no if_taken flag**, divided by **pvm_tid**