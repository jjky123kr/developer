# 문자열 클래스 

# String 
* 문자열 리터럴 동일하다면 String 객체 공유
*new 연산자를 이용한 String 객체 생성
*    힙 영역에 새로운 String 객체 생성
*    String 객체를 생성한 후 번지 리턴

# String 클래스
* String 객체를 생성한 후에 메소드에 의해서 값의 변화가 일어나면 변경된 값을 힙 메모리 영역에 다시 저장 한다.

## ==: 참조하는 주소를 비교 
```
String str1 = "자바";
 String str2 =  new String("자바");
 String str3 =  new String("자바");

str1          ----->    자바
 
str2          ----->    자바

str3          ----->    자바


(Stack영역)            (Heap영역)


if(str1 == str2){ //주소값을 비교

}

1. 주소 값이 같다
	String str1="자바";
	String str2="자바";
		
	if(str1==str2) { //비교연사잔(==)로 잠조하는 주소를 비교
	System.out.println("같은주소");     //같은 주소
	}else {
        System.out.println("다른 주소");
		
	}
   
 2. 주소 값이 다르다.  
   String str3= new String("자바");
    String str4= new String("자바");

	if(str3==str4) { //비교연사잔(==)로 잠조하는 주소를 비교
		System.out.println("같은주소");     
	}else {
	System.out.println("다른 주소");   //다른 주소		
       }
```````````````````````````       
## equals():참조하는 값(데이터)을 비교  (많이 사용하다.)
   
      if(str1.equals(str2)) {     //참조하는 값(데이터)을 비교
		System.out.println("같은값");
	}else {
		System.out.println("다른값");
	}
		
	if(str3.equals(str4)) {     //참조하는 값(데이터)을 비교
		System.out.println("같은값");
	}else {
		System.out.println("다른값");
	}
	
    }


// 객체 배열 : 객체의 주소를 참조하는(저장하는)배열
		
		String[]strArray= new String[3];//객체 배열	
		strArray[0]="Java";
		strArray[1]="Java";
		strArray[2]=new String("Java");
		
		System.out.println(strArray[0]==strArray[1]);           //true
		System.out.println(strArray[0]==strArray[2]);           //  false
		System.out.println(strArray[0].equals(strArray[2]));    // true
		
		
	}
``
#  String + 가 연결이 한다.  주소값을이 연결 시킨다. 

package p2022_07_01;

public class ConnectString {
	
    public static void main( String[] args ) {
	// String 객체 선언
	String gemini = "gemini";
	String johnharu = "johnharu";      //geminijohnharu
		
	// 두 String 객체를 "+" 연산 수행  
	String tempString1 = gemini + johnharu;
	System.out.println( tempString1 );
	System.out.println( "gemini" + "johnharu" );  //geminijohnharu

	// String + 정수형
	String tempString2 = tempString1 + 100;
	System.out.println( tempString2 );           //geminijohnharu100
	
    }
}
       
