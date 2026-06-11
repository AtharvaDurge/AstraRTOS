## Mutex sample code

Two tasks (`task1` and `task2`) increment and print a shared counter
over UART, protected by a mutex.

`task1` runs every 500 ms, `task2` runs every 700 ms. Both run at
priority 2 with a stack size of 128.

The mutex (`os_mutex_init`, `os_mutex_take`, `os_mutex_give`) ensures
that incrementing the counter and printing its value happens
atomically — preventing the two tasks from interleaving and producing
inconsistent output or a corrupted counter value.

### Expected output (over UART1)
```
Task1: counter = 1
Task2: counter = 2
Task1: counter = 3
Task2: counter = 4
...
```