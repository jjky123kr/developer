# 배열 Array <참조형>
 * 힙(heap)에 메모리 값을 저장한다. 
 * 힙(heap)공간을 늘릴수 있다. = new 
 * 동일한 자료형의 데이터 값을 저장하기 위한 (정적인 자료구조 )=>크기가 정해져 있다.
 * 변수를 확장 시킨 것 : 변수를 많이 사용할 경우 배열을 사용 할때 간결하게 작성 할수 있다.
 * 자동으로 초기값이 0으로 된다. <기본자료형이라도>
 * 효율적적으로 사용이 된다. (코드가 줄 일수 있다.)
#### 1차원 배열 :값이 정해져 있지 않은 경우
``````

 int[]       score     =     new        int[3];
  자료형    배열변수         연산자   배열의 크기(=방의 갯수)

score[0]=80;
score[1]=90;
score[2]=100;
 //int 배열은 자동으로0으로 초기화 된다. 
System.out.println(score[0]);   // 80
System.out.println(score[1]);   // 90
System.out.println(score[2]);   // 100

//double 배열은 자동으로 0.0으로 초기화 된다. 
double[]d =new double[3];
System.out.println(d[0]);    //0.0
System.out.println(d[1]);    //0.0  
System.out.println(d[2]);    //0.0

 // char은 초기값이 없다.
char[]c=new char[3];		
System.out.println(c[0]);
System.out.println(c[1]);
System.out.println(c[2]);
		
//boolean 배열은 자동으로 false로 초기화가 된다. 
boolean[] b= new boolean[3];
System.out.println(b[0]);    //false
System.out.println(b[1]);	//false
System.out.println(b[2]);   //false
		
// String
String[] str =new String[3];
System.out.println(str[0]);  //null : 값이 없다. 
System.out.println(str[1]);  //null
System.out.println(str[2]);  //null
		
str[0]= "자바";
str[1]= "오라클";
str[2]= "스프링";
System.out.println(str[0]);     //자바
System.out.println(str[1]);    // 오라클
System.out.println(str[2]);    // 스프링

```````

### 2차원 배열 : 배열 선언과 동시에 초기화를 할때 주로 사용
###    (배열에 할당될 값이 정해져 있는 경우)
  
* 초기값이 필요하다.  
* 배열의 크기를 구하는 속성 : _(length)_
``````    
int[][]    score    =   new   int[5][3];
 자료형    배열변수     연산자     [5]:행
   		      [3]:열

    int[]  score = {80, 90, 100};
    int[]  score = new int[]{80, 90, 100};

    double[] d = {3.14, 10.5, 42.195};

    char[]  c = {'j', 'a', 'v', 'a', '안'};

    String[]  str = {"java", "jsp", "oracle"};
    String[]  str = new String[]{"java", "jsp", "oracle"};
    
    
    int[]s1= {80,90,100};
		int[]s2=new int[] {80,90,100};
		System.out.println(s1[0]);     //80
		System.out.println(s1[1]);     //90
		System.out.println(s1[2]);     //100
 
 System.out.println("배열의 크기:"+s1.length);//배열의크기:3
  for(int i=0; i<s1.length; i++)
 
 System.out.println(s1[i]+"\t");
	   System.out.println();
    
 
 //작은 데이터 값을 큰데이터에 넣어도 된다. 하지만 큰 데이터값 에서 작은 데이터 값은 안된다.  
 double[]dd= {3.14,10.5,42.195,50};
 for(int i=0; i<dd.length; i++)

  System.out.println(dd[i]+"\t");
  System.out.println();
	    	 

