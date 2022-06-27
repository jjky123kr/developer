# String 
* 문자열 리터럴 동일하다면 String 객체 공유
*new 연산자를 이용한 String 객체 생성
*    힙 영역에 새로운 String 객체 생성
*    String 객체를 생성한 후 번지 리턴



```````````````
//String 클래스
//==: 참조하는 주소를 비교
//equals():참조하는 값(데이터)을 비교	
		
		String str1="자바";
		String str2="자바";
		
		if(str1==str2) { //비교연사잔(==)로 잠조하는 주소를 비교
			System.out.println("같은주소");     //같은 주소
		}else {
		System.out.println("다른 주소");
		
	}
    String str3= new String("자바");
    String str4= new String("자바");

	if(str3==str4) { //비교연사잔(==)로 잠조하는 주소를 비교
		System.out.println("같은주소");     
	}else {
	System.out.println("다른 주소");   //다른 주소
		
		
       }
     }
}


