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

-------
> 반복문

- 자바의 반복문은 조건이 참이 될 때까지 블록을 반복적으로 실행하는 데 사용된다.
- 루프를 사용하면 코드를 여러 번 또는 조건을 만족할 때까지 실행할 수 있다.

![반복문](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwgV9T%2FbtqOqUrOCDX%2FfhRVzcaStumboIZsoP1RjK%2Fimg.png "출처 https://kils-log-of-develop.tistory.com/349")

- `for`문
    - 사용자가 코드 블록을 여러 번 실행하려는 경우 사용한다.
    - 반복 횟수가 고정되어 있는 것이 특징이다.
    -  `for ( ;; )` 의경우는 무제한 반복횟수라고 볼 수 있다.
    - `for` 루프는 초기화, 조건, `for` 루프 본문, 증가 / 감소의 네 부분으로 구성된다.
    1. 초기화 
        - 초기화는 루프의 첫 번째 부분이며 한 번만 발생한다.
        - 여기에서 변수를 선언 및 초기화하거나 이미 초기화 된 변수를 사용할 수 있다.
    2. 조건
        - 조건은 루프의 두 번째 부분이며 부울 값을 `true` 또는 `false`로 반환해야하는 조건을 제공 / 작성해야한다.
        - 조건이 거짓이 될 때까지 실행을 계속한다.
    3. for 루프 본문
        - 조건 참을 평가 한 후 매번 실행되는 코드 블록을 포함한다.
    4. 증가 / 감소
        - 변수의 인덱스 값을 업데이트하는데 사용됩니다.
        
    ![반복문](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbcGiKo%2FbtqOvdRbSsE%2FFhTUipIn8BX2toBxnEwHlk%2Fimg.png "출처 https://kils-log-of-develop.tistory.com/349")
    ```
    for(initialization; condition; increment/decrement)
        {
            // Body of for loop
        }
    ```

- `while`문
    - 루프 상태  조건이 만족 될 때까지 허용 코드가 반복하여 실행된다.
    - 반복 횟수가 고정되지 않은 경우 `while` 루프 를 사용하는 것이 좋다.
    ```
    while(condition)
        {
            // Body of while loop
        }
    ```
    - `true`를 반환 하면 `while` 루프 의 본문 이 실행된다.
    - `while` 루프 의 본문 에서 명령문은 다음 반복을 위해 처리되는 변수에 대한 업데이트 값을 포함한다.
    - `false`를 반환하면 루프가 종료되어 수명주기의 끝을 표시한다.
    - `while` 루프 조건에서 `true`를 전달하면 무한 루프가된다.

    ![반복문](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb47mzT%2FbtqOtFnmy5l%2FYS9GErIOvxO9WqrcZhIobk%2Fimg.png "출처 https://kils-log-of-develop.tistory.com/349")

- `do-while`문
    - `while` 루프와 거의 유사하다. 
    - 루프 본문을 실행 한 후 조건을 확인하는 유일한 차이점이있다.
    - 조건에 관계 없이 적어도 한번 이상 반복문을 돈다는 특징을 가진다. 
    - Exit Control Loop 라고도  합니다. 
    ```
    do
    {
        // Body of loop
    } While(condition);
    ```
    ![반복문](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbnacqS%2FbtqOtDpxm01%2FqY8Qji1swG3gkRGF5asuj1%2Fimg.png "출처 https://kils-log-of-develop.tistory.com/349")

- `foreach`문
    - `foreach`는 J2SE 5.0 부터 추가되었다.
    - `foreach` 라는 키워드가 따로 있는 것은 아니고 동일한 for를 이용한다. 
    - 하지만 조건식 부분이 조금 다르다. 보통 다른 언어에서 for each 라고 많이 하므로 자바에서도 보통 for each문이라고 말한다.
    - `foreach`문은 따로 반복회수를 명시적으로 주는 것이 불가능하고, 1스탭씩 순차적으로 반복될때만 사용가능하다는 제약이 있다.
    ```
    for (변수타입 변수명 : 루프를 돌릴 객체) {
       // 실행 코드
    }
    ```

    > 과제 (옵션)은 진도를 다 따라가고 추가하겠습니다. ㅠ_ㅠ
    
    전에 인프런 강의를 통한 JUnit를 수강하며 정리한 블로그 일단 올려놓겠습니다!
    
    [JUnit5 티스토리 블로그](https://lifetime-devlop.tistory.com/)