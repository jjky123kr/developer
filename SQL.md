# Oracle SQL 
Oracle SQL Developer  실행  
1.계정 등록   
  system , scott , hr 등록한다.
2.

image.png
### 테이블 목록 확인
--2022.07.19(화)  

--테이블 목록 확인  
select * from tab;
select * from sys.tab;  

--DEPT : 부서 테이블  
--EMP  : 사원 테이블  
--BONUS  
--SALGRADE  

--DEPT 테이블 구조 확인 명령어   
describe dept;  
desc dept;  

DEPT 데이터 구조      
1.DEPTNO : 부서 번호  
2.DNAME: 이름  
3.LOC: 지역  

--EMP 데이터 검색   
select * from emp;  
--EMP 데이터 구조  
1.EMPNO =사원번호  
2.ENAME= 이름  
3.JOB= 직급  
4.MGR= 사상 사원번호  
5.HIREDATE: 입사일  
6.SAL:  급여  
7.COMM=  영업사원만 받는 돈  
8.DEPTNO=부서 번호    

`````````````````````````````````````
이름     널       유형           
------ -------- ------------ 
DEPTNO NOT NULL  NUMBER(2)    
DNAME            VARCHAR2(14) 
LOC              VARCHAR2(13) 

이름       널?       유형           
-------- -------- ------------ 
EMPNO    NOT NULL NUMBER(4)      정수값4자리
ENAME             VARCHAR2(10)    10바이트 저장
JOB               VARCHAR2(9)  
MGR               NUMBER(4)       사원 번호 4 
HIREDATE          DATE            날짜 (yyyy/mm/dd)
SAL               NUMBER(7,2)     숫자값 자료형 (전체 자리수 7자리, 소수점 자리2 )
COMM              NUMBER(7,2)     영업사원이 받는 돈
DEPTNO            NUMBER(2)       부서 번호2 
`````````````````````````````````````````






