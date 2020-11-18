String vs StringBuffer vs StringBuilder
================

### 대략적으로 StringBuffer>=StringBuilder>String 성능차이를 보인다.

+ String클래스는 변경이 불가능한 클래스이다.   
	String클래스에서 substring()*, toLowerCase(), concat*, trim()*등의 메소드를 생각하면   
	String클래스는 변경 가능한 클래스처럼 보인다.    
	하지만 이것은 새로운 String 객체를 만들어내는 것이다.    
	변경이 적어서 안전하게 공유될 수 있어, synchronization과 같은 안전장치가 필요없다.    

- StringBuffer클래스는 변경이 가능한 클래스이다.    
	append(), insert(), delete() 등의 메소드를 통해 변경이 가능하다.   
	synchronization이 되어있어, 멀티스레드에 대해선 안전하다.   
	문자를 추가하거나 삭제할 때 "인스턴스 생성을 최소화"하므로 성능을 향상시킨다.    

* StringBuilder클래스도 변경이 가능한 클래스이다.   
	StringBuffer와 같은 함수를 사용한다. (둘이 상호호환도 되는 것 같다.)   
	차이점은, StringBuilder클래스는 synchronization이 되어있지 않다.   
	그러므로 멀티스레드에서 전혀 안전하지 않다.   
	문자를 추가하거나 삭제할 때 "인스턴스 생성을 최소화"하므로 성능을 향상시킨다.   
	    
* * *

 ** ☆문자열 연산이 많지만 엄청나게 일어나지 않는 환경이라면    
   StringBuffer를 사용해서 thread-safe한 것(안정적인 것)이 좋아보인다. **

----------------------------------------------------------------------------
#### _StringBuffer & StringBuilder 함수 몇 가지_

* substring(): 문자열의 인덱스를 활용하여 자르는 함수이다.
    String.substring(start) //문자열 start index부터 끝까지 문자열 자르기(발췌)
    String.substring(start,end) //문자열 start index부터 end 전까지 문자열 발췌

+ concat: 문자열을 합치는 기능을 한다.
    a.concat(b) // 두개의 문자열을 합칠 때는 concat이 좋고, 여러 문자열일 때는 그냥 +연산자가 좋다.

- trim(): 문자열 앞 뒤 공백을 제거하는 함수이다.
