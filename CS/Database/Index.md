# Index(인덱스)
목적 : RDBMS에서 검색 속도를 높이기 위한 기술
- 테이블의 컬럼을 색인(Index)화 한다
- 데이터베이스 안의 레코드를 처음부터 풀스캔하지 않고, B + Tree로 구성된 구조에서 Index 파일 검색으로 속도를 향상시키는 기술

### 파일 구성
- FRM : 테이블 구조 저장 파일
- MYD : 실제 데이터 파일
- MYI : Index 정보 파일(Index 사용 시 생성)

사용자가 쿼리를 통해 Index를 사용하는 컬럼을 검색하게 되면, 이때 MYI 파일의 내용을 활용합니다.

### 단점
- Index 생성 시, .mdb 파일의 크기가 증가
- 한 페이지를 동시에 수정할 수 있는 병행성이 줄어듬
- 인덱스 된 Field 에서 Data를 업데이트하거나, Record를 추가 또는 삭제시 성능이 떨어짐
- 데이터 변경 작업이 자주 일어나는 경우, Index를 재작성해야 하므로 성능에 영향을 미침

### 사용하면 좋은 경우
- WHERE 절에서 자주 사용되는 Column
- 외래키가 사용되는 Column
- JOIN에 자주 사용되는 Column

### 사용을 피해야 하는 경우
- Data 중복도가 높은 Column
- DML이 자주 일어나는 Column

### DML이 일어났을 때의 상황
1. INSERT
  - 기존 Block에 여유가 없을 때, 새로운 Data가 입력됨
  - 새로운 Block을 할당 받은 후, Key를 옮기는 작업을 수행
  - Index Split 작업 동안, 해당 Block의 Key 값에 대해서 DML이 블로킹 됨(대기 이벤트 발생)

2. DELETE
  - Table에서 Data가 DELETE 되는 경우 : Data가 지워지고, 다른 Data가 그 공간을 사용 가능
  - Index에서 Data가 DELETE 되는 경우 : Data가 지워지지 않고, 사용 안 됨 표시만 해둠
  ***-> Table의 Date 수와 Index의 Data 수가 다를 수 있음***
3. UPDATE
  - Talbe에서 UPDATE가 발생하면 Index는 UPDATE 할 수 없음
  - Index에서는 DELETE가 발생한 후, 새로운 작업의 INSERT 작업 / 2배의 작업이 소요됨
