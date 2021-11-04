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
2. mutiple lines of traced byte codes(branch, CALL and RET)
   1. branch bytecode has **id** and **if_taken** flag
   2. CALL and RET only have bytecode **id** (83 is RET, other is CALL)

Traced Field:

1. Now it will also trace sub-calls of traced method.

## Baseline

Stores in baseline.out, same format with hardware-traced output.