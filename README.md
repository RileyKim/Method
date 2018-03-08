#메소드
-----------------

메소드는 선언부(리턴 타입, 메소드 이름, 매개변수 선언)와 실행 블록으로 구성된다.

**리턴 타입**

리턴 타입은 메소드가 실행 후 리턴하는 값의 타입을 말한다. 메소드는 리턴 값이 있을 수도 있고 없을 수도 있다.

리턴값이 없는 메소드는 리턴 타입에 void가 와야 하며 이턴 값이 있는 메소드는 리턴 값의 타입이 와야한다.

**메소드 이름**

메소드 이름은 이 메소드가 어떤 기능을 수행하는지 쉽게 알 수 있도록 기능 이름으로 지어주는 것이 좋다.

주의사항.

1. 숫자로 시작하면 안되고, $와_를 제외한 특수 문자를 사용하지 말아야한다.
2. 관례적으로 메소드 명은 소문자로 작성한다.
3. 서로 다른 단어가 홉한된 이름이라면 뒤이어 오는 단어의 첫머리 글자는 대문자로 작성한다.


**매개 변수 선언**

매개 변수는 메소드가 실행할 때 필요한 외부로부터 받기 위해 사용된다. 매개 변수도 필요한 경우가 있고 필요 없는 경우가 있다.

## 매개 변수의 수를 모를 경우

메소드의 매개 변수는 개수가 이미 정해져 있는 것이 일반적이지만, 경우에 따라서는 메소드를 선언할 때 매개 변수의 개수를 알 수 없는 경우가 있다. 예를 들어 여러 개의 수를 모두 합산하는 메소드를 선언해야 한다면, 몇 개의 매개 변수가 입력될지 알 수 없기 때문에 매개 변수의 개수를 결정할 수 없을 것이다. 

**해결 방법은 매개 변수를 배열 타입으로 선언하는 것이다**

```
//[예시1]
int sum1(int[] values){ }
```

##리턴 문

**리턴 값이 있는 메소드**

메소드 선언에 리턴 타입이 있는 메소드는 반드시 리턴 문을 사용해서 리턴 값을 지정해야 한다.

##메소드 호출
메소드는 클래스 내외부의 호출에 의해 실행된다. 클래스 내부의 다른 메소드에서 호출할 경우에는 메소드 이름으로 호출하면 되지만, 클래스 외부에서 호출할 경우에는 우선 클래스로부터 객체를 생성한 뒤, 참조 변수를 이용해서 메소드를 호출해야 한다. 그 이유는 객체가 존재해야 메소드도 존재하기 때문이다.


**객체 내부에서의 호출**

```
import java.util.Scanner;

/*문제] 함수로 분리하기 - 성적처리 
input() {  이름/과목 3개 입력받기; }
process( )  {   } 총점/평균 구하기
grade() {  } 학점 구하는 함수 
main() {  } 함수 호출하기 
(적절하게 알아서 만들기 )*/

public class homework2 {
	

	
	public static void main(String[] args) {

		input();
		int avg = process();
		grade(avg);
	}

	
	public static void input() {
		
		System.out.println("이름을 입력하세요");
		String name = new Scanner(System.in).nextLine();
		System.out.println("과목1을 입력하세요");
		String class1 = new Scanner(System.in).nextLine();
		System.out.println("과목2을 입력하세요");
		String class2 = new Scanner(System.in).nextLine();
		System.out.println("과목3을 입력하세요");
		String class3 = new Scanner(System.in).nextLine();
		
		System.out.println("이름 :" + name +"\n과목1: "+class1+"\n과목2 : "+class2+"\n과목3 : "+class3);
		
	}
	
	public static int process() {
		
		//System.out.println(input());
		
		System.out.println("과목1의 점수를입력하세요");
		int x = new Scanner(System.in).nextInt();
		System.out.println("과목2의 점수를 입력하세요");
		int y = new Scanner(System.in).nextInt();
		System.out.println("과목3의 점수를 입력하세요");
		int z = new Scanner(System.in).nextInt();
		
		int sum = x+y+z;
		int avr = sum/3;
		System.out.println("총점 : " + sum + "\n평균 : " + avr);
		
		return avr;
	}
	
	public static void grade(int avg) {
		if(avg <= 100 && avg >50) {
			System.out.println("학점A");
		}else {
			System.out.println("학점B");
		}
	}
}

```

**객체 외부에서의 호출**

```
//CarExample.java

public calss CarExample{
	public static void main (String[] args){
		Car myCar = new Car(): // 객체 생성
		myCar.keyTurnOn(); // 다른 클래스 내 메소드 호출
	}
}

```

```
//Car.java

public class car{
	void keyTurnOn{
	System.out.println("주행합니다.");
}
```

## 메소드 오버로딩
클래스 내에 같은 이름의 메소드를 여러 개 선언하는 것

메소드 오버로딩의 조건은 매개 변수의 타입, 개수, 순서 중 하나가 달라야 한다.

```
int plus(int x, int y){
	int result = x+y;
	return result;
}


int plus(double x, double y){
	double result = x+y;
	return result;
}
```