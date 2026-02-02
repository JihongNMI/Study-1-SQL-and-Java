# List<BoardDTO> boardList = new Vector<>();

문장을 조금 더 다듬어보면
"**List<BoardDTO>**라는 인터페이스 규격(명찰)을 가진 변수에, new 명령어로 Vector라는 실제 구현체(객체)를 메모리에 생성하여, 그 주소값을 boardList에 대입한다."

---
# 좋아. List가 인터페이스고 Vector가 구현체인거지. 이건 자바에서 정의된 특별한 예시잖아. 다른 자바의 정의된 동일한 느낌의 예시는 없는거지?

"인터페이스(규격) = new 구현체(실제)" 패턴의 가장 대표적인 자바 코드들입니다.

ArrayList (가장 많이 쓰는 리스트): List<String> list = new ArrayList<>();

LinkedList (데이터 삽입/삭제가 빠른 리스트): List<String> list = new LinkedList<>();

HashMap (키-값 쌍으로 저장하는 사전): Map<String, Integer> map = new HashMap<>();

HashSet (중복을 허용하지 않는 주머니): Set<String> set = new HashSet<>();

TreeMap (넣으면 자동으로 정렬되는 사전): Map<String, String> map = new TreeMap<>();

방금 나열한 예시들은 데이터를 담는 '컬렉션(Collection)' 영역에서 가장 많이 쓰이는 것들이고, 자바의 다른 영역(파일 읽기, 네트워크, 데이터베이스 등)에서도 이 패턴은 계속 등장합니다.

몇 가지만 더 실무적인 예시로 나열해 볼게요.

파일/데이터 흐름: InputStream is = new FileInputStream("file.txt"); (데이터를 읽는 통로 규격 = 파일에서 읽는 도구)

날짜/시간: Temporal temp = LocalDate.now(); (시간 규격 = 오늘 날짜 실체)

데이터베이스 접속: Connection conn = DriverManager.getConnection(url); (DB 연결 규격 = 특정 DB용 연결 객체)

그래픽/창: Shape circle = new Ellipse2D.Double(); (도형 규격 = 실제 타원 객체)

💡 왜 얘네가 기본 이름으로 정의되어 있을까요?

만약 자바에 Connection이라는 공통 규격이 없었다면, 개발자들은 오라클 DB용 코드, MySQL용 코드를 다 따로 공부해야 했을 거예요.

하지만 자바가 **Connection이라는 공통 이름(규격)**을 미리 만들어둔 덕분에, 우리는 어떤 DB를 쓰든 똑같은 방법으로 코딩할 수 있게 된 거죠. (알맹이인 '구현체'만 갈아 끼우면 되니까요!)

✍️ 한 줄 정리

"네, 자바가 미리 정의해둔 표준 인터페이스들이며, 우리가 자바 개발을 할 때 가장 많이 마주하게 될 거물급 이름들입니다."
