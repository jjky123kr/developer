# 배열 <참조형>
  힙(heap)에 메모리 값을 저장한다. 
  힙(heap)공간을 늘릴수 있다. = new
* 동일한 자료형의 데이터를 저장하기 위한 정적인 자료구조

#### 1차원 배열 :값이 정해져 있지 않은 경우
``````

 int[]       score     =     new        int[3];
  자료형    배열변수         연산자   배열의 크기(=방의 갯수)

score[0]=80;
score[1]=90;
score[2]=100;

System.out.println(score[0]);   // 80
System.out.println(score[1]);   // 90
System.out.println(score[2]);   // 100

```````

### 2차원 배열 : 배열 선언과 동시에 초기화를 할때 주로 사용
###    (배열에 할당될 값이 정해져 있는 경우)
    
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
    
    

