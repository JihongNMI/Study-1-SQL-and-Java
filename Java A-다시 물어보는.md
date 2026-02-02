# 순서는 필드 생성자 메소드 (게터 세터 일반)

ㅇㅇ

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

# Book b2 = new Book("자바의 정석") 이걸 하면 바로 ...뭐가 되지?

b2(title) 은 "정석"이 아니고 b2.title이 '정석'인건가?

O
b2.title → "자바의 정석"

b2("자바의 정석") → 이런 건 존재하지 않음 ❌

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
