# MySQL 
My SQL 8.0설치   
일반 계정 등록 
  
1. MySQL8.0 command Line Client 클릭 후 비밀번호 등록  
  
새로운 데이터 베이스 생성 (jsptest)  
mysql> create database jsptest;  
mysql> create user jspid@’%’ identified by ‘jsppass’ ;  
mysql> grant all privileges on jsptest.* to jspid@’%’ with grant option ;   
mysql> flush privileges ;   

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