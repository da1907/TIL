# Overloading VS Overriding

## 1. Overloading

### 1-1. 메서드 overloading 이란?

<변수의 중복선언>  
변수는 데이터 타입이 달라도 이름이 동일한 경우를 허용하지 않는다.  
=> 클래스 안에 동일한 이름의 변수를 사용했을 때, 프로그램이 모호해지기 때문에

<메서드의 중복정의>  
변수와 달리, 하나의 클래스에 동일한 이름의 메서드는 여러 개 정의할 수 있다.  
=> 매개변수의 개수와 타입을 통해 실행될 메서드를 구분할 수 있기 때문에

> "하나의 클래스에 동일한 이름의 메서드가 여러 개 중복되어 정의되는 것" : `메서드 overloading`

<메서드 overloading>

- 자바 같은 객체지향 언어에서만 제공되는 독특한 문법이다.
- 한 클래스 내에서 동일한 이름의 메서드라도 `매개변수의 개수와 타입만 다르다`면 **다른 메서드** 로 인식하는 것

<메서드 overloading 유형>

- 매개변수의 개수와 타입이 모두 다른 경우 (O)
- 리턴 타입이 다른 경우 (X)  
  -> 메서드 overloading에서 리턴 타입은 무시되므로 오류
- 매개변수의 개수와 타입이 같지만 순서가 다른 경우 (O)

<br>

### 1-2. 생성자 overloading

하나의 클래스는 매개변수의 유형과 개수를 달리해서 여러 개의 생성자를 가질 수 있다.

자바가 생성자 overloading을 지원하는 이유는?

- 클래스로부터 객체를 생성할 때 필요한 변수들만 적절히 초기화하기 위해서

<br>

```java
public Employee (String name, int age) {
  this.name = name;
  this.age = age;
}
public Employee (String name, int salary) {
  this.name = name;
  this.salary = salary
}
```

이 경우, 생성자의 매개변수 타입과 개수가 같으므로 overloading이 아닌 오류이다.

```java
public Employee (String name, int age) {
  this.name = name;
  this.age = age;
}
public Employee (int salary, String name) {
  this.salary = salary;
  this.name = name;
}
```

그럴 땐, 이렇게 매개변수의 순서를 변경해주면 overloading이 됨

<br>

### 1-3. this()

같은 클래스 내의 overloading 된 `다른 생성자 메서드를 호출`할 때 사용함

```java
public Employee() {
  this(0, "Anonymity", 0, 0);
}

public Employee(int employeeNo, String name) {
  this.employeeNo = employeeNo;
  this name = name;
}

public Employee(int employeeNo, String name, int age) {
  this(employeeNo, name);
  this.age = age;
}

public Employee(int employeeNo, String name, int age, int salary) {
  this(employeeNo, name, age);
  this.salary = salary;
}
```

<br>

## 2. Overriding

### 2-1. 메서드의 상속

부모 클래스가 가지고 있는 메서드가 자식 클래스로 상속되어 자식 클래스에서 사용할 수 있는 것

<br>

### 2-2. 메서드의 overriding

- 부모 클래스의 메서드를 재사용하지 않고 새롭게 정의하여 사용하는 것 (= `메서드 재정의`)
- 상속관계에 있는 클래스에서 자식 클래스가 부모 클래스의 `메서드를 재정의`해서 가지고 있는 것
- 자식 클래스에서 재정의된 메서드는 부모 클래스의 `메서드와 메서드 이름, 매개변수의 유형과 개수가 동일`해야 함

<br>

### 2-3. super()

자식 클래스에서 부모 클래스를 상속 받을 때 두 가지 방법이 있다.

- 부모 클래스의 메소드를 상속을 통해 그대로 재사용하는 방법
- overriding을 통해 부모 클래스의 메소드를 자식 클래스에서 재정의해서 사용하는 방법

만약 메서드를 overriding 하면서 부모 클래스의 메서드를 사용하고 싶다면?  
 -> 예약어 super를 사용하여 부모 클래스가 가진 메서드를 명시적으로 호출할 수 있다.

```java
class Camera {
  String name;
  int sheets;

  public void takePicture() {
    System.out.println(name + sheet + "장 찍는다");
  }
}

class PolaroidCamera extends Camera {
  int batteryGarage;

  public void takePicture() {
    super.takePicture();
    System.out.println(sheet + "장의 사진을 프린트한다.");
    System.out.println("배터리는 " + battery);
  }
}
```

Camera 클래스의 takePicture() 메서드를 super 예약어를 이용하여 명시적으로 호출하면서도 takePicture 메서드를 overriding(재정의)해서 사용가능하다.
