# b tree와 b+ tree

## b tree
데이터베이스와 파일 시스템에서 널리 사용되는 트리 자료구조의 일종으로, 이진 트리를 확장해 하나의 노드가 가질 수 있는 자식 노드의 최대 숫자가 2보다 큰 트리 구조

-> 하나의 노드에 여러 개의 자료가 배치되는 구조

## b+ tree
 B+tree는 B-tree의 확장개념으로, b-tree와 달리 모든 노드에 key, data가 있지 않으며, leaf 노드에만 key, data가 있다. 그리고 leaf 노드끼리는 연결리스트로 연결되어 있다. 

 <img width="834" alt="image" src="https://user-images.githubusercontent.com/76643037/201327659-d59477e0-b382-4538-8a7b-c49053ef2bd0.png">

 출처 : https://seunggi92.tistory.com/39
 