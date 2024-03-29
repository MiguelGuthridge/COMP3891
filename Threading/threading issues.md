## Race condition
Two [[thread]]s access same data (memory, files). See [[race condition]].

## Deadlock
Two threads waiting to access same data (memory, files). See [[deadlock]].

## Starvation
High priority threads use all resources, leaving none for low priority threads. See [[starvation]].

## Livelock
Similar to deadlock, but both threads are still doing stuff. See [[livelock]].

## What we need
- Avoid by **controlling access to shared resources using shared code** (critical sections)
- **Mutual exclusion** - no two processes running simultaneously in critical section
- No assumptions made about speed or number of CPUs (unlike UNSW's version of [[os-161]])
- **Progress** - process running outside critical region may block another process
- **Bounded** - no process waits forever to enter its critical region

## Solutions

### Global [[lock]] (bad)
- Not atomic - just creates a smaller race condition

### Taking turns (also bad)
- Requires cooperation - can't be trusted to perform well
- It's correct at least

### Disabling interrupts (similarly bad)
- Disable interrupts during critical sections
- Can only work in [[kernel]] - apps can't be trusted, since it requires cooperation
- Slows interrupt response times
- Doesn't work on [[multiprocessor system|multiprocessor systems]], since it doesn't block other [[CPU|CPUs]].

### Hardware support (aka [[spin lock]])
- "test and set" instruction
- Atomic operation
- Busy waiting - consumes [[CPU]]

### Sleep-wakeup
- Sleep processes while they wait
- Wake them up when there is data available
