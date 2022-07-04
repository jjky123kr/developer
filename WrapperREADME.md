
# Wrapper 클래스


* 주로 자료형 변환을 사용할 때 많이 쓴다.
 ### 자바의 기본 데이터형   Wrapper 클래스
####  기본자료형을 참조할때 
 |boolean| Boolean|
-|-----------------|
|byte| Byte|
|short|	Short|
|int|Integer|
|long|	Long|
|float|	Float|
|double|Double|
|char|Character|


* 각 자료형들이 제공은 되지만 거의 int형만 쓴다. Integer가 중요 - 90%이상 Integer 사용

``````````java

20이란 문자를 숫자 20으로 변환을 시킬 때
"20"  --->  20
 
방법1. 
	>int num = Integer.parseInt("20")>;  // (박싱) parseInt :int 형

방법2.
	>Integer in01 = new Integer("20");		
	>int num01 = in01.intValue();		//언박싱



 20  --->  "20"  int---> String 
>방법1.
	>String s = String.valueOf(20);/>/ valuof은 정적메소드(.) 

>방법2.
	>Integer in = new Integer(20);
	>String s = in.toString();      

방법3.    20 -->  20 + ""
```````````````````````````
예문
`````````````````````java
		// TODO Auto-generated method stub

		//int 형 변수의 최대값과 최소값 출력   	MAX_VALUE, MIN_VALUE 정적필드 
		
		System.out.println("max="+Integer.MAX_VALUE); 
		System.out.println("max="+Integer.MIN_VALUE); 
		
//		String형을 int형으로 형변환:"20"-->20;
		int n =Integer.parseInt("20");
		System.out.println(n);      //20: 숫자
		System.out.println(n+10);   //30: 산수연산 가능
		
//		10진수를 2진수로 변환= naryStrintoBig   
		System.out.println("2진수:"+Integer.naryStrintoBig(10));  //1010
//      10진수를 8진수로 변환=toOctalString	
		System.out.println("8진수:"+Integer.toOctalString(10));//12
//		10진수를 16진수로 변환=toHexString
		System.out.println("8진수:"+Integer.toHexString(10));//a 
		
	}

}

```````````````````````java
package p2022_07_04;

public class WrapperEx1 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
//      Integer 클래스는 기본생성자를 지원하지 않는다 
//   생성자: Integer(int value) , Integer(String s) 
//	Integer num =new Integer(); 생성자가 아닌것을 사용불가하다.  

//   박싱(boxing)힙 메모리를 박스로 생각하고,stack메모리에 저장된10을 
//	             힙 메모리에 복사를 한다.(박스에 집어넣는다.)

		int n=10;                       //지역변수(stack영역)
		Integer num01= new Integer(n);  // 박싱(boxing)
//		int n(변수)에 값을 힙 메모리 에 저장를 한다. 

//  언박싱(unboxing): heep메모리에 있는 데이터를 stack메모리로 가져오는 것을 의미한다.		
		int n01= num01.intValue(); // 언박싱(unboxing)

		//자료형 변환:"20"-->20
		Integer num02= new Integer("20");   // 박싱(boxing)
		int n02=num02.intValue();           // 언박싱(unboxing)  
	}

}
```````````````````java
//p529
//      박싱		
	    Integer obj01= new Integer(10);	
	    Integer obj02= new Integer("200");	
	    Integer obj03= Integer.valueOf("300"); // valueOf 메소드 사용
	    
//	    언박싱
	    
	    int value1= obj01.intValue();    //intValue 메소드 사용
	    int value2= obj02.intValue();  //자료형 변환:"200"-->200
	    int value3= obj03.intValue();  //자료형 변환:"300"-->300
	    
	    
	    System.out.println(value1);
	    System.out.println(value2);
	    System.out.println(value3);

```````````````````````````````````````	 java   
package p2022_07_04;

public class WrapperEx3 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

//	p530
//자동 박싱과 자동 언박싱 

		Integer oj=new Integer(10);                     // 박싱
		Integer obj=10;                                 //자동 박싱
		System.out.println("언박싱:"+obj.intValue());     // 언박싱은 .intValue
		System.out.println("언박싱:"+(obj.intValue()+10));   // 언박싱은 .intValue 
		System.out.println("자동언박싱:"+obj);  // 자동언박싱은   obj 
		
		// 언방식
		int value1 = obj.intValue();
//		자동 언박싱
		int value2= obj;
		System.out.println("value2:"+value2);
//		자동 언박싱
		int result= obj +100;
		System.out.println("result:"+result);
		
	}

}	}

}



# 예문3. Double형 일때 
```````````````````````````````````````````````````java

package p2022_07_04;

public class WrapperEx4 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

//      Double 클래스는 기본 생성자 지원 안된다. 		
//		Double d = new Double();  // 오류 발생 
		
		Double d1= new Double(3.14);  // 박싱(boxing)
        Double d11=3.14;              // 자동박싱
		
        double n1 = d1.doubleValue();   // 언박싱(unboxing)		
        double n11 = d1;                // 자동언박싱
        
     // 자료형 변환: "42.195"--->42.195    
        Double d2= new Double("42.195");  // 박싱(string형)
    //  Double d2="42.195";               // 자동 박싱은 오류 발생 
        
        double n2 = d2.doubleValue();     // 언 박싱 
		double n22=d2;                     // 자동 언 박싱 
		
//		자료형 변환:"42.195"--->42.195  
		double num= Double.parseDouble("42.195");
		System.out.println("num="+num);
		
	}

}
```````````````````````````
예문 4.string
`````````````````````````java
package p2022_07_04;

public class ValueOfEx {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

//p511
//valueof()	:기본 자료형을 문자열로 변환:
//		      ex) 20---->"20"
		 
		String str1= String.valueOf(10);   // 10--->"10"
		String str2= String.valueOf(10.5); // 10.5-->"10.5"
		String str3= String.valueOf(true); // true-->"true"
		
		
		System.out.println(str1);
		System.out.println(str2);
		System.out.println(str3);
	}

}




