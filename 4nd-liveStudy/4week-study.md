# 2주차 과제: 자바 데이터 타입, 변수 그리고 배열

## > 목표 :
#### 자바가 제공하는 제어문을 학습하세요.
## > 학습할것 :
- 선택문
- 반복문

### > 과제 (옵션)
- 과제 0. JUnit 5 학습하세요
    - 인텔리J, 이클립스, VS Code에서 JUnit 5로 테스트 코드 작성하는 방법에 익숙해 질 것.
    - 이미 JUnit 알고 계신분들은 다른 것 아무거나!
    - 더 자바, 테스트 강의도 있으니 참고하세요~
- 과제 1. live-study 대시 보드를 만드는 코드를 작성하세요.
    - 깃헙 이슈 1번부터 18번까지 댓글을 순회하며 댓글을 남긴 사용자를 체크 할 것.
    - 참여율을 계산하세요. 총 18회에 중에 몇 %를 참여했는지 소숫점 두자리가지 보여줄 것.
    - Github 자바 라이브러리를 사용하면 편리합니다.
    - 깃헙 API를 익명으로 호출하는데 제한이 있기 때문에 본인의 깃헙 프로젝트에 이슈를 만들고 테스트를 하시면 더 자주 테스트할 수 있습니다.
- 과제 2. LinkedList를 구현하세요.
    - LinkedList에 대해 공부하세요.
    - 정수를 저장하는 ListNode 클래스를 구현하세요.
    - ListNode add(ListNode head, ListNode nodeToAdd, int position)를 구현하세요.
    - ListNode remove(ListNode head, int positionToRemove)를 구현하세요.
    - boolean contains(ListNode head, ListNode nodeTocheck)를 구현하세요.
- 과제 3. Stack을 구현하세요.
    - int 배열을 사용해서 정수를 저장하는 Stack을 구현하세요.
    - void push(int data)를 구현하세요.
    - int pop()을 구현하세요.
- 과제 4. 앞서 만든 ListNode를 사용해서 Stack을 구현하세요.
    - ListNode head를 가지고 있는 ListNodeStack 클래스를 구현하세요.
    - void push(int data)를 구현하세요.
    - int pop()을 구현하세요.
- 과제 5. Queue를 구현하세요.
    - 배열을 사용해서 한번
    - ListNode를 사용해서 한번
-----------
> 선택문

- 제어문
    - 코드의 실행 흐름(순서)을 제어하는 구문
- 조건문 
    - 조건에 따라 코드의 실행 흐름을 제어하는 구문
    - `If` 문
        - 조건식의 진리값이 참인 경우 코드를 실행
        - 형식) `if(조건식)` 처리할 문장
        - 조건식에는 변수, 수식(관계, 논리연산자) 등이 들어갈 수 있음
        - ```
            if (su % 2 == 0) {
                System.out.println(su+"은(는) 짝수입니다.");
            }
            ```
    - `If-Else` 문
        - 조건식의 진리값이 참인 경우에는 if 다음의 코드를 실행하고 진리값이 거짓인 경우에는 else다음의 코드를 실행
        - 형식) `if(조건식) else`
        - ```
            if (su % 2 == 1) {
                System.out.println(su+"은(는) 홀수입니다.");
            } else  {
                System.out.println(su+"은(는) 짝수입니다.");
            }
            ```
    - `중첩 if` 문
        - if문 내부에 또 다른 if문이 나오는 구문
        - 형식) `if(조건식) { if(조건식) { `
        - ```
            if ((1 <= su) && (su <= 100)) {
                if (su % 2 == 1) {
                    System.out.println(su + "은(는) 홀수입니다.");
                } else {
                    System.out.println(su + "은(는) 짝수입니다.");
                }
            } else {
                System.out.println("숫자는 1~100 안에서 입력해 주세요!!");
            }
            ```
- 선택문
    - `switch` 문
        - 다중 if문 대신 사용, 조건문의 일종으로 볼 수 있다.
        - if문을 여러 개 사용하면 실행 속도가 느려지기 때문에 사용한다.
        - switch함수의 매개변수에 들어오는 값에 따라 코드를 실행한다.
        - 스위치 문은 조건에 기초한 다수의 블록 중 한 블록의 명령문을 실행한다.
        - switch 문에는 많은 선택 항목이 있으며 각 선택 항목에 대해 다른 작업을 수행 할 수 있다.
        - 각 케이스에는 선택적인 `break` 문 이 있다. 
        - 어떤 경우에도 `break` 문을 사용하지 않으면 `break` 문에 도달 할 때까지 다음 `case` 로 실행이 계속된다.
        - `break` 문 이 없으면 default case를 포함한 모든 case를 실행한다. 
        -형식) `switch(조건식){ case 값1: break; case 값2: break; ...`
        - ```
            switch (su % 2) {
                case 0:
                    System.out.println(su + "은(는) 짝수입니다.");
                    break;
                case 1:
                    System.out.println(su + "은(는) 홀수입니다.");
                    break;
            }
            ```
![스위치문](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcqPEVa%2FbtqOtfP0CE6%2FWHCO43zL2jeHF11UcZvuXk%2Fimg.png "출처 https://kils-log-of-develop.tistory.com/349")

        