### 게시판
###  테이블 생성  
`````````````````````````````````````
게시판
create table board(
	no number primary key,
	writer varchar2(20) not null, --글 작성
 passwd varchar2(20) not null, -- 비밀 번호
	subject varchar2(100) not null,-- 제목
	content varchar2(1000) not null,-- 내용
	reg_date timestamp );

select*from tab; --테이블 목록 (Alt+x) 확인
select*from seq; --시퀸스 목록  (Alt+x) 확인
select*from bdard; --데이터 검색 (Alt+x) 확인

* 테이블 생성 할때  반드시 primary을 설정을 해야한다.
게시판
no number primary key
회원가입
no ID primary key
  `````````````````````````````````````
* 테이브러이 생성 되었는지 확인: Alt+x 로 확인 

* 테이블 생성 할때  반드시 primary을 설정을 해야한다.  
* primary key는 중복이 되면 안되어,
* where 조건절을 사용이된다. 
* 문자 데이터 = varchar2 
* 숫자 데이터 = namber
* 날짜 = date 

#### insetr  작성

````````````````````````````java
package p2022_07_18;

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;

public class InsertBoard {

public static void main(String[] args) {
		// TODO Auto-generated method stub
 
Connection con = null; 
PreparedStatement pstmt =null; 결과 값 
	
	String driver ="oracle.jdbc.driver.OracleDriver";
	String url= "jdbc:oracle:thin:@localhost:1521:xe";
	
	try {
	Class.forName(driver); // 드라이버 로딩 
	con= DriverManager.getConnection(url, "scott", "tiger");
        // 여기까지 DB연동 할때 공통 작업 		
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); // 입력 객체  
	
System.out.print("작성자명을 입력하세요?"); // 컬럼 명와 일치 하게 작성 
String writer =br.readLine();
System.out.print("비밀번호를 입력하세요?");
String passwd= br.readLine();
System.out.print("제목을 입력하세요?");
String subject= br.readLine();
System.out.print("내용을 입력하세요?");
String content= br.readLine();
	
	// SQL 문법 
	String sql= "insert into board ";
	       sql+="values(board_seq.nextval,?,?,?,?,sysdate)";
// 넘버 숫자 출력해서 borard_seq.nextval 저장 
pstmt =con.prepareStatement(sql);	// 실행문: pstmt객체 설정 
pstmt.setString(1,writer); // setString (넘버,컬럼)
pstmt.setString(2,passwd); // 
pstmt.setString(3,subject); // 
pstmt.setString(4,content); // 
int result= pstmt.executeUpdate();//SQL문 실행 코드 (executeUpdate)
if(result==1) {
		System.out.println("글작성 성공");
	}else {
		System.out.println("글작성 실패");
	}
	
	}catch(Exception e) {
		e.printStackTrace();// 예외발생 파악 
	// 작성글 닫는다. 
	}finally {
		try {
			if(pstmt !=null) pstmt.close();
			if(con != null)pstmt.close();
		}catch(Exception e) {
			e.printStackTrace();
		}
	}
		
	}

}
```````````````````````````````````````````````````````
#### Selet 검색 확인 
```````````````````````````````````````````````````java
package p2022_07_18;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.Timestamp;
import java.text.SimpleDateFormat;

public class SelectBoard {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

