# HashMap

## 1. HashMap이란?

- Map 인터페이스를 구현한 것으로 Map의 성질을 가지고 있어 **키(key)** 와 **값(value)** 을 하나로 묶은 Entry 객체를 저장하는 구조를 가진다. 이 때, 키와 값은 모두 객체이다.
- 값은 중복될 수 있지만 키는 중복될 수 없다. 만약 키가 중복된 값이 들어오면 해당 키에 저장되어 있던 기존의 값은 새로 들어온 값으로 바뀐다.
- HashMap은 해싱(hashing)을 사용하기 때문에 빠른 속도로 많은 양의 데이터를 검색할 수 있다.
- List와 달리 Map에는 순서가 없다.

<br>

## 2. HashMap 생성자/메서드

### HashMap 생성자

```java
HashMap<String, String> map1 = new HashMap<String, String>();     // new에서 타입 파라미터 생략 가능

HashMap<String, String> map2 = new HashMap<>(map1);     // map1의 모든 값을 다 포함한 HashMap 생성

HashMap<String, String> map3 = new HashMap<>(5);    // 초기 사이즈 지정

HashMap<String, String> map4 = new HashMap<>() {{
  put("a", "apple");
}};     // 초기 값 지정
```

HashMap은 저장공간을 초과해서 값이 들어오면 공간을 늘리는데 들어오는만큼 늘리는 것이 아니라 약 두 배로 늘립니다. 따라서 초기에 저장할 데이터의 개수를 알고 있다면 초기 사이즈를 지정해주는 것이 좋습니다.

---

### put() / get()

`put()`으로 key, value 쌍의 데이터를 저장하고, `get()`은 인자로 전달된 key에 해당하는 value를 리턴한다.
key가 존재하지 않으면 null을 리턴한다.

```java
HashMap<String, String> map = new HashMap<>();

map.put("a", "apple");
map.put("b", "banana");
map.put("c", "carrot");
map.put("a", "ant");

System.out.println(map.get("a"));
System.out.println(map.get("b"));
System.out.println(map.get("d"));
```

<출력>  
ant  
banana  
null

---

### remove() / clear()

`remove()`는 인자로 전달된 key에 해당하는 value를 리턴한 뒤 데이터를 삭제한다. 존재하지 않는 데이터일 경우 null을 리턴한다. `clear()`는 해당 HashMap의 모든 데이터를 삭제한다.

```java
System.out.println(map.remove("a"));
System.out.println(map.remove("c"));
System.out.println(map.remove("z"));
System.out.println(map);
```

<출력>  
apple  
carrot  
null  
map: {b=banana}

---

### isEmpty()

`isEmpty()`는 HashMap의 데이터가 비어있다면 true를, 아니면 false를 반환한다.

```java
HashMap<String, String> map = new HashMap<>();

map.put("a", "apple");
map.put("b", "banana");
map.put("c", "carrot");

System.out.println(map.isEmpty());
map.clear();
System.out.println(map.isEmpty());
```

<출력>  
false  
true

---

### containsKey() / containsValue()

`containsKey()`와 `containsValue()`는 인자로 전달된 key/value가 HashMap에 존재하면 true, 아니면 false를 반환한다.

```java
HashMap<String, String> map = new HashMap<>();

map.put("a", "apple");
map.put("b", "banana");
map.put("c", "carrot");

System.out.println(map.containsKey("a"));
System.out.println(map.containsValue("carrot"));
System.out.println(map.containsValue("tomato"));
```

<출력>  
true  
true  
false

---

### keySet() / values() / entrySet()

`keySet()`은 HashMap에서 key만 가져오고, `values()`은 HashMap에서 value를 가져오고, `entrySet()`은 key와 value를 다 가져온다. 주로 반복문을 이용해 전체 출력/탐색 시 사용된다.

```java
HashMap<String, String> map = new HashMap<>();

map.put("a", "apple");
map.put("b", "banana");
map.put("c", "carrot");

for (String key : map.keySet()) {
  System.out.print(map.get(key) + " ");
}

for (Map.Entry<String, String> entry : map.entrySet()) {
  System.out.println(entry + " ");
}
```

<출력>  
a b c  
a=apple b=banana c=carrot

---

### replace()

`replace()`는 인자로 전달되는 key의 value를 인자로 전달된 value로 바꾸어준다. 바뀌고 삭제되는 value가 리턴되고, 존재하지 않는 key가 인자로 전달되면 null을 반환한다.

```java
HashMap<String, String> map = new HashMap<>();

map.put("a", "apple");
map.put("b", "banana");
map.put("c", "carrot");

System.out.println(map.replace("a", "ant"));
System.out.println(map.replace("z", "zero"));
System.out.println(map);
```

<출력>  
apple  
null  
map: {b=banana, a=ant, c=carrot}
