# 보조문
## break문
### 반복문을 빠져 나오는 역할
`````
for(int i=1;;i++) {
			System.out.println(i+"무한출력");
			if(i==100) break;
 i++ 증감식 
 
 *for문 은 반복문 
 *무한 루프를 할때 사용한다. (for문 보다는 While문을 사용한다.)
 *break을 쓸때는 아래쪽에 써야 한다. 
 *증감식 사용
 
 int i=1;
while(true) {    //     참인 조건식을 설정한다
	System.out.println(i+"무한루프");
	if(i==100) break;   <조건식>으로 많이 사용이 된다. 
  i++;
	  	}
``````
## continue문
### 다시 반복문으로 돌아가라는 의미를 가지고 있다.
### continue문 아랫쪽의 내용들은 실행 되지 않고 다시 반복문으로 돌아가게 된다.
````
for(int i =1; i<=10; i++) {
if(i==5)continue;    //continue문은 아랫쪽 문장은 실행되지 않는다. 
System.out.println("출력"+i);

      
