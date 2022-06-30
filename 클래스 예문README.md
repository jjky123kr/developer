

### 기본 
`````````````````````````````````
public class Animal {
    int age;  //멤버변수,필드(field),전역변수 : heap힙 메모리에 저장(자동 초기값0;값)
          // : 메소드 바깥쪽에 정의되는 변수
   public Animal(){  //기본 생성자(Default constructor) //클래스명과 동일
	                   
   System.out.println("생성자 호출 성공");        // 생성자 호출이 없을때  자동으로 컴파일러 한다.
	}
    public static void main(String[] args) {
	// TODO Auto-generated method stub
       
   int a=10;   // 지역변수: stack 메모리 영역에 저장
		
   String str = new String("자바");
		
  Animal  a1 =       new    Animal();
  클래스  레퍼런스 변수  연산자  생성자 호출
		
	System.out.println();         // 오류
	System.out.println(a1.age);   //0    *a1이 갖고 있는 주소 참조해서 (.)점으로 접근한다. 

	a1.age=5;
	System.out.println(a1.age);   //5
	
    Animal   a2   = new  Animal();
       System.out.println(a2.age);
	                   주소값
	    
	    
    if(a1==a2) {                    //주소값 비교
	   System.out.println("같은주소");
    }else {
	   System.out.println("다른 주소");
	    }
	}

}

package p2022_06_28;

//p201 //접근제어자는 1번만 쓴다. 메인 메소드만 사용할수 있다. 
class Car{
	//필드 (field)=속성을 표현한다. 주어진 값으로 초기값이 된다. 
	String company ="현대 자동차";
	String model="그랜저";
	String color ="검정";
	int maxSpeed=350;          
	int Speed;             //int는 자동으로 초기값0;

	
	public Car() {            //기본 생성자(필드와 생성자 구성)독립적으로 실행이 되지 않는다
        System.out.println("생성자 호출");
	}            
}
public class CarEX {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
        // 객체 생성
		Car mycar = new Car(); //객체를 생성할때 생성자가 호출된다. 
		System.out.println("제작회사:"+mycar.company);
		System.out.println("모델명:"+mycar.model);
		System.out.println("색깔:"+mycar.color);
		System.out.println("최고속도:"+mycar.maxSpeed);
		System.out.println("현재속도:"+mycar.Speed);  //0
		
		//필드값 변경
		mycar.Speed=60;
		System.out.println("수정된 속도:"+mycar.Speed);//60
		
				

```````````````````````````````````````````````````````````````
### 매개 변수의 초기화 
  
``````````````````````````````````````````````
package p2022_06_28;

//p202     
class FieldInitValue{
//	   필드(field)
	byte byteField;
	short shortField;
	int intField;                   //정수형0 초기화  *
	long longField;
	
	float floatField;               //실수형 0.0 초기화 *   
	double doubleField;
	
	char charField;
	boolean booleanField;           //논리형 false로 초기화*
	
	int[] arrField;
	String  referenceField;         //null은 참조할 주소가 없다. *
			                        //null 로 초기화
}

public class FieldEx {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		 FieldInitValue f = new FieldInitValue();
		 
		 System.out.println("byteField:"+f.byteField);
		 System.out.println("shortField:"+f.shortField);
		 System.out.println("intField:"+f.intField);
		 System.out.println("longField:"+f.longField);
		 
		 
		 System.out.println("floatField:"+f.floatField);
		 System.out.println("doubleField:"+f. doubleField);
		 
		 System.out.println("charField :"+f.charField);
		 System.out.println("booleanField :"+f.booleanField);
		 
		 
		 System.out.println("arrField:"+f.arrField);
		 System.out.println("referenceField:"+f.referenceField);
	}

}
`````````````````````````````````````````````````````````````````````
### 1. 매개 변수 와 멤버 변수가 이름을 다를게 명시 할때 
```````````````````````````
package p2022_06_28;

class MyDate05{     //필드
  private int year;      
  private int month;    
  private int day;

//  기본 생성자는 객체를 생성할때 컴파일러가 자동으로 만들어 주지만, 
//  예외적으로 매개변수를 가진 생성자가 있을 경우에는 더이상 기본생성자를 만들어주지 않는다. 
  
