---
title: "[DB] Sqlplus basic commands"
categories:
    - dev
tags:
    - dev
    - db
    - oracle
toc: true
---

cmd 창 여는 방법

시작>실행>cmd 엔터

윈도우키+R > cmd 엔터

명령프롬프트 상태에서 sys 계정으로 접속하는법

sqlplus "/as sysdba"

> **1. sqlplus 실행**

sqlplus sys/비번 as sysdba

-- sysdba는 관리자로 9버전 이후에 꼭 쓰도록 된듯

> **2. 현재 접속한 유저확인**

show user

> **3. 테스트 scott 계정**

scott/tiger

> **4. 스캇 계정 락 풀기**

-   스캇계정이 락 걸려있으므로 sys로 접속해서 락을 풀어줘야함

1.  sqlplus sys/비번 as sysdba : sys로 접속
    
2.  alter user scott identified by tiger account unlock; -- 스캇 계정의 락을 푼다.
    

> **5. 접속중 계정 변경**

conn sys/비번 as sysdba

> **6. 계정생성 : sys로 로그인 후**

create user 계정명 identified by 비번 default tablespace users;

create user insaman identified by zxcv default tablespace users;

> **7. 권한주기**

GRANT CONNECT, CREATE VIEW, RESOURCE TO INSAMAN;

> **8. 현재 계정의 테이블 확인**

SELECT * FROM TAB;

> **9. 테이블의 속성(열) 확인법**

DESC EMP;

> **10. 결과값에 문자열 붙이기**

SELECT '사원의 이름은:'||ENAME||'입니다.' AS "사원의 이름"

FROM EMP;

> **11. 화면 설정 (화면 짤릴때)**

SET LINESIZE 300;

SET PAGESIZE 200;

> **12. 화면 지우기**

cl scr -> clear screen

> **13. 언어(한글) 설정**

ALTER SESSION SET NLS_LANGUAGE=Korean;

> **14. 해당 칼럼에 대해 화면 출력 줄 설정**

COL EMPNO1 FOR A20;

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNjE4NTU5MjJdfQ==
-->