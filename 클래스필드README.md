## 정적 필드 stitic 
* 1.정적 필드 :객체 내부에 존재하지 않고, 메소드 영역에 존재
* 2. 정적 멤버는 객체를 생성하지 않고 클래스로 바로 접근해 사용
* 3. stitic 싱글톤을 만들때 사용한다.
* 4. 공유를 위해서  메소드에 할당을 하게 되어 마지막에 저장된 값 갖는다
## 정적 메소드 사용시 유의할점
*  1. 정적 메소드에서는 this 레퍼런스 변수를 사용할 수 없다.
*  2. 정적 메소드에서는 일반적인 변수를 사용할 수 없다.
*   정적 메소드에서는 정적멤버변수만 사용가능함
*  4. 정적 메소드는 메소드 오버라이딩되지 않는다.




예문
````````````````````````````````
package p2022_06_28;

class StaticTest2{
  private static int a=10;                  // 정적필드
  private int b=20;                         // 인스턴스 필드 
  
  public static void setA(int new_a){       // 정적 메소드       
     a = new_a;
  }
  public static int getA(){                 // 정적 메소드 
    return a;
  }
}
public class StaticTest02 {
  public static void main(String[] args) {
//  System.out.println(StaticTest2.a);//a가 private으로 선언되어서 컴파일 에러 발생 
    System.out.println(StaticTest2.getA());  

    StaticTest2 s1=new StaticTest2();          
    StaticTest2 s2=new StaticTest2();
  
    s1.setA(10000);
    int res1=s1.getA();
    System.out.println(res1);
    System.out.println(s2.getA());
 }    
}     
// 아무리 정적 필드라도 private은 외부 클래스는 허용이 되지 않는다. (정적 필드: 공유   private:공유X )
//  private 와 정적 필드는 같이는 사용 못한다. 















