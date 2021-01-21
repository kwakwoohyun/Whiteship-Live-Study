# 5주차 과제: 클래스

## > 목표 :
#### 자바의 Class에 대해 학습하세요.
## > 학습할것 :
- 클래스 정의하는 방법
- 객체 만드는 방법 (new 키워드 이해하기)
- 메소드 정의하는 방법
- 생성자 정의하는 방법
- this 키워드 이해하기

### > 과제 (옵션)
- 과제 0. int 값을 가지고 있는 이진 트리를 나타내는 Node 라는 클래스를 정의하세요.
    - int value, Node left, right를 가지고 있어야 합니다.
- 과제 1. BinrayTree라는 클래스를 정의하고 주어진 노드를 기준으로 출력하는 bfs(Node node)와 dfs(Node node) 메소드를 구현하세요.
    - DFS는 왼쪽, 루트, 오른쪽 순으로 순회하세요.

> 클래스와 객체

- 클래스
    - 클래스는 객체지향 프로그래밍(Object-oriented programming)에서 객체를 생성하기 위해 상태(state)와 행동(behavior)을 정의하는 일종의 설계도이다.
    - 클래스는 쉽게 설명하면 객체를 만들기 위한 틀이라고 말할 수 있다.
- 객체
    - 객체란 어플리케이션의 기능을 구현하기 위해 서로 협력하는 개별적인 실체로써 물리적일 수도 있고 개념적일 수도 있다.
    - 객체지향의 4대 특성(추상화, 캡슐화, 상속, 다형성)을 통해 프로그램 개발 및 유지보수를 더욱 쉽고 빠르게 할 수 있을 것이다.

- 클래스 정의
    - `필드(field)` : 필드는 해당 클래스 객체의 상태 속성을 나타내며, 멤버 변수라고도 불린다. 여기서 초기화하는 것을 필드 초기화 또는 명시적 초기화라고 한다.
        - `인스턴스 변수` : 이름에서 알 수 있듯이 인스턴스가 갖는 변수이다. 그렇기에 인스턴스를 생성할 때 만들어진다. 서로 독립적인 값을 갖으므로 heap 영역에 할당되고 gc(가비지컬렉션)에 의해 관리된다.
        - `클래스 변수` : 정적을 의미하는 static키워드가 인스턴스 변수 앞에 붙으면 클래스 변수이다. 해당 클래스에서 파생된 모든 인스턴스는 이 변수를 공유한다. 그렇기 때문에 heap 영역이 아닌 static 영역에 할당되고 gc(가비지컬렉션)의 관리를 받지 않는다. 또한 public 키워드까지 앞에 붙이면 전역 변수라 볼 수 있다.
    - `메서드(method)` : 메서드는 해당 객체의 행동을 나타내며, 보통 필드의 값을 조정하는데 쓰인다.
        - `인스턴스 메서드` : 인스턴스 변수와 연관된 작업을 하는 메서드이다. 인스턴스를 통해 호출할 수 있으므로 반드시 먼저 인스턴스를 생성해야 한다.
        - `클래스 메서드` : 정적 메서드라고도 한다. 일반적으로 인스턴스와 관계없는 메서드를 클래스 메서드로 정의한다.
    - `생성자(constructor)` : 생성자는 객체가 생성된 직후에 클래스의 객체를 초기화하는 데 사용되는 코드 블록이다. 메서드와 달리 리턴 타입이 없으며, 클래스엔 최소 한 개 이상의 생성자가 존재한다.
    - `초기화 블록(initializer)` : 초기화 블록 내에서는 조건문, 반복문 등을 사용해 명시적 초기화에선 불가능한 초기화를 수행할 수 있다.
        - `클래스 초기화 블록` : 클래스 변수 초기화에 쓰인다.
        - `인스턴스 초기화 블록` : 인스턴스 변수 초기화에 쓰인다.
    ```
    class Class {               // 클래스
        String constructor;
        String instanceVar;     // 인스턴스 변수
        static String classVar; // 클래스 변수

        static {                // 클래스 초기화 블록
            classVar = "Class Variable";
        }

        {                       // 인스턴스 초기화 블록
            instanceVar = "Instance Variable";
        }

        Class() {                // 생성자
            constructor = "Constructor";
        }

        void instanceMethod() {       // 인스턴스 메서드
            System.out.println(instanceVar);
        }

        static void classMethod() {   // 클래스 메서드
            System.out.println(classVar);
        }
    }
    ```
