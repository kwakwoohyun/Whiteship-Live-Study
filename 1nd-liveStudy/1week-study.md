# 1주차 과제: JVM은 무엇이며 자바 코드는 어떻게 실행하는 것인가.

## > 목표 :
#### 자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기.
## > 학습할것 :
- JVM이란 무엇인가
- 컴파일 하는 방법
- 실행하는 방법
- 바이트코드란 무엇인가
- JIT 컴파일러란 무엇이며 어떻게 동작하는지
- JVM 구성 요소
- JDK와 JRE의 차이
-----------
> JVM이란 무엇인가

JVM은 'Java Virtual Machine'을 줄인 것으로 직역하면 '자바를 실행하기 위한 가상 기계'라고 할 수 있다. 자바로 작성된 애플리케이션은 모두 이 가상 컴퓨터(JVM)에서만 실행되기 때문에, 자바 애플리케이션이 실행되기 위해서는 반드시 JVM이 필요하다. JVM은 JRE안에 있다.</br> 
Java Byte Code를 OS에 맞게 해석해주는 역할을 한다. Java Compiler는 `.java` 파일을 `.class` 파일로 변환시켜준다. Byte Code는 기계어가 아니기 때문에 OS에서 바로 실행되지 않는다. 이때 JVM은 OS가 ByteCode(`.class`)를 이해할 수 있도록 해석 해준다.</br>
하지만 JVM의 해석을 거치기 때문에 c언어 같은 네이티브 언어에비해 속도가 느렸지만 JIT(Just In Time)컴파일러를 구현해 이점을 극복했다. Byte Code는 JVM 위에서 OS상관없이 실행된다. 이런 점이 Java의 가장 큰 장점이라고 할수 있다. OS에 종속적이지 않고 Java 파일 하나만 만들면 어느 디바이스든 JVM 위에서 실행 할 수 있다. JVM은 크게 Class Loader, Runtime Data Areas, Excution Engine 3가지로 구성되어 있다.</br>
![jvm구조](https://miro.medium.com/max/2100/1*slIuYO633BCuBh_gfYRmGg.png "출처 https://heropy.blog/2017/09/30/markdown/") </br>
</br>
자바 프로그램 실행 순서</br>
1. 프로그램이 실행되면 JVM은 OS로부터 이 프로그램이 필요로 하는 메모리를 할당받는다. JVM은 이 메모리를 용도에 따라 여러 영역으로 나누어 관리한다. 
2. 자바 컴파일러(javac)가 자바 소스코드(`.java`)를 읽어들여 자바 바이트코드(`.class`)로 변환 시킨다. 
3. Class Loader를 통해 `.class` 파일들을 JVM으로 로딩한다.
4. 로딩된 `class` 파일들은 Excution Engine을 통해 해석된다.
5. 해석된 바이트 코드는 Runtime Data Areas에 배치되어 실질적인 수행이 이루어진다.</br>
------------
> 컴파일 하는 방법 (mac os)
 
 개발자가 Eclipse나 InteliiJ를 사용하여 java 파일을 만든다.</br>
 그리고 Build라는 작업을 하게되면 JavaCompiler의 `javac` 라는 명령어를 사용하여 `.class` 파일을 생성한다. 
- javac </br>
1. 터미널을 실행한다.
2. 자바 파일이 있는 곳으로 이동한다.
3. 터미널에 아래 명령어를 입력한다.</br>
`$ javac 자바파일이름.java` </br>

![컴파일](https://blog.kakaocdn.net/dn/bdjypD/btqvW2UYOVN/BbrwEZCEa4BEnUMfe3Kquk/img.png "출처 https://kim6394.tistory.com/215")</br>

------------
> 실행하는 방법 (mac os)
- java

컴파일된 `.class` 파일을 `java`명령어를 사용하여 실행한다.</br>
`$ java 자바클래스이름` </br>
 실행할 때는 java명령어를 사용하고, 파일 확장자(.class)를 뺀 클래스 이름만 써주면 된다.</br>
 만약 라이브러리(`.jar`)를 함께 실행해야 한다면 </br>
 `$ java -cp :자르파일 경로.jar 자바클래스이름`</br>

 ------------
> 바이트코드란 무엇인가
- 바이트코드 </br>
바이트코드(Bytecode, portable code, p-code)는 특정 하드웨어가 아닌 가상 컴퓨터에서 돌아가는 실행 프로그램을 위한 이진 표현법이다. 하드웨어가 아닌 소프트웨어에 의해 처리되기 때문에, 보통 기계어보다 더 추상적이다.</br>
사람이 읽기 쉽도록 쓰인 소스 코드와 비교하면, 바이트 코드는 덜 추상적이며, 더 간결하고, 더 컴퓨터 중심적이다. 

- 자바 바이트코드 </br>
자바 바이트 코드(Java bytecode)란 자바 가상 머신이 이해할 수 있는 언어로 변환된 자바 소스 코드를 의미한다.
자바 컴파일러에 의해 변환되는 코드의 명령어 크기가 1바이트라서 자바 바이트 코드라고 불리고 있다.
이러한 자바 바이트 코드의 확장자는 `.class`이다.
자바 바이트 코드는 자바 가상 머신만 설치되어 있으면, 어떤 운영체제에서라도 실행될 수 있다.
-------------
>JIT 컴파일러란 무엇이며 어떻게 동작하는지

- JIT 컴파일러란</br><br>
JIT는 Just-In-Time 의 약자로, 말 그대로 하면, "그 순간" 컴파일러라는 뜻이다.</br>
Java에서 Compile 을 하면 Bytecode 로 변환된다.
이 바이트코드는 기계가 바로 읽을 수 있는 형태가 아니며, 
이 바이트코드는 실제 실행될 때 다시 한번 기계가 읽을 수 있는 형태(native code)로 interpreter 를 통해 해석(JVM)이 되어야 한다.</br>
이렇게 한번에 기계어로 변환하지 않고 두번의 과정을 밟는 이유는 
Java 의 최대 장점 중 하나인 machine-independent 특성때문이다. 
platform independent 라고도 하는데, 요건 한번 작성하면 어떤 기계에서든 돌릴 수 있다는 특성을 말한다.</br>
이 JVM이 bytecode -> 기계어로 interpret(해석) 할 때,
반복되는 내용은 컴파일을 해서 사용하곤 한다.( 한번만 컴파일된다. )
요 과정을 JIT 컴파일링이라고 한다.
JIT 컴파일링은 실행될 때 최초 실행되기 때문에, 최초실행에서는 조금 느릴 수 있다.
![JIT](https://mblogthumb-phinf.pstatic.net/MjAyMDAzMDlfMjQ2/MDAxNTgzNzI5NzE5OTMx.ssOvevl1zjkfpsRqbDaD2OIcrD-DLCk6-09nLVF7_log.-Qgy9hTaFRLQQzMkoq4bX1v1I9e77Mb3BM7WBL_ukU8g.PNG.ki630808/jitcompiler3.PNG?type=w800 "출처 https://m.blog.naver.com/ki630808/221844888233")</br>
 인터프리터의 단점을 보완하기 위해 도입된 방식으로 바이트 코드 전체를 컴파일하여 네이티브 코드로 변경하고 이후에는 해당 메서드를 더 이상 인터프리팅 하지 않고 네이티브 코드로 직접 실행하는 방식이다.</br> 하나씩 인터프리팅하여 실행하는것이 아니라 바이트 코드 전체가 컴파일된 네이티브 코드를 실행하는 것이기 때문에 전체적인 실행 속도는 인터프리팅 방식보다 빠르다.

 - 동작 </br></br>
 네이티브 코드는 캐시에 보관하기 때문에 한 번 컴파일된 코드는 캐시에서 바로 꺼내어 실행하기 때문에 빠르게 수행된다. 하지만 JIT 컴파일러가 컴파일하는 과정은 바이트 코드를 하나씩 인터프리팅 하는 것보다 훨씬 오래 걸리기 때문에 JIT 컴파일러를 사용하는 JVM은 내부적으로 해당 메서드가 얼마나 자주 호출되고 실행되는지 체크하고, 일정 기준을 넘었을 때에만 JIT 컴파일러를 통해 컴파일하여 네이티브 코드를 생성한다.</br>
 JIT 컴파일러를 통한 컴파일 과정은 바이트 코드를 바로 네이티브 코드로 만드는 것이 아니라 안에서 IR(Intermediate Representation)로 변환하여 최적화를 수행하고 그 다음에 네이티브 코드로 변환는 과정을 거친다.
![JIT2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F9949E83D5B73D7EA25 "출처 https://steady-snail.tistory.com/67")
------------
> JVM 구성요소

JVM은 크게 4가지로 구성된다. 
- Class Loader
- Execution Engine
- Runtime Data Area = memory
- Native

![JVM구성요소](https://miro.medium.com/max/2100/1*0QTaWr-_7nK5w4OspltAcA.jpeg "출처 https://medium.com/webeveloper/jvm-java-virtual-machine-architecture-94b914e93d86")

1. Class Loader
![Class Loader](https://miro.medium.com/max/2100/1*CxSdAreqKLQtu0Jx_UrDtA.jpeg "출처 https://medium.com/webeveloper/jvm-java-virtual-machine-architecture-94b914e93d86")
클래스 로더는 로딩, 링크, 초기화 순서로 진행된다. 클래스 로더라는 이름 그대로 클래스 파일을 적재(Runtime Data Area) 하는 역할을 한다.</br>
`.java` 자바 소스 파일을 컴파일 하면 바이트 코드(`.class`)가 생성되며 이런 파일들을 모아, 클래스 로더가 메모리에 적재시킨다.

2. Execution Engine</br>
Execution Engine 은 Class Loader에 의해 Runtime Data Area 에 적재된 클래스(바이트 코드)들을 컴퓨터가 이해할 수 있는 기계어로 변경해 명령어 단위로 실행하는 역할을 한다.</br> 이때 명령어를 하나씩 실행하는 인터프리터 방식이 있고, 바이트 코드를 네이티브 코드로 변환하는 JIT Compiler 방식이 있다.

3. RunTime Data Area</br>
클래스 파일들이 적재되어있는 장소인 Runtime Data Area 에는 5 가지 영역이 존재한다.
- Method Area (= Class Area, Code Area, Static Area)
- Heap Area
- Stack Area
- PC registers
- Native Method stack
--------
> JDK와 JRE의 차이
- JRE란 </br>
JRE(Java Runtime Enviroment) : 컴파일된 자바 프로그램을 실행시킬 수 있는 자바 환경이다. </br>
JRE는 JVM이 자바 프로그램을 동작시킬 때 필요한 라이브러리 파일들과 기타 파일들을 가지고 있다.
JRE는 JVM의 실행환경을 구현했다고 할 수 있다.</br>
자바 프로그램을 실행시키기 위해선 JRE를 반드시 설치해야한다.</br>
하지만 자바 프로그래밍 도구는 포함되어있지 않기 때문에 자바 프로그래밍을 하기 위해선 JDK가 필요하다.
![JRE](https://goodgid.github.io/assets/img/java/java_jdk_jre_1.png "출처 https://goodgid.github.io/Java-JDK-JRE/")

- JDK란 </br>
JDK(Java Development kit) : 자바 프로그래밍시 필요한 컴파일러 등 포함된다.</br>
JDK는 개발을 위해 필요한 도구(javac, java등)들을 포함한다.</br>
JDK를 설치하면 JRE도 같이 설치가 된다.
즉 JDK = JRE + @ 라고 생각하면 된다.
![JRE](https://goodgid.github.io/assets/img/java/java_jdk_jre_2.png "출처 https://goodgid.github.io/Java-JDK-JRE/")