# java.io.*(BufferedReader,FileReader,FileWriter,File)
* 자바의 기본적인 데이터 입출력(IO: Input/Output) API 제공
* 바이트 기반 스트림과 문자 기반 스트림
* 예외 처리를 해야 한다. try ~catch 

### 바이트 기반 스트림
* 바이트 기반 입력 스트림의 최상위 클래스로 추상 클래스
### 문자 기반 입력 스트림의 최상위 클래스로 추상 클래스
* Reader  
문자 기반 입력 스트림의 최상위 클래스로 추상 클래스
* Writer  
문자 기반 출력 스트림의 최상위 클래스로 추상 클래스




 * import  java.io.*;

#### o 스트림(Stream) : 데이터의 흐름
```````````````java
Stream - Byte Stream           	         - 입력 (InputStream)
          (1Byte 단위로 데이터를
          전송하는 스트림)                 -출력 (OutputStream)


         Text Stream                     -  입력 (Reader)
         (2Byte 단위로 데이터를
          전송하는 스트림)                -   출력 (Writer)
```````````````````````
#### o Byte Stream에 관련된 클래스(1Byte 입.출력 처리)
````````````````java

  InputStream  - FileInputStream
  (입력)         FilterInputStream      -  BufferedInputStream
	         DataInputStream  		       	           	   
                 bjectInputStream

  
  OutputStream - FileOutputStream
  (출력)         FilterOutputStream       -  BufferedOutputStrea   DataOutputStream
	         PrintStream
	         ObjectOutputStream
``````````````````````````````````
#### o Text Stream에 관련된 클래스(2Byte 입.출력 처리)
````````````````````````````java
Reader -     BufferedReader
  (입력)     InputStreamReader - FileReader

  Writer -   BufferedWriter
  (출력)     OutputStreamWriter - FileWriter
             PrintWriter
`````````````````````````````````````````````
### BufferedReader : 1바이트2바이트 가리지 않고, 사용자 입력을 한줄로 출력이 가능하다. (키보드 입력 할때 )

``````````````````````````````````````````
예문1.
package p2022_07_12;

import java.io.*;

public class BufferedReaderTest {
    public static void main( String[] args ) {
		
	InputStream is = System.in;
	InputStreamReader isr = new InputStreamReader( is );// InputStreamReader생성자 (is )
	BufferedReader br = new BufferedReader( isr ); // 객체 생성(BufferedReader)
/*
BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); // 
*/
	System.out.print( "Input Data : " );
	//예외처리 try~ catch 	
	try {//입력한 한줄을 모두읽음.
	    String inputString = br.readLine();// 결과를 돌려주는 String 형이다. (예외를 발생시킨다.)
	    System.out.println();              
	    System.out.println("Output String = " + inputString );	//readLine()은 String형이다.    
	} catch ( IOException io ) {
	    System.out.println( io.getMessage() );
	}
    }//main() end
}
``````````````````````````````````````````````````
#### 예문 응용문제
`````````````````
package p2022_07_12;

import java.io.BufferedReader;
import java.io.InputStreamReader;

public class BufferedReaderEx {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
	// 키보드로 구구단 1개 단을 입력 받아서, 구구단 1개 출력하는 프로그램 작성?
		
		System.out.println("한 단을 입력하세요");
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
			
			
	try {
		 String input = br.readLine();//String input=5; 예외처리 

         int dan = Integer.parseInt(input); // int dan =5; 
		  
         for(int i=1; i<=9; i++) {
		  System.out.println(dan+"*"+i+"="+dan*i);
         }	
		}catch(Exception e) {
		 System.out.println("숫자만 입력하세요");
		
		}
	    }	

	}
``````````````````````````````````````````````````````````````
### FileInputStream: 
##### 1.예문  FileInputStream
``````````````````````````````````````java
package p2022_07_12;

import java.io.*;

public class FileInputStreamTest {
    public static void main( String[] args ) {
 // 파일을 읽어오기 위해서 ,   	
// 입력을 받아들이는 변수 선언
	int inputValue = 0; 
	
	// FileInputStream 객체 선언
	FileInputStream file = null;
		
	try {
//FileInputStream 1바이트 한글자만 입력을 받는다. 
	    // "read.txt"와 InputStream 형성  try~catch 안에 쓴다. 
	    file = new FileInputStream( "read.txt" );	// 지정된 위치에 파일이 없을 경우 예외처리(상대결로) 
	    file = new FileInputStream( "C:\\Intel/read.txt" );	// 지정된 위치에 파일이 없을 경우 예외처리 (절대결로)
			
	    // file의 끝을 만날 때까지 데이터를 읽어 들임
		// read() 메소드는 File에서 한 byte씩 데이터를 읽어옴.
		// 읽어온 데이터를 int로 변환해서 리턴,파일의 끝을 
		// 만나면 -1을 반환함.
	    while(( inputValue = file.read() ) != -1 ) { //한글자씩 읽어보는 것 
			System.out.print(( char )inputValue );
	    }
	} catch ( Exception e ) {
	    System.out.println( e.toString() );
	}

	// stream을 형성한 file을 닫음
	try {
	    file.close();
	} catch ( IOException io ) {
	    System.out.println( io.toString() );
	}
    }//main() end
}
//읽어오는 경우는 2가지 : 상대경로, 절대 경로 로 지정하여 읽어온다. 
// 자바 프로젝트에 넣어야지 읽을수 있고, 같은 패키지에 넣으면 읽을 수 가 없다. (상대결로)
// c드라이브에 폴더에 넣어서 읽어온다. 
//한 글자 씩 읽어와서, 10 진수 아스키코드로 저장한다. (InputValue)그다음에 형변환 ((char) inputvalue)변환 
//더이상 읽어올 글자가 없을면 -1을 리턴을 한다. != -1 While문을 바쪄나온다. 