`
###  StringBuffer 클래스 (시작 주소 값이 바뀌지 않는다.) 
````````````````````````````````````````````````````````````````
1. StringBuffer sb = new StringBuffer("자바");

sb1         ----->	   gemini  is beautiful1004

sb2         ----->

// sb1과 sb2는 같은 내용을 가리키고 있음
(Stack영역)	                 (Heap영역)

1.package p2022_07_01;

public class StringBufferTest {
public static void main( String[] args ) {

StringBuffer sb1 = new StringBuffer("gemini");    //생성자
System.out.println( "sb1.length() : " + sb1.length() );     
System.out.println( "sb1.capacity() : " + sb1.capacity());    

sb1.append( "A string buffer implements"+ 
				"a mutable sequence of characters");
System.out.println( "sb1.length() : " + sb1.length() );
System.out.println( "sb1.capacity() : " + sb1.capacity());

StringBuffer sb2 = new StringBuffer();          // 생성자  
System.out.println( "sb2.length() : " + sb2.length() );
System.out.println( "sb2.capacity() : " + sb2.capacity());
    }
}

// 문자를 저장하기 위한 힙메모리 크기 capacity 
// append 은 동적으로 크기를 늘려준다.   
// 
2. StringBuffer 
public class AppendStringBuffer {
    public static void main( String[] args ) {
		
	// StringBuffer 객체 생성
	StringBuffer sb1 = new StringBuffer( "gemini" );
	System.out.println( "sb1 = " + sb1 );

	// StringBuffer sb1에 문자열을 추가해 새로운 객체 생성
	StringBuffer sb2 = sb1.append( " is beautiful" );
	System.out.println( "sb2 = " + sb2 );
	System.out.println( "sb1 = " + sb1 );

	// 정수형 데이타 형을 추가
	System.out.println( sb1.append( 1004 ));   //sb1와 sb2 는 주소값이 같다. 
	System.out.println( "sb1 = " + sb1 );      // sb1 = gemini is beautiful1004
	System.out.println( "sb2 = " + sb2 );      // sb2 = gemini is beautiful1004

	String str = new String(sb1);              // StringBuffer를 String으로 변환
	System.out.println(str.toUpperCase());     //GEMINI IS BEAUTIFUL1004
 // string 클래스 중에  매개 변수가 StringBuffer 있어서 StringBuffer를 String으로 변환 가능하다. 
   

    if (sb1==sb2) {                  // 주소 비교
    	System.out.println("같은 주소");
    }else {
    	System.out.println("다른 주소");
    }
    
    }   
}
    sb1에 append는 새로운 공간을 만들지 않고, 기존에 있던거에 추가한다. 
   기존에 있던 추가 된 것을 sb2에 값에 리턴한다. (시작 주소값 바뀌지 않는다)
3.   
//Insert메소드 
public class InsertStringBuffer {
    public static void main( String[] args ) {
	StringBuffer sb1 = new  StringBuffer("gemini is beautiful" );
	System.out.println( sb1 );
// 인덱스 10번 위치에 very라는 문자를 삽입 
	sb1.insert( 10, "very" );
	System.out.println( sb1 );   // gemini is verybeautiful
// 인덱스 0번 위치에 1004를 삽입
	sb1.insert( 0, 1004 );
	System.out.println( sb1 );  // 1004gemini is verybeautiful
    }
}
 insert 지정된 삽입된 위치에 집어 넣는다.
``````````````````````````````````````````````````````````````````````````````````````
##  StringTokenizer 클래스
````````````````````````

`````````````````````````````````````````````````````````````````````````
##  touppercaes 
``````````````````````````````````````````````````````````````````````
package p2022_07_01;

//String 객체를 생성한 후에 메소드에 의해서 값의 변화가 일어나면
//변경된 값을 힙 메모리 영역에 다시 저장 한다.

//Garbage Collection 기능(쓰레기 수집 기능)
//재사용할수 없는 힙 메모리 영역의 데이터를  모아서 , 지워주는 기능
class StringTest01 {

  public static void main(String[] args) {
    String str1 = "Java Programming";
	str1.toUpperCase();                      //메서드 호출 후에도 ( toUpperCase: 모두 대문자를 바꿔주는 역할)
    
	System.out.println(str1);               //str1의 내용은 수정되지 않는다. 
    System.out.println(str1.toUpperCase());
//String 은 값의 변화가 일어나면 힙 메모리에 매번 변환된 값을 저장을 하다  
    String str2=str1.toUpperCase();          //메소드의 처리 결과를 str2에 저장
    System.out.println(str2); 
//  str 2 새로운 변수에 다시 값을 할당해야지 ,재사용이 가능하다. 
  }    
}  
// String 은 값의 변화가 일어나면 힙 메모리에 매번 변환된 값을 저장을 하다, 변경된 값을 재사용을 하지 못하면, 지워진다. 
// 재사용을 하지 못하는 값은 지우고,새로운 변수에 다시 값을 할당해야지 ,재사용이 가능하다. 
//

`````````````````````````````````````````````````````````````````````````````````````````````
## length, char    메소드 
* length은 문자의 길이를 구하는 역할
* char은 문자 한글자 추출하는 역할
````````````````````````````````````````````````````````````
package p2022_07_01;
public class FindBlankIndex {
    public static void main( String[] args ) {
		
	String message = "Java program creates many objects.";
                                                              message의 길이를 구함.(문자의 길이를 구하는(글자수)length)
	int len = message.length();

	System.out.println(len);  // len = 34;

	                                                        message 중에서 ' '을 찾음
	for( int i=0 ; i<len ; i++ ) {
	    char c = message.charAt( i );
		if( c == ' ' ) {       공백의 인덱스 번호를 구해서 출력
		    System.out.println( "index = " + i );
		}
	}//for end
    }
}
배열의 크기는(s).length은 속성 , String은 length(); 문자의 길이(띄어쓰기,"문자등도 같이 ) 
charAt은 문자 한글자 추출하는 역할 
```````````````````````````````````````````````````````````````````````````````````````````
## Indexof 특정 문자의 인덱스 번호
package p2022_07_01;