  public MyDate05(){   //기본생성자
  }                    //매개변수 생성자 (지역변수)  
  public MyDate05(int new_year, int new_month, int new_day){ 
    year=new_year;
    month=new_month;
    day=new_day;
  }  
  public void print(){  //메소드 
    System.out.println(year+ "/" +month+ "/" +day); 
  }
}
public class ConstructorTest05 {     
  public static void main(String[] args) {
    MyDate05 d= new MyDate05();  
    d.print();
//                    기본생성자 호출
    MyDate05 d2= new MyDate05(2017, 7, 19);
    d2.print();       //매개변수가 있는 생성자 호출 (생성자를 통해서 초기화 역할 )
  }
}      


``````````````````````````````````````````
### 2. 매개 변수와 멤버 변수가 같을때 (  이경우를 많이 사용한다. )
###  this. 생성자와 메소드 안에서 멤버변수와 매개변수 이름이 동일한 경우에 주로 사용함. 
``````````````````````````````
package p2022_06_28;

class MyDate04{   //필드  
  int year;      //2017
  int month;     //7
  int day;       //19

  public MyDate04(){   //기본생성자
    year=2016;
    month=4;    
    day=1;
  }
  
  *이클립스를 활용해서 만들때 오른쪽 마우스 클릭후 source를 클릭후 밑에서3번째 클릭한다. 
  *그리고, 마지막 칸 체크후 생성 
  //매개변수와 멤버변수의 같은 이름이 같을때 this 쓰면 값이 나온다. 
  //this:내부 레퍼런스 변수  this.은 멤버변수 
  public MyDate04(int year,int month,int day){
   this.year=year;
   this.month=month;
   this.day=day;
  }
  public void print(){      
	System.out.println(year+ "/" +month+ "/" +day); 
  }
}// MyDate end

public class ConstructorTest04 {     
  public static void main(String[] args) {
    MyDate04 d= new MyDate04();	   //생성자 호출
    System.out.println(d.year);
    System.out.println(d.month);
    System.out.println(d.day);
    d.print();  //메소드 호출 

    MyDate04 d2=new MyDate04(2017, 7, 19);
    System.out.println(d2.year);
    System.out.println(d2.month);
    System.out.println(d2.day);
    d2.print();
    
    MyDate04 d3=new MyDate04(2022,6,28); 
    
    d3.print();
    
    
  }
}         
```````````````````````````````````````````````````
### 필드 값을 변경하고 싶을  경우
````````````````````````````````````````````````````````````````````
package p2022_06_28;

// 생성자 초기화 중에 필드값을 변경을 해주고 싶을때 
// 메소드를 통해 필드값을 변경한다. 
class MyDate06 {
	private int year; // 필드
	private int month;
	private int day;

//  public MyDate(){//default 생성자
//  }  
	public MyDate06(int new_year, int new_month, int new_day) {
		year = new_year; // 2017
		month = new_month; // 7
		day = new_day; // 19
	}
	// 매개변수 명과 메소드 변수 다르게 해야 수정이 가능하다.,this.을 사용해서 한다.
// 이클립스에서 오른쪽 마우스 클릭후 source를 클릭후 getters,setter 생성 코드 확인후 클릭한다. 
	public int getYear() {            //getters method (메소드 호출 (setter)값한 곳에 값을 돌려주는( return)  역할을 한다.)
		return year;
	}

	public void setYear(int year) {   // setter method (매개변수와 멤버변수가 동일할때 자동으로 this. 으로 생성해준다.  )
		this.year = year;
	}

	public int getMonth() {
		return month;           
	}

	public void setMonth(int month) {
		this.month = month;
	}

	public int getDay() {
		return day;
	}

	public void setDay(int day) {
		this.day = day;
	}

	public void print() { // 수정된 값을 출력을 한다.
		System.out.println(year + "/" + month + "/" + day);
	}
}

public class ConstructorTest06 {
	public static void main(String[] args) {
		MyDate06 d = new MyDate06(2017, 7, 19);
		d.print();

		d.setYear(2022);
		d.setMonth(6);
		d.setDay(28);
		d.print();     //출력한다. 
		
		System.out.println(d.getYear());      메소드 호출한 곳에 값을 돌려주는 역할을 한다. 
		System.out.println(d.getMonth());
		System.out.println(d.getDay());
		
		
		
		
	}
}
````````````````````````````````````````````````````````````````````
###  필드 값을 변경하고 싶을  경우 this() -생성자 오버 로딩 
``````````````````````````````````````````
package p2022_06_28;
//this():같은 클래스안에 있는 생성자를 호출하는 의미
class MyDate10{   

  private int year;    
  private int month;    
  private int day;
// 생성자 오버로딩 : 한개의 클래스에 여려 개의 생성자를 정의 하는 것
//  매개변수의 자료형을 다르게 한다., 매개변수의 갯수,매개변수의 순서 
  public MyDate10(){                  
    this(2016, 1, 1);                   
  }  
  public MyDate10(int new_year){
    this(new_year, 1, 1);                
  }  
  public MyDate10(int new_year, int new_month){
     this(new_year, new_month, 1);    
  }  
public MyDate10(int new_year,int new_month,int new_day){        
    year=new_year;
    month=new_month;
    day=new_day;
  }    

  public void print(){
	System.out.println(year+ "/" +month+ "/" +day); 
  }
}

public class ConstructorTest10 {     
  public static void main(String[] args) {
    MyDate10 d=new MyDate10(2017, 7, 19);  
    d.print();
    MyDate10 d2=new MyDate10(2017, 7);     
    d2.print();
    MyDate10 d3=new MyDate10(102017);       
    d3.print();
    MyDate10 d4=new MyDate10();          
    d4.print();
  }
}
``````````````````````````````````````````````````````````````
###  메소드 예제 1.
`````````````````````````````````````````````````````````
package p2022_06_29;

