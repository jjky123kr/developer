# 반복문
## for문
````java
 for(초기값; 조건식; 증감식){
       반복 실행할 문장;
    }
 for(int i=1; i=<10; i++){
 System.out.println(i+"사랑해요");
 
 int sum=0;
 for(int i=1; i=<10; ++i){
 sum=sum+i;
 System.out.println("1~"+i+"="+sum);
 System.out.println("sum="+sum);
 `````
 #####  지역변수:for안에서만 사용가능
 ##### sum+=i; <누적되는 변수-알고리즘 식>
 ##### sum에 초기값을 설정해야 한다.
 #####  (0으로 설정하는 이유는 +값에 영향이 없어서이다.)
``````
```````
 
### for문 과 if 문 
``````java
int odd=0, even=0;
		for(int i=1; i<=100;i++) {
		 if(i%2==1) {        //홀수
			 odd+=i;
		 }else {            //짝수
			 even+=i;
		      }
  }
  System.out.println("1~100홀수의 합:"+odd);
  System.out.println("1~100짝수의 합:"+even);
    }
}

````````
## While 문
`````java
 while(조건식){
      반복 실행할 문장;
 }
 
 int i=1;
 while(i<=100){
 System.out.println(i+"사랑해요");
 i++ // 증감식
 
 *while 문 과 if ~else문 사용
 int i=1, odd=0, even=0;    //초기값
 while(i<=100){
			if(i%2==1) {      //홀수  구하는 법 
		       odd+=i;
} else {                 //짝수
			    even+=i;
	}
			     i++;            //증감식
     }
     System.out.println("1~100홀수의 합="+odd);
    System.out.println("1~100짝수의 합="+even);
      }
  }
 ```````
 ## do~while문
 `````java
    do(
         반복 실행할 문장;
    }while(조건식);
    
 int i=1;   //초기값
		do {
			System.out.println(i+"사랑해요~");
		     i++;	     
	 }      while(i<=10);    //조건식 (;)세미콜론    
   
   
* do~ While 과 if문  else 과 사용
 int i=1, odd=0, even=0; 
		do {
		if(i%2==1) {
				    odd+=i;
		}else {
			    	even+=i;
}
		i++;
	}while(i<=100);
	
	  System.out.println("1~100홀수의 합="+odd);
	  System.out.println("1~100짝수의 합="+even);
 