     Connection con =null;
     PreparedStatement pstmt = null;
     ResultSet rs01 =null; // 검색 결과 관리
     ResultSet rs02 =null;      
     int conut =0; //총 데이터 갯수
     
String driver ="oracle.jdbc.driver.OracleDriver";
String url= "jdbc:oracle:thin:@localhost:1521:xe";
 	
try {
 	Class.forName(driver);
 	con= DriverManager.getConnection(url, "scott", "tiger");
 		
 	String sql="select count(*)from board"; // 그룹 함수 count(*) =총 데이터
 		
 	pstmt= con.prepareStatement(sql);
 		
 	rs01=pstmt.executeQuery(); //SQL문 실행
     if(rs01.next()) { //데이터 가져오는 역할
     conut=rs01.getInt(1);
  // conut=rs01.getInt("count(*)");
        }
System.out.println("총데이터 수:"+conut);
 		
System.out.println("번호\t작성자명\t비밀번호\t제목\t\t내용\t\t날짜");
System.out.println("=================================");
 		
sql= "select * from board order by no desc"; // 오림 차순 정렬 
 		
pstmt =con.prepareStatement(sql); 
 		
rs02= pstmt.executeQuery(); //SQL문 실행
 		// 날짜 타입 지정  출력할때 sd.format(ts))
SimpleDateFormat sd = new SimpleDateFormat("yyyy-mm-dd HH:mm:ss");
 		
while(rs02.next()) {
int no =rs02.getInt("no");
String writer =rs02.getString("writer");
String passwd =rs02.getString("passwd");
String subject =rs02.getString("subject");
String content =rs02.getString("content");
Timestamp ts = rs02.getTimestamp("reg_date");
 			
System.out.print(no+"\t"+writer+"\t"+passwd+"\t");
System.out.print(subject+"\t"+content+"\t"+sd.format(ts)); //출력
System.out.println();
 			
 		}
 			
 	}catch(Exception e) {
 	e.printStackTrace();
 			
 	}finally {
 	  try {
 		  if(rs01 != null) rs01.close();
 		  if(rs02 != null) rs02.close();
 		  if(pstmt!= null) pstmt.close();
 		  if(con  != null) con.close();
 	  }catch(Exception e) {
 		 e.printStackTrace();
 	  }
 	}
		
			
	}

}
``````````````````````````````````````````````````````````````````````
Update 수정 
````java
package p2022_07_18;

import java.io.BufferedReader;
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.Reader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;

public class UpdateBoard {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		
	Connection con=  null;
	PreparedStatement pstmt = null;
	
	 String driver ="oracle.jdbc.driver.OracleDriver";
	 String url= "jdbc:oracle:thin:@localhost:1521:xe";
		
	 try {
		 
		 Class.forName(driver);
		 con = DriverManager.getConnection(url, "scott", "tiger");
		 
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
System.out.print("수정할 글 번호를 입력 하세요?");
int no= Integer.parseInt(br.readLine()); // 형변환(문자 -->숫자) 
System.out.print("작성자명를 입력 하세요?");
String writer =br.readLine();
System.out.print("비밀번호를 입력 하세요?");
String passwd= br.readLine();
System.out.print("제목을 입력하세요?");
String subject= br.readLine();
System.out.print("내용을 입력하세요");
String content = br.readLine();
		
	String sql="update board set writer=?,passwd=?,subject=?,";
	sql+="content=? ,reg_date=sysdate where no=?";
	    
	pstmt = con.prepareStatement(sql);
		
	pstmt.setString(1, writer);
	pstmt.setString(2, passwd);
	pstmt.setString(3, subject);
	pstmt.setString(4, content);
	pstmt.setInt(5, no);
		
	int result =pstmt.executeUpdate();// SQL문 실행 
	if(result==1) {
			System.out.println("수정이 성공.");
		}else {
			System.out.println("수정이 실패.");
		}
	 }catch(Exception e) {
		 e.printStackTrace();
	 }finally {
	
		 try {
			 if(pstmt!= null)pstmt.close();
			 if(con!= null)con.close();
		 }catch(Exception e) {
			 e.printStackTrace();
		 }
	 
		 
	 }
				
	}

	}
`````
### Delete
``````````java
package p2022_07_18;

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;

public class DeleteBoard {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

  Connection con = null;
  PreparedStatement pstmt = null;
  
	 String driver ="oracle.jdbc.driver.OracleDriver";
	 String url= "jdbc:oracle:thin:@localhost:1521:xe";
	 
	try {
		 
	Class.forName(driver);
	con= DriverManager.getConnection(url, "scott", "tiger");
		
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		
	System.out.print("삭제할 글 번호 입력하세요");
		
	int no= Integer.parseInt(br.readLine()); 
		
	String sql= "delete from board where no = ?";
		
	  pstmt = con.prepareStatement(sql);
	   pstmt.setInt(1, no);
	    
	  int result = pstmt.executeUpdate(); // SQL실행
	  if(result==1) {
	    System.out.println("글 삭제 성공");
	 }else{
	    System.out.println("글 삭제 실패");
	  }
		
	 }catch(Exception e) {
		 
	 }finally {
		 
		 
		 try {
			 if(pstmt !=null)pstmt.close();
			 if(con !=null)con.close();
			 
		 }catch(Exception e) {
			 
			e.printStackTrace();									 
		
		 }
		 
	   }
  				
	 }

 }
``````````````````````````


