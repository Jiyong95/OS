## Priority Scheduling (1)

- Priority (우선순위): typically an integer number
  - Low number represents high priority in general (Unix/Linux)

| Process | Burst Time(사용시간) | Priority |
| ------- | -------------------- | -------- |
| P1      | 10                   | 3        |
| P2      | 1                    | 1        |
| P3      | 2                    | 4        |
| P4      | 1                    | 5        |
| P5      | 5                    | 2        |

- AWT

```
	P2	P5		P1		P3		P4
{  0 +	1	+ 	6	+	16	+	18}  /  5 = 8.2 msec
```

## Priority Scheduling (2)

- Priority(우선순위 정하는 법)

  - Internal(내부요소): time limit, memory requirement, i/o to CPU burst, …

  - External(외부요소): amount of funds being paid(돈 많이 낸 사람), political factors, …

- Preemptive or Nonpreemptive

```
Preemptive : 새로 들어온 Process가 실행중인 Process보다 우선순위가 높을 때
```

- Problem
  - Indefinite blocking: starvation (기아)
  ```
  Ready Queue에서 기다리고있는 Process가 현재 + 새로 계속 들어오는 Process보다 우선순위가 낮아버리면 계속 기다리게 됨
  ```
  - Solution: againg
  ```
  기다리는 시간에 따라 우선순위를 조금씩 올려주는 방법
  ```

## Round-Robin (1)(빙빙도는 새)

- Time-sharing system (시분할/시공유 시스템)
- Time quantum 시간양자 = time slice (10 ~ 100msec)
  ```
  시분할 시스템에서의 똑같이 분배할 시간을 말함
  ```
- Preemptive scheduling

| Process | Burst Time (msec) |
| ------- | ----------------- |
| P1      | 24                |
| P2      | 3                 |
| P3      | 3                 |

- AWT(Average waiting time)

```
Time Quantum = 4msec

	P1		P2		P3
{(10-4)	+	4	+	7} / 3	=	5.66 msec
```

## Round-Robin (2)

- Performance depends on the size of the time quantum

```
Time quantum의 사이즈에 의존적이다.
```

- ∆(time quantum) → ∞ FCFS
  ```
  process가 끝나야 switching이 일어남 = FCFS
  ```
- ∆ → 0 Processor sharing (\* context switching overhead => dispatcher 많이 일어남 -> 부담)
  ```
  switching이 빈번하게 일어나서
  process가 동시에 돌아가는 것처럼 보인다.
  ```

| Process | Burst Time (msec) |
| ------- | ----------------- |
| P1      | 6                 |
| P2      | 3                 |
| P3      | 1                 |
| P4      | 7                 |

- Example: Average turnaround time (ATT)

```
ATT 구하기

Q1.
Time quantum(∆ = 1)
P1->P2->P3->P4 1씩 계속 돌아감

turnaround : 시작해서 끝날때까지의 시간
P1 : 15
P2 : 9
P3 : 3
P4 : 17

Q2.
Time Quantum(∆ = 5)


```
