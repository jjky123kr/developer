# MySQL 설치 

My SQL 8.0설치   
<https://www.mysql.com/downloads/>  
설치 과정에서 root 계정 비밀번호 등록 

설치 후 path 혼경 설정 
MySQL 설치 경로 까지 path 설정  
C:\Program Files\MySQL\MySQL Server 8.0\bin   
내PC – 오른마우스(속성) – 고급시스템 설정 – 고급Tab – 환경변수  
시스템 변수 path 편집 새로 만들기   
C:\Program Files\MySQL\MySQL Server 8.0\bin 등록 한다.   
일반 계정 등록  하는 법   
 1.MySQL8.0 command Line Client 클릭 후 비밀번호 등록   
 
 2 .데이터 베이스 일반 계정 생성 (jsptest)    

MySQL8.0 command Line Client 들어가서   
mysql> create database jsptest;      
MySQL 8 에서는 계정 생성과 DB권한 부여를 각각 수행해야 한다  
mysql> create user jspid@’%’ identified by ‘jsppass’ ;    
mysql> grant all privileges on jsptest.* to jspid@’%’ with grant   option ;     
mysql> flush privileges ;   

## 이클립스 와 MySQL  연결 해야 한다. 
드라이브 파일을 설치   
JDBC Driver download  
<https://dev.mysql.com/downloads/connector/j/>
 
드라이브 파일을 자바 에 설치한 곳에 저장


###  숫자형
int 
auto_incrment :
### 2.문자형
char  
varchar  
text  
### 3. 날짜, 시간형
date  
time  
datetime  
timestamp  

sysdate(); 

###  MySQL Workbench 사용
테이블 생성  
create table member(  
id varchar(20),  
name varchar(20),  
email varchar(20),    
address varchar(100);  
-- 테이블 목록 확인
show tables;

