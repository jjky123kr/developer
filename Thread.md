## Thread
```````````````````
cpu ---> RAM (주기억 장치)  
             ||
          HDD,SDD (보조기억장치)
`````````````````````````````````
### Thread : 한개의 프로세스(process) 구성하는 (논리적인) 작업 단위
### 멀티 Thread(스레드):  두개 이상 프로세스 돌아가는 것

### Thread 만드는 경우
*  동시에 2가지 이상 작업 을 할 경우 
*  채팅프로그램 만들때 (보내는것 , 받는것)
### Thread 만드는 방법 
*1. Thread클래스를 상속을 받아서 만드는 방법
*    unnable 매개값으로 갖는 생성자 호출
* 2 Runnable 인터페이스를 상속받아서 만드는 방법

###  Thread의 생명 주기(Life Cycle)

* Runnable :  새로 생성한 Thread를 start하면 Runnable 상태가 됨.  
실행 가능한 상태( start() 메소드 호출한 상태)  

* Running : CPU를 점유하고 run() 메소드 내의 명령문을 실행하는   
	  상태. 실행상태(run() 메소드를 실행한 상태)  

* Block : 특정 메소드의 호출에 의해서 현재 실행중인 Thread가 CPU의   제어권을 잃어버린 상태.  

* Dead : run() 메소드의 명령 수행이 끝났을 경우  

## 1.예문: 자바에서 Thread 만드는 방법     
           Thread클래스를 상속을 받아서 만드는 방법      
````````````````````````java
package p2022_07_11;

// Thread:한개의 process를 구성하는 논리적인 작업 단위
// 자바에서 Thread를 만드는 방법
//1. Thread 클래스 상속 받아서 만드는 방법
//2. Runnable 인터페이스를 상속받아서 만드는 방법


public class ThreadEnd extends Thread {
	
	@Override
	public void run() { // 실행중인 상태 
		// TODO Auto-generated method stub
		// thread가 시작되면 실행되는 문장
		for( int i=1 ; i<=20 ; i++ ) {
		System.out.println( "run number = " + i );
		}
	}

    public static void main( String[] args ) {		
		ThreadEnd tt = new ThreadEnd(); // 객체 생성 
		// thread를 실행시킴
		tt.start();// 실행가능한 상태:run()메소드 호출
		
		// main()내에서 화면에 101부터 120까지 출력  
		for( int i=101 ; i<=120 ; i++ ) {
			System.out.println( "-------> main number = " + i );
		}
    }
    
}
// 실행 할때 마다 결과가 달라진다. 그이유는 cpu를 서로 사용하기 위해서 서로 경쟁한다.
// 1.방법을 사용 못할때는 다중 상속인 경우에 사용하지 못한다. 
``````````````````````````````````````````
## 예문2.:	Runnable 인터페이스를 상속받아서 만드는 방법
``````````````
package p2022_07_11;

public class RunnableTest implements Runnable {
	
    // 1부터 20까지 화면에 출력시키는 메소드 
   
    @Override
    public void run() {
    	// TODO Auto-generated method stub
    	for( int i=1 ; i<=20 ; i++ ) {
			System.out.println( "number = " + i );
		}	
    }
   

    public static void main( String[] args ) {
		// 객체 생성
		RunnableTest tt = new RunnableTest();
		// Thread 클래스 객체 생성
		Thread t = new Thread( tt ); // Thread객체 생성해야 한다. 
		// Thread를 시작시킴
		t.start();  // 실행 가능한 상태: run(); 메소드가 호출 
		System.out.println( "--------> main thread end" );
    }
    
}
``````````````







