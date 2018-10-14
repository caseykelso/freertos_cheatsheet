# freertos_cheatsheet
FREERTOS Notes / Cheat Sheet

# Heap
## Heap_1 - Small embedded systems
* All memory allocation happens at start-up
* Pseudo "static"

## Heap_2 - Deprecated
* Heap is allocated at task creation time
* available for backwards compatibility

## Heap_3 - Standard malloc() free()
* thread-safe by temporarily suspending the scheduler

## Heap_4 - First Fit Algorithm
* Coalescences adjacent free blocks together
* Single statically allocated array

## Heap_5
* Identical to Heap_4  with the exception that heap_5 is not limited to allocating memory to a statically declared array
* Heap_5 can allocate memory from multiple and separate memory spaces

# Task Management
* Tasks are concurrent functions
* Tasks must not be allowed to return, rather tasks infinitely loop
* Tasks have their own stack

## Task Priorities
* configMAX_PRIORITIES should be kept to the minimum value necessary to minimize RAM usage
* set configUSE_PORT_OPTIMIISED_TASK_SELECTION to 1 if possible to take advantage of architecture specific optimizations
* The highest priority task will be selected to enter the running stage
* When more than one task is available at equal priority, each task will be scheduled round-robin

## Time Measurement and Tick Interrupt
* configTICK_RATE_HZ sets the tick rate a typical value is 100
* pdMS_TO_TICKS( macro converts a time specific in milliseconds into a time specified in ticks (note that pdMS_TO_TICKS() cannot be used if configTICK_RATE_HZ is greater than 1000

### Running State
### Not Running State
#### BLocked State
* vTaskDelay() places the calling task into the Blocked state for a fixed number of tick interrupts

#### Suspended State
#### Ready State
#### 
