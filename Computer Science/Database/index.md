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