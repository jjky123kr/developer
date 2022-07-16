
## 자바에서 SQL문 DB연동 예제1.
````````````````````````````````````````````````````````````````java
1. 데이터 테이블 만들기
create table customer( no number(4)  primary key, 
		       name varchar2(20),
		       email varchar2(20),
		       tel varchar2(20));

alter table customer add(address varchar2(50));

alter table customer add(reg_date timestamp);

create sequence customer_no_seq
	start with 1
	increment by 1;

					       

1. insert 입력
package p2022_07_15;
// 도스 콘솔 창에서 사용자 입력을 받아들이기 위해 BufferedReader 
import java.io.BufferedReader;  
import java.io.InputStreamReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement; // 실행 객체
import java.sql.ResultSet; // 검색 결과 객체 

class JDBC_Insert01 {
	public static void main(String[] args) {

		String driver = "oracle.jdbc.driver.OracleDriver";
		String url = "jdbc:oracle:thin:@localhost:1521:xe";

		Connection con = null;
		PreparedStatement pstmt = null; 

		//ResultSet rs = null;
		String sql;

		String name, email, tel, no;

		try {
			Class.forName(driver);
			con = DriverManager.getConnection(url, "scott", "tiger");

			// ---JDBC_Insert 추가된 내용-------
			// 테이블에 추가할 내용을 도스 콘솔 창에서 사용자의 입력을 받도록 한다.
			BufferedReader br = new BufferedReader(new InputStreamReader(
					System.in));

			System.out.println(" customer 테이블에 값 입력하기 .....");
			System.out.print(" 번호 입력: ");
			no = br.readLine();
			System.out.print(" 이름 입력: ");
			name = br.readLine(); // 테이블에 추가할 name 필드 값을 입력 받음
			System.out.print(" 이메일 입력: ");
			email = br.readLine(); // 테이블에 추가할 email 필드 값을 입력 받음
			System.out.print(" 전화번호 입력: ");
			tel = br.readLine(); // 테이블에 추가할 tel 필드 값을 입력 받음

			int ino = Integer.parseInt(no); // 자료형 변환 - 형변화 int 

			// INSERT 쿼리문을 작성
			sql = "INSERT into customer (no, name, email, tel) values (?, ?, ?, ?)"; 

			pstmt = con.prepareStatement(sql); // SQL 문 읽어온다. 
			
			pstmt.setInt(1, ino); // ((?),(컬럼);
			pstmt.setString(2, name);
			pstmt.setString(3, email);
			pstmt.setString(4, tel);
			
			int result= pstmt.executeUpdate();// SQL 실행 
			if(result == 1){
				System.out.println("데이터 입력 성공");
			}else{
				System.out.println("데이터 입력 실패");
			}

		} catch (Exception e) {
			System.out.println("데이터베이스 연결 실패!");
		} finally {
			try {
		//		if (rs != null)
		//			rs.close();
				if (pstmt != null)
					pstmt.close();
				if (con != null)
					con.close();
			} catch (Exception e) {
				System.out.println(e.getMessage());
			}
		}
	}
}

2. Select 출력 (저장된 데이터 )
package p2022_07_15;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

class JDBC_Select01 {
	public static void main(String[] args) {

		String driver = "oracle.jdbc.driver.OracleDriver";
		String url = "jdbc:oracle:thin:@localhost:1521:xe";

		Connection con = null;
		PreparedStatement pstmt = null;
		
		// ---JDBC_Select 추가된 내용 -------
		ResultSet rs = null;      // 검색 객체 1
		ResultSet rs01 = null;    // 검색 객체 2
		int no = 0;
		String name, email, tel; // 데이터베이스에서 얻어온 필드값 저장할 변수 선언
		String sql; // SQL문을 저장할 변수 선언
		int cnt=0;	// 총회원수 초기값
		
		try {
			Class.forName(driver);
			con = DriverManager.getConnection(url, "scott", "tiger");
//          총 회원 수:  count(*) 그룹 함수 
			String sql01="select count(*) from customer"; 
			pstmt = con.prepareStatement(sql01);
			rs01 = pstmt.executeQuery();
			if(rs01.next()){  // next()는 값을 가져온다. 
				cnt = rs01.getInt(1); 
		//		cnt = rs01.getInt("count(*)");
			}
			System.out.println("총회원수:"+cnt);
			
			// ---JDBC_Select 추가된 내용 -------
			sql = "SELECT * FROM customer";
			System.out.printf("번호 \t 이름 \t\t 이메일 \t\t 전화번호 \n");
			System.out.printf("-----------------------------------------------------------------\n");
			
			pstmt = con.prepareStatement(sql);
			rs = pstmt.executeQuery(); // 얻어진 레코드를 가져옴

			while (rs.next()) {  // 데어터가 여러개 일때 while 사용
				no = rs.getInt("no");// 컬럼 인덱스 번호 , 컴럼 명 으로 가져올 수 있다. 
				name = rs.getString("name");
				email = rs.getString("email");
				tel = rs.getString("tel");
				System.out.printf(" %d \t %s \t %s \t %s\n", no, name, email,
						tel);
			}
		} catch (Exception e) {
			System.out.println("데이터베이스 연결 실패!");
		} finally {
			try {// rs, stmt, con 객체를 close() 메서드를 호출해 해제
				if (rs != null)
					rs.close();
				if (pstmt != null)
					pstmt.close();
				if (con != null)
					con.close();
			} catch (Exception e) {
				System.out.println(e.getMessage());
			}
		}
	}
}
3.Update 수정 
package p2022_07_15;