public class IndexOfTest {
	public static void main( String[] args ) {
	
	indexof(); 특정 문자의 인덱스 번호를 구한다. 
		
	String message = "Java program creates many objects.";
	                                         가장 먼저 나오는 a의 인덱스 번호 
	int index1 = message.indexOf( 'a' ); 
	                                         10진수 아스키코드 97 에 해당되는 (a)의 인덱스 번호를 구함 (97='a',65='A')
	int index2 = message.indexOf( 97 );//

	System.out.println( index1 );
	System.out.println( index2 );

	 index번호 13번째 이후에서 (가장먼저 )a를찾음 ,a의 인덱스 번호를 구함 
	int index3 = message.indexOf( 'a', 13 ); 
	System.out.println( index3 );
	 가장먼저 나오는 'av'의 인덱스 번호
	int index4 = message.indexOf( "av" );   
	System.out.println( index4 );
                                                  
	int index5 = message.indexOf( "man", 12 );   인덱스 번호12번 이후에서 'man'의 인덱스 번호 구하라
	System.out.println( index5 );
                                                     찾고자 하는 인덱스 번호가 없으면(-1)리턴 출력
	int index6 = message.indexOf( "java" );
	System.out.println( index6 );
    }
    
`   
### 1.Trim(): 문자열  좌우의 공백을 없애주는 역할 
```````````````````````````````````````````````````````````
package p2022_07_01;

public class TrimTest {

	
//	1.Trim(): 문자열  좌우의 공백을 없애주는 역할
//	boolean equals(): 값을 비교하는 역할
    public static void main( String[] args ) {
	String str1 = new String( "gemini   " );
	String str2 = new String( "   gemini " );

	System.out.println( str1.equals( str2 )); // 공백이 있어서 값이 다르게 출력 false +
	System.out.println( str1.trim().equals( str2.trim())); // 공백을 없애주어서 값이 true
    }
}
// 공백도 메모리에 차지한다. 
``````````````````````````````````````````````````````````````````````````````````
### substring 메소드 
`````````````````````````````````

public class SubStringTest {
    public static void main( String[] args ) {

 substring(): 전체 문자열에서 특정 범위의 문자를 추출하는 역할   
    	
 substring(n) : index번호 n번 부터 끝까지 추출
 substring(n1, n2) : index번호 n1번 부터  (n2-1)번 까지 추출 
		           
    	
		
String message = "Java program creates many objects.";
  인덱스 번호 13부터 끝까지 추출		
	String str1 = message.substring( 13 );
	System.out.println( str1 );

	인덱스번호 13부터 15까지 추출 (n1번 부터  (n2-1))
	String str2 = message.substring( 13, 16 );
	System.out.println( str2 );
    }
}
```````````````````````````````````````
### 주민번호 문제
````````````````
package p2022_07_01;

import java.util.Scanner;

public class JuminCheck {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

//키보드로 주민 번호를 입력받아서 남자인지,여자인지 판별하는 프로그램 작성
//(단 주민번호 앞자리는 6자리  뒤자리는 7자리 인지를  유효성 검사를 한다.)
		
		Scanner sc =new Scanner(System.in);
		
		System.out.println("주민번호 앞자리를 입력하세요?");
		String jumin1 =sc.nextLine();
		System.out.println("주민번호 뒤자리르를 입력하세요?");
		String jumin2 =sc.nextLine();
		
		String g =jumin2.substring(0,1);//(뒷자릿 추출)
		
		if(jumin1.length()!=6) {
			System.out.println("주민번호 앞자리 6자리를 입력하세요");
			
		}else if(jumin2.length()!=7) {
			System.out.println("주민번호 뒷자리 7자리를 입력하세요");
			
		}else if(g.equals("1")|| g.equals("3")) {
			System.out.println("남자 입니다.");
		}else if(g.equals("2")|| g.equals("4")) {
			System.out.println("여자입니다.");
			
		}else {
			System.out.println("똑바로 입력하세요.");
		}
		
		
		
		
		
	}

}
`````````````````````````
# StringTokenizer 클래스





















String의 split() 메소드 이용












