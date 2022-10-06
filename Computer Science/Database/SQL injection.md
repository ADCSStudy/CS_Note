# SQL Injection
해커에 의해 조작된 SQL 쿼리문이 데이터베이스에 그대로 전달되어 비정상적 명령을 실행시키는 공격 기법

## 공격 방법
1. 인증 우회

    e.g.) 로그인을 할 때 input 창에 비밀번호를 치는 것과 동시에 다른 쿼리문을 날린다.

2. 데이터 노출

    e.g.) GET 방식으로 동작하는 URL 쿼리 스트링을 추가하여 공격

## 방어 방법
1. input을 받을 때 특수 문자 여부 확인
2. SQL 오류 발생 시, 에러 원인 감추기
3. prepared statement 사용

     ```python
    로그인 기능을 제공한다고 가정하자.

    Statement를 사용하면 아래와 같은 문법으로 작성하게 된다.
    String sql = "SELECT * FROM user WHERE id ="+id+" AND password="+password;

    사용자가 id에 1을 입력했다면 sql은 "SELECT * FROM user WHERE id=1 AND password="+password 가 된다.

    사용자가 id에 1이 아닌 "1 OR 1=1 --"을 입력했다고 가정하자. password에는 1을 입력했다고 가정하자.

    그러면 SQL문은 다음과 같이 된다.
    SELECT * FROM user WHERE id=1 OR 1=1 -- AND password=1;

    여기서 --은 주석이기 때문에 password 검증은 사라지고 모든 유저 정보가 전부 나온다.
    ```
    
    SELECT * FROM user WHERE id = ? AND password = ?;