// p217 ~ 218

class Calculator{
	// 메소드
	void powerOn() {
		System.out.println("전원을 켭니다.");
		return;					// 생략 가능
	}
	int plus(int x, int y) {	// 지역변수 : x, y, result
		int result = x + y;
		return result;
//		System.out.println("test");
	}
//	return문 : plus() 메소드를 호출한 곳에 값을 돌려주는 역할.
//	return문은 메소드 가장 마지막 줄에 사용해야 한다.
	
	double divide(int x, int y) {
		double result = x / (double)y;
		return result;
	}
	
	void powerOff() {
		System.out.println("전원을 끕니다.");
	}
}

public class CalculatorEx {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Calculator cal = new Calculator();
		cal.powerOn();
		
		int result1 = cal.plus(5, 6);
		System.out.println("result1:"+ result1);
		
		byte x = 10;
		byte y = 4;
		double result2 = cal.divide(x, y);
		System.out.println("result2:"+ result2);
		
		cal.powerOff();
	}

}


















``````````````````````````````````````````````````````````````````````````````````
### 메소드 2.예제  참조형(배열) : 주소값 전달에 의한 메소드 호춯(Call by Reference방식) 
```````````````````````````````````````````````````````````````````````````
package p2022_06_29;
//p220~221

class Computer{	
	int sum1(int[]values) {
		int sum=0;
		for(int i =0; i<values.length; i++) {
			sum+=values[i];
			}
        return sum;
	}
//	vargus: 전달된 값은 배열로 받음
	int sum2(int...values) {
		int sum=0;
		for(int i=0; i<values.length;i++) {
			sum+= values[i];
		}
	      return sum;
	}
}
public class ComputerEx {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

		Computer com = new Computer ();
		int[] values1= {1,2,3,};
		int result1=com.sum1(values1); // sum1(호출)
		System.out.println("result1:"+result1);
		
		int result2 = com.sum1(new int[] {1,2,3,4,5,});
		System.out.println("result1:"+result2);
		
		int result3 = com.sum1(new int[] {1,2,3,});
		System.out.println("result3:"+result3);
		
		
		int result4 = com.sum1(new int[] {1,2,3,4,5});
		System.out.println("result4:"+result4);
	}

}







































