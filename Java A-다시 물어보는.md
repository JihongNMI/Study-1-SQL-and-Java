# 순서는 필드 생성자 메소드 (게터 세터 일반)
예시 코드

```
class Book {
    String title;   // 필드
    int pages;      // 필드

    public Book() { }              // 기본 생성자
    public Book(String title) {    // 매개변수 있는 생성자
        this.title = title;        // 필드에 값 저장
    } 
}

다음 호출
Book b1 = new Book(); // 2번 호출
Book b2 = new Book("자바의 정석"); // 3번 호출

값은
b1.title, b1.pages는 null 0
b2.title = "자바의 정석" b2.pages 는 0

```


# 생성자
void가 안되는건 알겟고 
```
public Book() { } // 2번
public Book(String title) // 3번 
{
this.title = title;
}

```

이 둘 다 생성자라는데 사실인가?

O
```
Book b1 = new Book();                 // 2번 호출
Book b2 = new Book("자바의 정석");     // 3번 호출
```

---

# 위에 예시에서 Book b2 = new Book("자바의 정석") 이걸 하면 바로 ...뭐가 되지?
**O : b2.title → "자바의 정석"**

b2(title) 은 "정석"이 아니고 b2.title이 '정석'인건가? b2("자바의 정석") → 이런 건 존재하지 않음 ❌

b2는 변수 이름, 뒤에 괄호 붙이면 문법 에러

---

# xyz
그럼 잠시만...... Book b2 = new Book("자바의 정석"); 했는데 

public Book(String title) { this.xyz = title } 

하면 b2.xyz 가 자바의 정석 이 되는건가?

O

맞아요, 거의 정확하지만 한 가지 조건이 있어요. 🔑

xyz가 Book 클래스 안에 필드로 선언되어 있어야 합니다.

그냥 생성자 안에서 this.xyz = title;만 쓰고 xyz를 선언 안 하면 컴파일 에러 납니다.

예시
```
class Book {
    String xyz;  // 필드로 선언 필수

    public Book(String title) {
        this.xyz = title;
    }
}

Book b2 = new Book("자바의 정석");
System.out.println(b2.xyz);  // 출력: 자바의 정석
```

✅ 이렇게 하면 b2.xyz가 "자바의 정석"이 됨.

# 필드가 메소드야?

아니요 😄 필드와 메서드는 완전히 다른 개념이에요.

| 구분   | 필드                | 메서드                      |
| ---- | ----------------- | ------------------------ |
| 무엇?  | 변수, 객체 상태 저장      | 함수, 객체 행동 정의             |
| 이름   | title, xyz, pages | printTitle(), getTitle() |
| 값/실행 | 값 가짐              | 호출 시 실행됨                 |
| 예    | `b2.title = "자바"` | `b2.printTitle();`       |


1️⃣ 필드(Field)

클래스 안에 있는 변수

객체의 상태(state)를 저장

```
class Book {
    String title;   // 필드
    int pages;      // 필드
}
```

title과 pages는 메서드 이름이 아니라 변수 이름

```
Book b1 = new Book();
b1.title = "자바";  // b1의 title

Book b2 = new Book();
b2.title = "파이썬"; // b2의 title
```

2️⃣ 메서드(Method)

클래스 안에 정의된 함수

객체가 수행할 동작을 정의

```
class Book {
    void printTitle() {         // 메서드
        System.out.println(title);
    }
}
```

printTitle()은 메서드 이름

객체의 동작(행동)을 수행

---



