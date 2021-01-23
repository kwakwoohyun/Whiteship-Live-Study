# 6주차 과제: 클래스

## > 목표 :
#### 자바의 상속에 대해 학습하세요.
## > 학습할것 :
- 자바 상속의 특징
- super 키워드
- 메소드 오버라이딩
- 다이나믹 메소드 디스패치 (Dynamic Method Dispatch)
- 추상 클래스
- final 키워드
- Object 클래스
-------------------
> 상속
- 상속이란 상위클래스에서 정의한 필드와 메서드를 하위클래스도 동일하게 사용할 수 있게 물려받는 것이다.
- 상속 받는 클래스 = 하위클래스 = 자식클래스 = 서브클래스
- 상속 해주는 클래스 = 상위클래스 = 부모클래스 = 슈퍼클래스 
```
class 자식클래스명 extends 부모클래스명 { 

}
```
- 자바에서 상속은 `extends` 라는 키워드를 통해 이루어진다.
- 코드를 재사용하기에 편하고 클래스 간 계층구조를 분류하고 관리하기 쉬워진다.

> 상속의 특징
1) 다중 상속 금지
```
class 자식클래스명 extends 부모클래스명1, 부모클래스명2{
    //컴파일 에러
}  
```
2) 최상위 클래스 `Object`
```
public class Main {
    public static void main(String[] args) {
        Object testClass = new TestClass(); //TestClass 는 Object의 서브클래스
    }
}
```
-------------------
> `super` 키워드

- `super` 키워드는 `자식클래스`가 `부모클래스`로부터 상속받은 멤버를 사용하고자 할때 사용된다.
- `부모클래스`의 멤버와 `자식클래스`의 멤버 이름이 같을 경우 `super` 키워드를 사용하여 구별할 수 있다.
- `super` 는 `부모클래스`의 참조변수라고 볼 수 있다.
- `super()` 를 사용하면 `부모클래스`의 생성자를 호출할 수 있다.
- `부모클래스`의 생성자에 인자가 없다면 `자식클래스`에서 `super()`를 작성하지 않아도 자동으로 컴파일시에 추가된다.
--------------
> 메소드 오버라이딩 (Method Overridding)

- `부모클래스`가 가지고있는 `메서드`를 `자식클래스`에서 새롭게 다른 로직으로 정의하고 싶을 때(새롭게 작성) 사용하는 문법이다.
- 상속관계에 있는 클래스간에 `같은 이름의 메서드`를 정의하는 문법을 `메서드 오버라이딩`이라고 한다.
- `오버라이딩 어노테이션`은 생략할 수도 있다.
```
public class A{
     public void print(){
           System.out.println("A");
     }
}

public class B extends A {
     
     //메소드 오버라이딩 - A를 상속받았으나 함수를 재정의
     @Override
     public void print(){
           System.out.println("B");
     }
}

public class Test{
      public static void main(String[] args){
             B b = new B();
             b.print();         //B를 출력 
      }
}
```




