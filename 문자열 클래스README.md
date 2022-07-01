# String 
* 문자열 리터럴 동일하다면 String 객체 공유
*new 연산자를 이용한 String 객체 생성
*    힙 영역에 새로운 String 객체 생성
*    String 객체를 생성한 후 번지 리턴

# String 클래스
## ==: 참조하는 주소를 비교 
````````````
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
       
``````````````````````````````````
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
#  String + 가 연결이 왼다.  주소값을이 연결 시킨다. 
`````````````````````````````````````````````````````````
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


```````````````````````````````````````````````````````````````````````
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

`````````````````````````````````````````````````````````````````````````````````````
## length, char  
* length은 문자의 길이를 구하는 역할
* char은 문자 한글자 추출하는 역할
````````````````````````````````````````````````````````````
package p2022_07_01;
public class FindBlankIndex {
    public static void main( String[] args ) {
		
	String message = "Java program creates many objects.";
	// message의 길이를 구함.(문자의 길이를 구하는(글자수)length)
	int len = message.length();

	System.out.println(len);  // len = 34;

	// message 중에서 ' '을 찾음
	for( int i=0 ; i<len ; i++ ) {
	    char c = message.charAt( i );
		if( c == ' ' ) {//  공백의 인덱스 번호를 구해서 출력
		    System.out.println( "index = " + i );
		}
	}//for end
    }
}
//배열의 크기는(s).length은 속성 , String은 length(); 문자의 길이(띄어쓰기,"문자등도 같이 ) 
//charAt은 문자 한글자 추출하는 역할 
`
## Indexof 특정 문자의 인덱스 번호
package p2022_07_01;

public class IndexOfTest {
	public static void main( String[] args ) {
	
//		indexof(); 특정 문자의 인덱스 번호를 구한다. 
		
	String message = "Java program creates many objects.";
	//가장 먼저 나오는 a의 인덱스 번호 
	int index1 = message.indexOf( 'a' ); 
	//10진수 아스키코드 97 에 해당되는 (a)의 인덱스 번호를 구함 (97='a',65='A')
	int index2 = message.indexOf( 97 );//

	System.out.println( index1 );
	System.out.println( index2 );

	//index번호 13번째 이후에서 (가장먼저 )a를찾음 ,a의 인덱스 번호를 구함 
	int index3 = message.indexOf( 'a', 13 ); 
	System.out.println( index3 );
	//가장먼저 나오는 'av'의 인덱스 번호
	int index4 = message.indexOf( "av" );   
	System.out.println( index4 );
//    인덱스 번호12번 이후에서 'man'의 인덱스 번호 구하라
	int index5 = message.indexOf( "man", 12 );
	System.out.println( index5 );
	// 찾고자 하는 인덱스 번호가 없으면(-1)리턴 출력
	int index6 = message.indexOf( "java" );
	System.out.println( index6 );
    }
}
``````````````````````````````````````````````````````````````````````````````````````
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












