# Java sql
* 1. 오라클 서비스 연결 방법   
  내pc 오른쪽 버튼 (관리) 서비스 및 응용 프로그램 후     
  Orcale ServiceXE, OrcalXETNSListener 실행 모드 되어 있어야 실행이 가능하다.   
  Orcale ServiceXE, OrcalXETNSListener 사용하지 않을때는 수동으로 사용할수 있다. 
## 2. 클라이언트 접속 방법: 명령 프롬프트 입력 
````````````````````````````````````````
c:\> sqlplus  scott/tiger 

c:\> sqlplus  system/oracle => 접속 
SQL> show user 
SQL> alter user scott account unlock;

SQL> connect scott/tiger   (계정전환)
SQL> show user
SQL> select * from tab; (테이블 목록출력)
SQL> quit; (종료)

c:\> sqlplus  scott/tiger

```````````````````````````
* 3. sql 명령어 저장소 : c드라이브-oraclexe- app- oracle- product-11.2.0->server-bin 장소 있다.
* 4. 오라클 계정 : SCOTT 실습 
```````````````````````````````````````````````````````
### 오라클 계정 활성화 방법 
scott계정 활성화

c:\> sqlplus scott/tiger
c:\> sqlplus system/oracle

SQL> @c:\scott.sql

SQL> alter user scott identified by tiger;

SQL> conn scott/tiger (scott계정으로 전환)

SQL> select * from tab; (테이블 목록)

SQL> quit; (종료)
`
### 데이터베이스 관리 시스템 DBMS
* 기업이 지속적으로 유지 관리해야 하는 데이터의 집합
* 방대한 양의 데이터를 편리하게 저장하고 효율적으로 관리하고 검색할 수 있는 환경을 제공해주는 시스템 소프트웨어
* 데이터를 공유하여 정보의 체계적인 활용을 가능하게 합니다.
* 응용 프로그램과 데이터베이스의 중재자로서 모든 응용 프로그램들이 데이터베이스를 공용할 수 있게끔 관리해 주는 소프트웨어 시스템입니다. 
### 관계형 데이터베이스 관리 시스템
* RDBMS: Relational DataBase Management System)은 가장 일반적인 형태의 DBMS 입니다.
* 오라클(Oracle), 사이베이스(Sybase), 인포믹스(Infomix), MYSQL, Acess, SQL Server
* 장점
* 작성과 이용이 비교적 쉽고 확장이 용이하다.
* 처음 데이터베이스를 만든 후 관련되는 응용 프로그램들을 변경하지 않고도, 새로운 데이터 항목을 데이터베이스에 추가할 수 있다.
* 관계형 데이터베이스 정보를 테이블 형태로 저장합니다.
* 테이블은 2차원 형태의 표처럼 볼 수 있도록 로두 와 칼럼 으로 구성합니다. 
* DEPT테이블은 4개의 로우와 3개의 칼럼(부서번호:DEPTNO, 부서이름:DNAME,지역:LOC으로 구성된 테이블 
## SQl과 SQL*plus의 개념
* SQL(Structured Query Language)
* 데이터베이스에 저장된 데이터를 조회, 입력, 수정 삭제하는 등의 조작이나, 테이블을 비롯한 다양한 객체(시퀀스. 인덱스 등)를 생성 및 제어하는 역할을 합니다. 
### SQL의 종류 명령문
`````````````````````````````````````````````````````````````````````
오라클 에서는 가장 먼저 할일은 CREATE를 테이블을 만들어야 한다. 
1.DDL: Data Ddfinition Language (데이터 정의어): 객체 생성 및 변경시 사용
명령문  
 CREATE(데이터베이스 생성) = 테이블 생성 
 ALTER(데이터베이스 변경)
 DROP(데이터베이스 삭제)
 RENAME(데이터베이스 객체이름 변경)
 TRUNCATE(데이터베이스 저장 공간 삭제)

DQL: Data Query Language 
명령문 :SELECT(데이터 검색시 사용) 

DML 데이터 조작 
명령문
INSERT(데이터 입력)
UPDATE(데이터 수정)
DELETE(데이터 삭제)
TCL:Transaction Control Language
(트랜잭션 처리어)
COMMIT(트랜잭션의 정상적인 종료처리)
ROLLBACK(트랜잭션 취소)
SAVEPOINT(트랜잭션내에 임시 저장점 설정)
DCL:Data Control Language
(데이터 제어어)![image]
GRANT(데이터베이스에 대한 일련의 권한 부여)
REVOKE(데이터베이스에 대한 일련의 권한 취소)
`````````````````````````````````````````````````````````````````````````````````````````
### DDL 명령어 
* 테이블 생성                       
 SQL> create table 테이블명 (컬럼명  데이터타입, 
		                           컬럼명  데이터타입, ......);

 SQL> create table member01(
	    id  varchar2(20),      
	    name  varchar2(20), 
	    address varchar2(50), 
	    phone  varchar2(20));
오라클은 자료형
1. 숫자 number, 문자 varchar, 날짜 :Data 
`
## DML명령어
``````````````````````````````````````````````````````
1. insert (데이터 입력)

  형식:  insert into 테이블명(컬럼1, 컬럼2,..) values(데이터1, 데이터2,...); 
// 원하는 컬럼을 선택적으로 할때, 
           insert into 테이블명 values(데이터1, 데이터2,...);
// 테이블에 만든 컬럼을 순서대로 만들때 
     1.insert into member01(id,name,address,phone) values('test','ahn','seoul','123-4567');
     2.insert into member01 values('toto','홍길동','인천시','111-1111');
     ex) insert into dept01(deptno, dname, loc)
            	values(10,'ACCOUNTING', 'NEW_YORK'); 
           insert into dept01(dname, loc, deptno)
            	values('RESEARCH', 'DALLAS', 20); 
           insert into dept01 values(30, 'SALES', 'CHICAGO');
           insert into dept01 values(40, 'OPERATIONS','BOSTON');
````````````````````````````````````````````````````````````````````````````````
### 2. update (데이터 수정)
``````````````````````````````````````````````````````````````````````````````
      형식: update 테이블명 set 컬럼1=수정할값1,
		          컬럼2=수정할값2,...
             where 조건절;
ex) update member01 set address='제주시' where id='toto'; 
```````````````````````````````````````````````````````````````````````````````````````````
### 3.수정 확인 : select*from member01 where id='toto';
``
### 4. delete (데이터 삭제)
  > 형식:  delete from 테이블명 where 조건절;
``
### 5. delete (데이터 삭제)
``````````````````````````````````````````````````````````````````````````
   형식:  delete from 테이블명 where 조건절;
   ex) delete from member01 where id='toto';
6.select* from member01;
````````````````````````````````````````````````````````````````````````````````````````````````````
### 자바와 오라클 연동
* JDBC Drive(ojdbc6.jar)   :  자바와 오라클 연결 시킨다.  
-> 자바가 설치한 곳에 넣는다. 


          
