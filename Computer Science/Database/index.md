# 인덱스

__RDBMS에서 검색 속도를 높이기 위한 기술__

Table의 Column을 색인화(따로 파일로 저장) </br>
-> Table을 full scan하지 않음 </br>
-> B tree 구조로 검색 속도 향상

Table을 형성하면 3개의 파일 생성됨</br>
1) FRM : 테이블 구조
2) MYD : 실제 데이터
3) MYI : Index 정보

(index를 사용하지 않는 경우 MYI 파일은 비어져 있음 </br>
index를 사용하면 MYI 파일의 내용을 검색함)

__단점__</br>
* Index 생성시, .mdb 파일 크기가 증가함
* 한 페이지를 동시에 수정할 수 있는 병행성이 줄어듬 ???
* 인덱스 된 Field에서 Data를 업데이트하거나, Record를 추가 또는 삭제시 성능이 떨어짐
* 데이터 변경 작업이 자주 일어나는 경우, Index를 재작성해야 하므로, 성능에 영향을 미침

__사용하면 좋은 경우__
1) Where 절에서 자주 사용되는 Column
2) 외래키가 사용되는 Column
3) Join에 자주 사용되는 Column

__Index 사용을 피해야 하는 경우__
1) Data 중복도가 높은 Column
2) DML(데이터 조작)이 자주 일어나는 Column


__INSERT__
기존 Block에 여유가 없을 때, 새로운 Data가 입력됨

-> 새로운 Block을 할당 받은 후, Key를 옮기는 작업을 수행 (**많은 양의 Redo가 기록**되고, 유발)

-> Index split 작업 동안, 해당 Block의 Key 값에 대해서 DML이 블로킹 됨... 대기 이벤트 발생


__DELETE__
[Table과 Index 상황 비교]
Table에서 data가 delete 되는 경우 : Data가 지워지고, 다른 Data가 그 공간을 사용 가능
Index에서 Data가 delete 되는 경우 : Data가 지워지지 않고, 사용 안 됨 표시만 해둠.
-> Table의 Data 수와 Index의 Data 수가 다를 수 있음.


__UPDATE__
Table에서 update가 발생하면 -> Index는 Update 할 수 없음.
Index에서는 Delete가 발생한 후, 새로운 작업의 Insert 작업 / 2배의 작업이 소요되어, 힘듦