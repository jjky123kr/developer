# Java sql
* 1. 오라클 서비스 연결 방법   
 내pc 오른쪽 버튼 (관리) 서비스 및 응용 프로그램 후     
  Orcale ServiceXE, OrcalXETNSListener 실행 모드 되어 있어야 실행이 가능하다.   
  Orcale ServiceXE, OrcalXETNSListener 사용하지 않을때는 수동으로 사용할수 있다. 
* 2. 클라이언트 접속 방법: 명령 프롬프트 입력 
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





          
