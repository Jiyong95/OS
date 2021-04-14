## Multilevel Queue Scheduling

- Process groups
  - System processes
  - Interactive processes
  - Interactive editing processes
  - Batch processes
  - Student processes
- Single ready queue → Several separate queues

  - 각각의 Queue 에 절대적 우선순위 존재
  - 또는 CPU time 을 각 Queue 에 차등배분
  - 각 Queue 는 독립된 scheduling 정책

  ```
  process groups 종류에 따른 queue를 설정하여 각각 queue마다 우선순위, CPU time, Scheduling를 정해둠

  애초에 process group종류에 따라 해당하는  queue에 넣음
  ```

</br></br>

## Multilevel Feedback Queue Scheduling

- 복수 개의 Queue
- 다른 Queue 로의 점진적 이동

  - 모든 프로세스는 하나의 입구로 진입
  - 너무 많은 CPU time 사용 시 다른 Queue 로
  - 기아 상태 우려 시 우선순위 높은 Queue 로

  ```
  여러 Queue를 두고 1번째 Queue에 Process를 두고 문제가 있는 Process는 2번째 Queue로 넘기고 문제생기면 3번째.....

  모든 process가 1번째 Queue로 들어온다음 조건에 따라 2번째 3번째로 이동
  ```

</br></br>

## Process Creation

- 프로세스는 프로세스에 의해 만들어진다!
  - 부모 프로세스 (Parent process)
  - 자식 프로세스 (Child process)
    - cf. Sibling processes(형제 process)
  - 프로세스 트리 (process tree)
- Process Identifier (PID) 프로세스 ID
  - Typically an integer number
  - cf. PPID(Parent Process ID)
  ```
  OS부팅 후 OS가 0번째 process를 만듬
  0번째 Process가 1,2,3,4...process를 만든다.
  이 모습을 보고 프로세스 트리라고함
  ```
- 프로세스 생성

  - fork() system call – 부모 프로세스 복사

  ```
  새로운 system call을 만드는 명령어가 fork()
  ```

  - exec() – 실행파일을 메모리로 가져오기

  ```
  하드디스크에 있는 실행파일을 메모리로 가져오는 명렁어
  ```

  </br></br>

## Process Termination

- 프로세스 종료
  - exit() system call
  - 해당 프로세스가 가졌던 모든 자원은 O/S 에게 반환 (메모리, 파일, 입출력장치 등)

</br></br>

## Thread?

- 쓰레드 (Thread)
  - 프로그램 내부의 흐름, 맥

```java
class Test {
	public static void main(String[] args) {
		int n = 0;
		int m = 6;
		System.out.println(n+m);
		while (n < m)
			n++;
		System.out.println("Bye");
}
```

</br></br>

## Multithreads

- 다중 쓰레드 (Multithreads)
  - 한 프로그램에 2개 이상의 맥
  - 맥이 빠른 시간 간격으로 스위칭 된다 ⇒ 여러 맥이 동시에 실행
    되는 것처럼 보인다 (concurrent vs simultaneous)
- 예: Web browser
  - 화면 출력하는 쓰레드 + 데이터 읽어오는 쓰레드
- 예: Word processor
  - 화면 출력하는 쓰레드 + 키보드 입력 받는 쓰레드 + 철자/문법
    오류 확인 쓰레드
- 예: 음악 연주기, 동영상 플레이어, Eclipse IDE, …

</br></br>

## Thread vs Process

- 한 프로세스에는 기본 1개의 쓰레드
  - 단일 쓰레드 (single thread) 프로그램
- 한 프로세스에 여러 개의 쓰레드
  - 다중 쓰레드 (multi-thread) 프로그램
- 쓰레드 구조
  - 프로세스의 메모리 공간 공유 (code, data)
  - 프로세스의 자원 공유 (file, i/o, …)
  - 비공유: 개별적인 PC, SP, registers, stack
- 프로세스의 스위칭 vs 쓰레드의 스위칭
