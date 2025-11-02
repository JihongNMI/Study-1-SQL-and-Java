# 1. 오징어 가격!
## 6900원 나누기 80g 곱하기 100은 8625원이 아니고 8620원?

결론1 : 1. 1.0을 쓴다, 2. CAST를 쓴다. 3. (안해봤지만)처음부터 가격도 REAL로 한다 근데 이건 INTEGER인 전제로 하는게 좋겠지

```
CREATE TABLE "FOOD6" (
	"날짜"	TEXT,
	"상품명"	TEXT,
	"가게"	TEXT,
	"제조업체"	TEXT,
	"가격"	INTEGER,
	"그램수"	INTEGER,
	"단위가격"	REAL GENERATED ALWAYS AS ( CAST("가격" AS REAL) / "그램수" * 100.0) STORED,
	"비고"	TEXT
);

INSERT INTO "FOOD6" ("날짜", "상품명", "가게", "제조업체", "가격", "그램수", "비고")
SELECT "날짜", "상품명", "가게", "제조업체", "가격", "그램수", "비고" 
FROM "FOOD";
```



```sql
CREATE TABLE "FOOD5" (
	"날짜"	TEXT,
	"상품명"	TEXT,
	"가게"	TEXT,
	"제조업체"	TEXT,
	"가격"	INTEGER,
	"그램수"	INTEGER,
	"단위가격"	REAL GENERATED ALWAYS AS ("가격" * 1.0 / "그램수" * 100.0) STORED,
	"비고"	TEXT
);

INSERT INTO "FOOD5" ("날짜", "상품명", "가게", "제조업체", "가격", "그램수", "비고")
SELECT "날짜", "상품명", "가게", "제조업체", "가격", "그램수", "비고" 
FROM "FOOD";
```

결론 2:아무 것도 없는 테이블에서 Generated Column(생성된 컬럼)으로 100G당 가격을 하려면 새로 만든다음에 기존 테이블에서 옮겨야 된다. 귀찮지만...

```
그럼 정리하자면

기존 GENERATED COLUMN의 수식 변경 : X

그냥 컬럼 추가 : O

새로운 GENERATED COLUMN의 생성 : X

기존 컬럼 삭제 : X
```

