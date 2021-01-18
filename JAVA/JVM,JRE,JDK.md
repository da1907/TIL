# JVM / JRE / JDK

▶️ HelloJava.java(소스파일) -> 자바 컴파일러(javac.exe) -> 바이트코드(\*.class)

▶ 바이트코드(\*.class) -> 자바 인터프리터(java.exe) -> 실행결과 출력

: 컴파일러를 거치고나면 (javac HelloJava.java) \*이 HelloJava로 바뀐 후 바이트 코드가 생성되고 (파일 명과 클래스 명은 동일), 인터프리터를 거치면 (java HelloJava) 실행결과가 출력됨.

![스크린샷 2021-01-18 오후 11 34 02](https://user-images.githubusercontent.com/32568829/104928156-a7a62b00-59e5-11eb-9f99-72afe4e8d08b.png)

<br>

## JVM (Java Virtual Machine)

- 자바 가상 머신(Java Virtual Machine)의 약자
- 자바는 어떤 운영체제에서도 동일한 형태로 실행시킬 수 있는데 이를 가능하게 해주는 것이 JVM이다.
- JVM은 소스코드로부터 컴파일러를 통해 바이트코드(.class)가 만들어지면 인터프리터를 통해 이 코드를 실행해주는 가상머신
- 실행환경(Runtime Environment)의 규격 제공
- Java와 OS 사이에서 중개자 역할을 수행하여 Java가 OS에 구애받지 않고 재사용을 가능하게 해준다.
- 각 플랫폼에 의존적이다. (리눅스 JVM과 윈도우 JVM은 다름)  
  => 바이너리 파일(.class)만 만들면 각 플랫폼에서 동작 가능
- 자바 프로그램의 메모리를 효율적으로 관리해주고 최적화해 준다. (Garbage Collection)

<br>

## JRE (Java Runtime Environment)

- 자바 실행환경(Java Runtime Environment)의 약자 (개발도구 제외)
- JVM의 실행환경 구현  
  -> JVM이 자바 프로그램을 실행시킬 때 필요한 라이브러리 및 기타 파일을 가지고 있음
- JRE = JVM + Library Classes

<br>

## JDK (Java Development Kit)

- 자바 개발 도구(Java Development Kit)의 약자
- JDK = JRE + Development Tools
- Development Tools? 개발에 필요한 도구(컴파일러(javac.exe), 인터프리터(java.exe) 등)

<br>

![스크린샷 2021-01-18 오후 11 29 37](https://user-images.githubusercontent.com/32568829/104927690-133bc880-59e5-11eb-8871-af5215035cc0.png)