import java.sql.*;
import java.io.*;  // 도스 콘솔 창에서 사용자 입력을 받아들이기 위해 BufferedReader 

class  JDBC_Update01{
public static void main(String[] args) {

  String driver = "oracle.jdbc.driver.OracleDriver";
  String url = "jdbc:oracle:thin:@localhost:1521:xe";

  Connection con = null; // 초기값 
  PreparedStatement pstmt =  null;

  String sql;
  String name, email, tel ;
  int ino;
  
     try{
      Class.forName(driver);
      con = DriverManager.getConnection(url, "scott", "tiger" );      

      //---JDBC_Insert 추가된 내용-------
      // 테이블에 추가할 내용을 도스 콘솔 창에서 사용자의 입력을 받도록 한다.
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      System.out.println(" customer 테이블에 값 갱신하기 .....");
      System.out.print("수정할 회원의 회원번호를 입력? ");
      ino = Integer.parseInt(br.readLine()); //형변환 
      
      System.out.print("변경할 이름을 입력:");
      name = br.readLine();            //테이블에 추가할 name 필드 값을 입력 받음
      System.out.print("변경할 이메일 입력: ");
      email = br.readLine();             //테이블에 추가할 email 필드 값을 입력 받음
      System.out.print("변경할 전화번호 입력: ");
      tel = br.readLine();               //테이블에 추가할 tel 필드 값을 입력 받음     

	  sql = "UPDATE customer SET name=?,email=?, tel=? where no =?";
	  pstmt = con.prepareStatement( sql ); //SQL문 읽어온다. 
	  pstmt.setString(1, name);// 자료형의 따라 메소드가 다르다. 
	  pstmt.setString(2, email);
	  pstmt.setString(3, tel);
	  pstmt.setInt(4, ino);
      int result=pstmt.executeUpdate(); 
      if(result==1){
    	  System.out.println("데이터 수정 성공");
      }else{
    	  System.out.println("데이터 수정 실패");
      }
	}
    catch(Exception e){
      System.out.println("데이터베이스 연결 실패!");
    }
    finally{
      try{
        if( pstmt != null ) pstmt.close();
        if( con != null )  con.close();
      }
      catch(Exception e){ 
        System.out.println( e.getMessage());
      }
    }
  }
} 
4.Delete 삭제 
package p2022_07_15;

import java.sql.*;
import java.io.*;  // 도스 콘솔 창에서 사용자 입력을 받아들이기 위해 BufferedReader 