````````````````````````````````````````````````````````````````
### 예문2.FileReader
* 2바이트 문자를 데이터를 읽어온다. 
````````````````````````````````````````````````java
package p2022_07_12;
// 2바이트 문자 입력 스트림, inputValue--> 유니코드로 변환 
import java.io.*;

public class FileReaderTest {
    public static void main( String[] args ) {
		
	// FileReader 객체 선언
	FileReader file = null;
	int inputValue = 0; 
		
	try {
	    // "data.txt" File과 stream 형성
	    file = new FileReader( "data.txt" );// 예외처리 , 객체생성에 읽어올 파일명 

	    // file의 끝을 만날 때까지 데이터를 읽어 들임
	    while(( inputValue = file.read() ) != -1 ) {
			System.out.print(( char )inputValue );// 유니코드를 문자로 변환 (char)
	    }


	    // stream을 닫음
//	    file.close();
	    
	} catch ( Exception e ) {
	    System.out.println( e.toString() );
	}finally {   
		try {
			
			if(file !=null) file.close();
		}catch(Exception e){}

	}
    }//main() end
}
//FileReader 객체 생성이 되면  파일을 닫아야한다. finally은 초기값이 null 값이 있으면, 닫을 수 없다. 그래서 예외처리를 해야 한다.
//FileReader 2바이트 문자 입력도 읽어온다. 
`````````````````````````````````````````````````````````
## FileWriter 출력을 만들어서, 파일로 저장한다. 
`````````````````````````````````java
package p2022_07_12;

import java.io.*;

public class FileOutputStreamTest {
    public static void main( String[] args ) {
    	
	try {
		// * 첫째 인수로 지정된 파일 객체에서 읽어서 
		// 둘째 인수로 지정된 파일 객체에 출력함
		// (즉, 동일한 파일이 생성됨)
	    // File에서 데이터를 읽어오는 FileInputStream 객체 생성	    
	    FileInputStream fis = new FileInputStream( "read.txt" );

	    // File에 데이터를 전송하기 위한 FileOutputStream 객체 생성
	    FileOutputStream fos = new FileOutputStream( "read1.txt" );
//	    FileOutputStream fos = new FileOutputStream( "C:\\Intel/read1.txt" );
//  FileOutputStream 객체은 전송받은 파일을 저장한다.(상대경로): 자바프로젝트  "read.txt"
//  FileOutputStream 객체은 전송받은 파일을 저장한다.(절대경로):c드라이브 intel 폴더에 저장 "C:\\Intel/read1.txt"
	    
	    	    
	    int input = 0;		
		
	    // File에 저장된 모든 데이터를 스트림을 통해 
		// 읽어 들여 File에 저장
		// 파일의 내용을 끝까지 다 읽으면 -1이 반환됨.
	    while(( input = fis.read() ) != -1 ) {
			System.out.print( (char)input ); //화면에 출력 부분
			fos.write( input ); // 다른 파일에 쓰는 부분 ,자동으로 문자형태로 저장이된다.
	    }

	    // FileInputStream, FileOutputStream을 해제	   
	    fos.close();
	    fis.close();  // 파일을 닫지 않는다면, 파일이 저장이 되지 않는다. 
	    
	} catch( Exception e ) {
	    System.out.println( e.getMessage() );	    
	}
    }//main() end
}
``````````````````````````````````````
## 예문2.  FileReader , FileWriter
``````````````````````````````````````````````````java
package p2022_07_12;

import java.io.*;

public class FileWriterTest {
    public static void main( String[] args ) {
    	
    	FileReader fr= null;
    	FileWriter fw= null;
    	
	try {
	    // 명령행 첫번째 인수로 들어오는 값을
	    //  인수로 받아 들여 FileReader 객체 생성
	   fr = new FileReader( "data.txt" );  //예외처리해야한다. 생성자 명은 : 파일명

	    // 명령행 두번째 인수를  
	    //  생성자의 argument로 받아 들여 FileWriter 객체 생성
	   fw = new FileWriter( "data1.txt" ); // 예외처리해야한다. 생성자 명: 파일명

	    int input = 0;

	    // File에 저장된 모든 데이터를 스트림을 통해 
 	    // 읽어 들여 다른File에 저장
	    while(( input = fr.read() ) != -1 ) {
			System.out.print( (char)input ); //화면에 출력 부분
			fw.write( input ); // 다른 파일에 쓰는 부분
	    }
		
	    // FileInputStream, FileOutputStream을 해제	    
//	    fr.close();
//	    fw.close();
        } catch ( IOException io ) {
			System.out.println( io );
	  
     }  finally{
    	 try{ if(fr!=null)fr.close();}catch(Exception e) {}
    	 try{ if(fw!=null)fw.close();}catch(Exception e) {}
    
     }
	
    }//main() end

}
		


