- 접근제어자 : 접근 제어자는 해당 클래스 또는 멤버를 정해진 범위에서만 접근할 수 있도록 통제하는 역할을 한다. 클래스는 `public`과 `default`밖에 쓸 수 없다. `default`는 아무것도 붙지 않은것을 말한다.
    - `public`
    - `protected`
    - `(default)`
    - `private`
    
    ![접근제어자](https://jeeneee.dev/static/f696bef2cc0494a8ba68c72411b52879/cad6c/access-modifier.png "출처 https://jeeneee.dev/java-live-study/week5-class/")
- 그외 
    - `static` : 변수, 메서드는 객체가 아닌 클래스에 속한다
    - `final` : 클래스 앞에 붙으면 해당 클래스는 상속될 수 없다. 변수 또는 메서드 앞에 붙으면 수정되거나 오버라이딩 될 수 없다.
    - `abstract` : 클래스 앞에 붙으면 추상 클래스가 되어 객체 생성이 불가하고, 접근을 위해선 상속받아야 한다. 변수 앞에 지정할 수 없다. 메서드 앞에 붙는 경우는 오직 추상 클래스 내에서의 메서드밖에 없으며 해당 메서드는 선언부만 존재하고 구현부는 상속한 클래스 내 메서드에 의해 구현되어야 한다.
    - `transient` : 변수 또는 메서드가 포함된 객체를 직렬화할 때 해당 내용은 무시된다.
    - `synchronized` : 메서드는 한 번에 하나의 쓰레드에 의해서만 접근 가능하다.
    - `volatile` : 해당 변수의 조작에 CPU 캐시가 쓰이지 않고 항상 메인 메모리로부터 읽힌다.

- 객체정의 
    - 인스턴스화 : 클래스 ----> 객체
    - 클래스에서 객체를 생성하려면 `new`키워드를 생성자 중 하나와 함께 사용하면 된다.
    - `new`키워드는 새 객체에 메모리를 할당하고 해당 메모리에 대한 참조값을 반환하여 클래스를 인스턴스화한다.
    - `클래스명 변수명 = new 클래스명();`
    - 일반적으로 객체가 메모리에 할당되면 인스턴스라 부른다.
    - 인스턴스 p1과 p2은 서로 다른 생성자에 의해 생성되었다.
    ```
    public class Point {
        private int x = 1;
        private int y = 2;

        Point() {}  // 기본 생성자

        Point(int x, int y) {
            setX(x);
            setY(y);
        }

        public int getX() {
            return x;
        }

        public int getY() {

            return y;
        }

        public void setX(int x) {
            this.x = x;
        }

        public void setY(int y) {
            this.y = y;
        }
    }
    ```
    ```
    public class PointMain {
        public static void main(String[] args) {
            Point p1 = new Point();
            Point p2 = new Point(3, 4);
            System.out.println("" + p1.getX() + ", " + p1.getY());  // 1, 2
            System.out.println("" + p2.getX() + ", " + p2.getY());  // 3, 4
            p1.setX(3);
            p1.setY(4);
            System.out.println("" + p1.getX() + ", " + p1.getY());  // 3, 4
        }
    }
    ```
    - 객체의 생성과정
        - new 연산자가 메모리 영역에 저장공간을 할당받는다.
        - 생성자가 객체를 초기화한다.
        - new연산자가 새로 생긴 객체의 주소를 변수에 저장한다.
        - 변수를 통해 해당 객체에 접근한다.

- 메소드
    - `메소드(method)`란 어떠한 특정 작업을 수행하기 위한 명령문의 집합이라 할 수 있다.
    - 메소드를 사용하는 이유는 중복되는 코드의 반복적인 프로그래밍을 피할 수 있기 때문이다.
    - 모듈화로 인해 코드의 가독성도 좋아진다.
    - 프로그램에 문제가 발생하거나 기능의 변경이 필요할 때도 손쉽게 유지보수를 할 수 있게 된다.

    ![메소드](https://jeeneee.dev/static/78df1fd61b3bd0e6ca321ac491b59b2c/21b4d/method-declaration.png "출처 https://jeeneee.dev/java-live-study/week5-class/")
    ```
    접근제어자 리턴타입 메소드명(파라미터){
        // 실행할코드
        return 리턴타입;
    } 
    ```
    ```
    public int getX() {
        return x;
    }

    public int getY() {
        return y;
    }

    public void setX(int x) {
        this.x = x;
    }

    public void setY(int y) {
        this.y = y;
    }
    ```
    - 접근 제어자 및 기타 제어자 - 해당 메서드에 접근할 수 있는 범위를 명시하거나 위에서 언급했듯이 부가적인 의미를 부여한다.
    - 반환 타입 - 메서드가 모든 작업을 수행한 뒤에 반환할 타입을 명시한다.
    - 메서드 이름 - 메서드명은 동사여야 하고 lowerCamelCase를 따르며 뜻이 명확해야 한다. 위의 메서드는 getter/setter 메서드이다.
    - 매개변수 리스트 - 메서드에서 사용할 매개변수들을 명시한다.
    - 메서드 시그니처 - 컴파일러는 메서드 시그니처를 보고 오버로딩(overloading)을 구별한다. 물론 리스트의 순서도 동일해야 한다.

- 생성자
    - 객체를 생성할 때 항상 실행되는 것으로, 객체를 초기화해주기 위해 맨 처음 실행되는 메소드이다.
    - 반환값이 없는 메소드는 생성자가 유일하다.
    - 생성자는 인스턴스를 생성해주는 역할을 하는 특수한 메소드라고 할 수 있다.
    - 반환값이 없기 때문에 `return`도 사용하지 않고, 반환 값 타입을 메소드 정의 포함시키지도 않는다.
    - 클래스에는 반드시 생성자가 존재해야 한다.
    - 인스턴스 생성시 딱 한번 호출 된다.
    - 인스턴스 변수의 초기화가 목적이다.
    - 클래 이름과 동일한 이름을 가진 메소드이다.
    - 반환형이 존재하지 않는다. 즉 return이 없다.
    - class에 생성자를 정의해주지 않아도 객체를 선언할 수 있다. => 정의해주지 않으면 detault로 생성자가 정의된다.
    ```
    Point() {}  // 기본 생성자

    Point(int x, int y) {
        setX(x);
        setY(y);
    }
    ```
    - 생성자를 명시하지 않으면 컴파일러가 자동으로 기본 생성자를 생성한다. 하지만 기본 생성자가 아닌 다른 형태의 생성자만 명시했다면 기본 생성자는 컴파일시에 생성되지 않는다.

- `this` 키워드
    - `this` 키워드는 인스턴스 자신을 가르킨다.
    - `this` 를 사용함으로써 지역변수 `x`, `y`와 구분할 수 있다
    - 클래스 메서드에서는 `this` 를 쓸 수 없다. 왜냐하면 인스턴스가 생성되지 않았을 수도 있기 때문이다.
    - `this()` 는 해당 클래스 생성자를 호출할 수 있다. 그렇기 때문에 생성자를 재사용하는 데 쓰인다.
    - 사용은 총 3가지 형태로 사용되며, 대부분 호출한 객체를 명확히 하기위해 사용된다.

        __1. 클래스의 속성과 매개변수의 이름이 같을 때__
        ```
        public Class Test{
            int a;
            
            public void Test(int a){
                    this.a = a;
            }
        }
        ```
        __2. 오버로딩된 다른 생성자를 호출할 때__

            주의할 점은 this()는 반드시 생성자의 첫번째 문장에 사용되어야 한다.
        ```
        public Class Test{
            int a;
            int b;

            public void Test(){
                this(null,null);
            }

            public void Test(int a){
                this(a, null);
            }

            public void Test(int b){
                this(null, b);
            }

            public void Test(int a , int b){
                    this.a = a;
                    this.b = b;
            }
        }
        ```
        __3. 객체 자신의 참조값을 전달하고 싶을때__
        ```
        public Class Test{
            int a;
            public Test(int a){
                    this.a = a;
            }
                
            public Test getTest(){
                    return this;
            }
        }
        ```
- `super` 키워드
    - super의 경우 this와는 다르게 자식클래스가 부모클래스로부터 상속받은 멤버로를 사용하고자 할때 사용된다.
    - super를 사용하면 부모클래스에 선언된 속성 값을 가져올 수 있습니다.
    - super() 키워드는 this()와 마찬가지로 생성자를 호출하는 함수로, 자기자신이 아닌 부모클래스의 생성자를 호출한다.
    ```
    class Parent{
        int a = 10;
        }

    class Child extends Parent{
        int a = 20;
            
        void childMethod(){
            System.out.println(a);         //20
            System.out.println(this.a);     //20
            System.out.println(super.a);   //10
        }
    }
    ```