class  JDBC_Delete01{
public static void main(String[] args) {

  String driver = "oracle.jdbc.driver.OracleDriver";
  String url = "jdbc:oracle:thin:@localhost:1521:xe";

  Connection con = null;
  PreparedStatement pstmt =  null;
  String sql;
  String name, email, tel ;
  int ino;
  
     try{
      Class.forName(driver);
      con = DriverManager.getConnection(url, "scott", "tiger" );      

      //---JDBC_Delete 변경된 내용-------
      // 테이블에 추가할 내용을 도스 콘솔 창에서 사용자의 입력을 받도록 한다.
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      System.out.println(" customer 테이블에서 레코드 삭제하기 .....");
      System.out.print("삭제할 회원의 회원번호를 입력하세요? ");
      ino = Integer.parseInt(br.readLine());     //테이블에서 삭제할 name 필드 값을 입력 받음
   
      // DELETE 쿼리문을 작성
	  sql = "DELETE FROM customer WHERE no = ?"; // 삭제 
	  pstmt = con.prepareStatement( sql );
	  pstmt.setInt(1, ino);	  
      int result=pstmt.executeUpdate() ;   
	  if(result==1){
		  System.out.println("회원 삭제 성공");
	  }else{
		  System.out.println("회원 삭제 실패");
	  }
      
	}catch(Exception e){
      System.out.println("데이터베이스 연결 실패!");
    }
    finally{
      try{
        if( pstmt != null ) pstmt.close();
        if( con != null )  con.close();
      }
      catch(Exception e){ 
        System.out.println( e.getMessage());
      }
    }
  }
} 
````````````````````````````````````````````````````````````````````````````
## SQL문 실행 Method
```````````````````````````````
SQL문			   Method
----------------------------------------------------------
select       -    ResultSet       executeQuery()


insert
update       -     int	       executeUpdate()
delete
```````````````````````````````````````````````````````
2. 예제 날짜
```````````````````````````````````````````````````````````````java
1.insert  입력
package p2022_07_15;

import java.io.BufferedReader;  // 도스 콘솔 창에서 사용자 입력을 받아들이기 위해 BufferedReader 
import java.io.InputStreamReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.Timestamp;

class  JDBC_Insert02{
public static void main(String[] args) {

  String driver = "oracle.jdbc.driver.OracleDriver";
  String url = "jdbc:oracle:thin:@localhost:1521:xe";	

  Connection con = null;
  PreparedStatement pstmt =  null;

 // ResultSet  rs   = null;
  String sql;

   String name, email, tel, no, address;
  
     try{
      Class.forName(driver);
      con = DriverManager.getConnection(url, "scott", "tiger" );      

      //---JDBC_Insert 추가된 내용-------
      // 테이블에 추가할 내용을 도스 콘솔 창에서 사용자의 입력을 받도록 한다.
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

      System.out.println(" customer 테이블에 값 입력하기 .....");
//      System.out.print(" 번호 입력: ");
//      no = br.readLine().trim();	  
      System.out.print(" 이름 입력: ");
      name = br.readLine().trim();            //테이블에 추가할 name 필드 값을 입력 받음
      System.out.print(" 이메일 입력: ");
      email = br.readLine().trim();             //테이블에 추가할 email 필드 값을 입력 받음
      System.out.print(" 전화번호 입력: ");
      tel = br.readLine().trim();               //테이블에 추가할 tel 필드 값을 입력 받음
      System.out.println("주소를 입력 하세요?");
      address = br.readLine().trim();
//	  int ino = Integer.parseInt(no);
      
	  Timestamp ts = new Timestamp(System.currentTimeMillis());//날짜 시간 Timestamp 객체 
	  
      // INSERT 쿼리문을 작성
	  sql = "INSERT into customer (no,name,email,tel,address,reg_date) "; 
	  sql+=" values (customer_no_seq.nextval, ?, ?, ?,?,?)";
//                   sequence 실행 법 (no은(?)을 사용하지 않는다. )
	  pstmt = con.prepareStatement( sql );
//	  pstmt.setInt(1, ino);
	  pstmt.setString(1, name);
	  pstmt.setString(2, email);
	  pstmt.setString(3, tel);
	  pstmt.setString(4, address);
	  pstmt.setTimestamp(5, ts);
	  int result=pstmt.executeUpdate();   
	  	if(result == 1){
			 System.out.println(" Data insert success!! ");
	  	}else{
			System.out.println(" Data insert failed ");
		}
    } catch(Exception e){
      System.out.println("데이터베이스 연결 실패!");
    } finally{
		try{
//			if( rs != null )   rs.close();        
			if( pstmt != null ) pstmt.close();
			if( con != null )  con.close();
		 } catch(Exception e){ 
			System.out.println( e.getMessage());
		}
    }
  }
} 
2. Select 저장된 데이터 확인 
package p2022_07_15;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

class  JDBC_Select02{
  public static void main(String[] args)  {

	String driver = "oracle.jdbc.driver.OracleDriver";
    String url = "jdbc:oracle:thin:@localhost:1521:xe";

    Connection con  = null;
    PreparedStatement pstmt =  null;
    //---JDBC_Select 추가된 내용 -------
    ResultSet  rs   = null;
	int no = 0; 
    String name="", email="", tel="", address="", ts="";  //데이터베이스에서 얻어온 필드값 저장할 변수 선언
    String sql;               //SQL문을 저장할 변수 선언

    try{
      Class.forName(driver);
      con = DriverManager.getConnection(url, "scott", "tiger" );
     
      //---JDBC_Select 추가된 내용 -------
      sql = "SELECT * FROM customer";
      System.out.printf("번호 \t 이름 \t\t 이메일 \t\t 전화번호 \t 주소\t 날짜\n");
      System.out.printf("-----------------------------------------------------------------\n");
	  pstmt = con.prepareStatement( sql );
      rs = pstmt.executeQuery();  //얻어진 레코드를 가져옴

      while( rs.next() ){
		 no = rs.getInt("no"); 
         name = rs.getString("name");  
         email = rs.getString("email");     
         tel   = rs.getString("tel"); 
         address = rs.getString("address");
         ts = rs.getTimestamp("reg_date").toString();
        System.out.printf(" %d \t %s \t %s \t %s\t %s\t %s\t  \n", no, name,email,tel,address,ts);
      } 
    }
    catch(Exception e){
      System.out.println("데이터베이스 연결 실패!");
    }
    finally{
      try{//rs, stmt, con 객체를 close() 메서드를 호출해 해제
        if( rs != null )      rs.close();        
        if( pstmt != null )    pstmt.close();
        if( con != null )     con.close();
      }
      catch(Exception e){
        System.out.println( e.getMessage( ));  
      }
    }
  }
}  

3.
package p2022_07_15;

import java.io.BufferedReader;  // 도스 콘솔 창에서 사용자 입력을 받아들이기 위해 BufferedReader 
import java.io.InputStreamReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.Timestamp;

class  JDBC_Update02{
public static void main(String[] args) {

  String driver = "oracle.jdbc.driver.OracleDriver";
  String url = "jdbc:oracle:thin:@localhost:1521:xe";

  Connection con = null;
  PreparedStatement pstmt =  null;

  String sql;
  int no;
  String name, email, tel, address ;
  
     try{
      Class.forName(driver);
      con = DriverManager.getConnection(url, "scott", "tiger" );      

      //---JDBC_Insert 추가된 내용-------
      // 테이블에 추가할 내용을 도스 콘솔 창에서 사용자의 입력을 받도록 한다.
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      System.out.println(" customer 테이블에 값 갱신하기 .....");
      System.out.println("번호를 입력 하세요?");
      no = Integer.parseInt(br.readLine());
      System.out.print("변경할 이름을 입력하세요: ");
      name = br.readLine();            //테이블에 추가할 name 필드 값을 입력 받음
      System.out.print("변경할 이메일 입력: ");
      email = br.readLine();             //테이블에 추가할 email 필드 값을 입력 받음
      System.out.print("변경할 전화번호 입력: ");
      tel = br.readLine();               //테이블에 추가할 tel 필드 값을 입력 받음     
      System.out.println("변경할 주소를 입력하세요?");
      address = br.readLine();
      Timestamp ts = new Timestamp(System.currentTimeMillis());
      
	  sql = "UPDATE customer SET name=?, email= ?, tel = ?, address = ?, reg_date= sysdate where  no = ?";
	  pstmt = con.prepareStatement( sql );
	  pstmt.setString(1, name);
	  pstmt.setString(2, email);
	  pstmt.setString(3, tel);
	  pstmt.setString(4, address);
//	  pstmt.setTimestamp(5, ts);
	  pstmt.setInt(5,no);
      int result=pstmt.executeUpdate() ; 
      	if(result == 1){
 		 System.out.println(" 데이터 수정 성공!! ");
       }else{
 		 System.out.println(" 데이터 수정 실패 ");
 	  }
	}
    catch(Exception e){
      System.out.println("데이터베이스 연결 실패!");
    }
    finally{
      try{
        if( pstmt != null ) pstmt.close();
        if( con != null )  con.close();
      }
      catch(Exception e){ 
        System.out.println( e.getMessage());
      }
    }
  }
} 
4.
package p2022_07_15;

import java.io.BufferedReader;  // 도스 콘솔 창에서 사용자 입력을 받아들이기 위해 BufferedReader 
import java.io.InputStreamReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;

class  JDBC_Delete02{
public static void main(String[] args) {

  String driver = "oracle.jdbc.driver.OracleDriver";
  String url = "jdbc:oracle:thin:@localhost:1521:xe";

  Connection con = null;
  PreparedStatement pstmt =  null;
  String sql;
  int no;
  String name, email, tel ;
  
     try{
      Class.forName(driver);
      con = DriverManager.getConnection(url, "scott", "tiger" );      

      //---JDBC_Delete 변경된 내용-------
      // 테이블에 추가할 내용을 도스 콘솔 창에서 사용자의 입력을 받도록 한다.
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      System.out.println(" customer 테이블에서 레코드 삭제하기 .....");
      System.out.print("삭제할 회원 번호를 입력하세요: ");
      no = Integer.parseInt(br.readLine());     //테이블에서 삭제할 name 필드 값을 입력 받음
   
      // DELETE 쿼리문을 작성
	  sql = "DELETE FROM customer WHERE no = ?";
	  
	  pstmt = con.prepareStatement( sql );
	  pstmt.setInt(1, no);	  
      int result=pstmt.executeUpdate() ;   
      if(result == 1){
  		 System.out.println(" 데이터 삭제 성공!! ");
        }else{
  		 System.out.println(" 데이터 삭제 실패 ");
  	  }
	}catch(Exception e){
      System.out.println("데이터베이스 연결 실패!");
    }
    finally{
      try{
        if( pstmt != null ) pstmt.close();
        if( con != null )  con.close();
      }
      catch(Exception e){ 
        System.out.println( e.getMessage());
      }
    }
  }
} 




































