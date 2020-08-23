# TODO
## Alarm clock
Reimplement timer_sleep(), defined in ‘devices/timer.c’.

    주어진 코드는 현재 busy waiting으로 구현되어있다. busy waiting을 사용하지 않고 재구현해야한다.

    waiting threads를 위해 ‘sleep_list’ 만들어야 한다.
    You’ll need to properly use thread_block and thread_unblock in order to implement timer_sleep properly.
    When timer interrupt occurs, check threads to be woken up
    timer_interrupt() in device/timer.c

## Priority scheduling
Implement priority scheduling in Pintos.

    주어진 코드는 현재 Round-Robin scheduling으로 구현되어있다. 이를 priority scheduling으로 구현해야한다.

    Thread with the highest priority in the ready_list should get CPU.

    If a thread is added to the ready list which has a higher priority than the currently running thread, immediately yield the processor to the new thread.
    Also, when threads are waiting for a lock, semaphore, or condition variable, the highest priority waiting thread should be woken up first.
    Solve the ‘Priority Inversion’ problem of ‘Lock’.
    - Implement priority donation.


    Thread priorities range from PRI_MIN (0) to PRI_MAX (63).
    Priority 0 is the lowest priority and priority 63 is the highest.
    If there’s no reason to choose another priority, use PRI_DEFAULT (31).

## Priority donation
Implement priority donation.

    You will need to account for all different situations in which priority donation is required. Be sure to handle multiple donations, in which multiple priorities are donated to a single thread. 
    You must also handle nested donation.
    You must implement priority donation for locks.
    You need not implement priority donation for the other Pintos synchronization constructs. 
    You do need to implement priority scheduling in all cases.

---
## Glossary
- busy waiting

    원하는 자원을 얻기 위해 기다리는 것이 아니라 권한을 얻을 때까지 확인하는 것.
    자원의 권한을 얻는데 많은 시간이 소요되지 않는 상황인 경우 사용.
    Context Switching 비용보다 성능적으로 더 우수한 상황인 경우 사용.
    권한 획득을 위해 많은 CPU를 낭비한다는 단점 존재.

- preemptive priority scheduling

    만약 어떤 프로세스가 ready list에 도착했는데 이 프로세스가 가지는 우선순위가 현재 돌아가고 있는 프로세스의 우선순위보다 높을 경우 기존에 돌아가던 프로세스를 중단시키고, 우선순위가 높은 프로세스를 먼저 수행시킨다.

- priority inversion problem(우선순위 역전 문제)

    우선 순위가 높은 태스크가 READY 상태(실행 가능)로 바뀌었지만 더 낮은 우선순위의 태스크가 CPU를 점유하고 있어서 실행되지 못하는 상태. 이의 문제점은 RTOS 환경하에서 중요한 태스크의 수행이 요구된 시간에 끝내지 못하고, 중요한 태스크의 무한정 대기로 인한 전체 시스템의 이상현상이 발생할 수 있음.


- lock


- semaphore