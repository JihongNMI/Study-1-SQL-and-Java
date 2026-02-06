# 발단은 람다식

요약하자면 
1. Adder myAdder = new Adder(); // myAdder라는 객체를 Adder 클래스를 통해서 만든다. 이 안에는 .add같은 더해주는 메소드가 있다. 그건 public int add(int a, int b)로 정의해놓은 것이다.
2. Adder myAdder = new Adder() { }; // myAdder라는 객체를 Adder 클래스를 통해서 만든다. 그리고 그 자리에서 같은 add를 @Override를 통해서 덮어씌워서, 임시로 메소드를 수정한다. 익명클래스라는 방법을 사용한다.

---

그럼요! 방금 우리가 이야기한 **"기본형"**과 **"개조형(익명 클래스)"**의 차이를 한눈에 볼 수 있도록 전체 코드를 짜드릴게요.

이 코드를 실행해 본다고 상상하면서 흐름을 따라와 보세요.

---

### 1. 설계도 만들기 (Adder.java)

먼저 기본이 되는 `Adder` 클래스가 있어야겠죠?

```java
class Adder {
    // 기본적으로 두 수를 더해주는 메서드
    public int add(int a, int b) {
        return a + b;
    }
}

```

---

### 2. 실제 사용하기 (Main.java)

이제 메인 코드에서 두 가지 방식으로 객체를 만들어 비교해 보겠습니다.

```java
public class Main {
    public static void main(String[] args) {
        
        // 1번: 일반적인 객체 생성 (기존 설계도 그대로!)
        Adder normalAdder = new Adder();
        System.out.println("기본 더하기: " + normalAdder.add(10, 20)); 
        // 결과: 30 (10 + 20)

        // -------------------------------------------------------

        // 2번: 익명 클래스로 객체 생성 (만들면서 메서드 개조!)
        Adder bonusAdder = new Adder() {
            @Override
            public int add(int a, int b) {
                // 기본 더하기에 보너스 500을 더해주는 특수 개조!
                return a + b + 500;
            }
        }; 
        
        System.out.println("개조된 더하기: " + bonusAdder.add(10, 20));
        // 결과: 530 (10 + 20 + 500)
    }
}

```

---
