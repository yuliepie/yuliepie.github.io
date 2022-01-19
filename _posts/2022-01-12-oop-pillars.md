---
layout: post
title: OOP - 객체지향형 프로그래밍
tag: Programming
image: /assets/images/oop-pillars.jpg
---
![]({{ page.image | relative_url }}){: width="250" }

# Programming Paradigm & OOP

**OOP - Object Oriented Programming**은 가장 많이 쓰이는 프로그래밍 방식 중 하나이다. 이러한 프로그래밍 방식을 **프로그래밍 패러다임**이라고 하는데, 소프트웨어를 만들기 위한 프로그래밍 작업을 할때 따르게 되는 **개념, 규칙, 전략 등을 포함한 프로그래밍 방법론**이라고 볼 수 있다.

모든 프로그래밍 언어는 한가지 이상의 프로그래밍 패러다임을 적용한다 (꼭 한가지만 100% 적용하는 것은 아니다). 예를 들어 **Java는 OOP**의 특성을 강하게 지닌 언어로 유명하다. Python, Javascript 같은 경우는 OOP 언어로도 쓰이지만 functional programming 언어로도 사용할 수 있다. 

프로그래밍 패러다임은 여러종류가 있지만 크게 두가지 브랜치로 나뉘게 된다 - **Imperative, Declarative (명령형, 선언형)**. OOP 패러다임은 전자, 명령형 패러다임에 속한다. 몇가지 다른 패러다임으론 Logical programming, Procedural programming, Functional programming 등이 있다.

프로그래밍 패러다임은 각자 특성이 매우 다르고, 장점과 단점을 지니고 있는데, 어떤 프로그래밍 패러다임을 사용할지는 결국 선택에 달려있다. 개발자들의 선호, 그리고 개발하려는 소프트웨어의 특징과 목표에 따른다.

## OOP - 객체지향형 프로그래밍

객체지향형 프로그래밍 패러다임은 이름이 설명하듯이, ‘객체’를 주된 단위로 하며, 데이터를 **'클래스'와 '객체'**로 만들어 관리하게 된다. 객체가 담고 있는 데이터는 지속적으로 비즈니스 로직에 의해 바뀌게 되며, 데이터-중심적인 패러다임이라고 할 수 있겠다.

### Class (클래스)

클래스란 객체의 베이스가 되는 blueprint, 즉 설계도라고 볼 수 있다. 즉 클래스로 특정 종류의 객체들을 찍어내는 것이다. 클래스는 특정 엔터티에 대한 자료구조를 대표한다고 볼 수 있다. 예) 동물 class

클래스는 state, behaviour 즉 상태와 액션을 포함한다.

### Attributes (변수)

클래스의 변수들은 객체가 담을 데이터를 명시한다.

예) 동물 class - 종류, 다리개수, 크기, 식성...

### Methods (메서드)

메서드는 클래스의 객체가 실행할 수 있는 함수를 뜻하며, 보통 객체의 변수들이 가진 데이터를 조회하거나 바꾸는 기능을 한다. 일반 함수와 달리 클래스의 메서드는 클래스의 객체를 만든다음, 그 객체를 통해 호출하게 된다.

### Object (객체)

클래스를 이용해 생성된 하나의 인스턴스, 즉 설계도에 따라 만들어진 객체이다. 클래스에서 미리 정의한 변수들과 메서드를 가진 채 만들어지게 된다.

객체는 소프트웨어의 비즈니스 도메인에 관련된 실제 entity를 대표한다. 예를 들어 사람, 동물, 페북유저 등... 어떤 객체들로 데이터를 표현할지, 그 객체들의 베이스가 되는 클래스들은 어떤것일지 소프트웨어 디자인과정에서 정하게 되는데, 이를 **‘data modeling’** 데이터 모델링이라고 한다.

예시로 페이스북 유저 클래스를 상상해보자. 변수로는 이름, 친구목록이 있고 메서드로는 친구추가, 글쓰기 기능이 있다.

```python
class FacebookUser:
    
    def __init__(self, name):
        self.name = name # 이름
        self.friends = [] # 친구 목록
        self.posts = []

    def addFriend(newFriend)
        self.friends.append(newFriend)

    def addPost(content):
        self.posts.append(content)

# 객체 만들기
yulie = FacebookUser("정율리")
soondoong = FacebookUser("순둥이")

# 메서드 사용
yulie.addFriend(soondoong)
```

# 4 Principles of OOP
### OOP의 네 가지 기둥

흔히 OOP의 기둥이라고 불리는 네 가지 원칙이 있는데, 바로 Encapsulation, Inheritance, Polymorphism, Abstraction 이다.

## Encapsulation (캡슐화)

캡슐화의 원칙에 의하면 객체는 꼭 필요한 정보와 메서드만 외부세계에서 열람 가능하도록 한다. 변수를 캡슐화 시킨다는 것의 의미는, 외부 코드 즉 클래스의 바깥에서는 그 변수를 볼 수도 조작할 수도 없다는 뜻이 된다. 숨겨진 변수를 조작하는 것은 클래스 내부에서만 가능하다.

이런 캡슐화는 private, public 변수, 메서드 등으로 이루어지게 되며, 클래스 외부에서는 오직 퍼블릭 변수, 퍼블릭 메소드만 사용 가능하다.

### 캡슐화가 중요한 이유는?
클래스 바깥에서 모든 데이터가 조작가능하다면 실수로 데이터를 덮어써버리거나, 비즈니스 로직에 맞지않는 데이터 수정이 이루어질 가능성이 있다.

예를 들어 위에서 언급한 페이스북 친구 추가 기능이 있다고 치자. 만약 비즈니스 로직에 따라서 친구를 중복으로 추가할 수 없고, 친구추가를 할때 1000명 이상이면 추가를 할 수 없게 되어있다고 한다면? 

```python
# 페이스북 앱
soondoong2 = FacebookUser("순둥이")
yulie.friends.append(soondoong2) # 중복추가!
```

FacebookUser 클래스의 friends 변수가 캡슐화 되어있지 않기때문에, 외부 코드에서 그냥 append를 써서 중복친구를 추가해버릴 수 있고, 친구가 1000명이 넘었어도 그냥 추가해버리는 실수가 발생할 수 있다.    

특히 여러 개발팀이 협업을 해야하고, 친구 추가 기능이 여러군데에 포진해 있을 경우에 이런 비즈니스 로직을 기억해서 일일이 추가하는 것은 좋은 방법이 아니다.

```python
class FacebookUser:
    __friends = [] # PRIVATE 변수
    __posts = []

    def __init__(self, name):
        self.name = name # 이름

    def addFriend(newFriend):
        if newFriend not in self.__friends and len(self.__friends < 1000): # 비즈니스 로직
            self.__friends.append(newFriend)

    def addPost(content):
        self.__posts.append(content)


# 페이스북 앱
yulie.__friends # 안보임!!
yulie.addFriend("순둥이") # 반드시 메서드를 통해 친구추가
```

이런식으로 변수들을 캡슐화해서 외부에선 직접적으로 변수를 조작하는 대신 메서드를 이용하게 하면, 비즈니스 로직을 일관성있게 구현할 수 있고 버그를 방지할 수 있다.

## Inheritance (상속)

상속이란 클래스들 간에 부모-자식 관계를 형성해서 코드를 설계하는 방법이다. 자식 클래스는 부모 클래스의 변수와 메서드를 상속해서 쓸 수 있다. 이렇게 함으로써 코드의 재사용성을 높이고, DRY (Don’t Repeat Yourself) 원칙을 지킬 수 있다.

예를 들어 페북유저와 인스타그램유저 클래스가 있다고 하자. 두 클래스 다 친구목록, 이름 변수를 공유하기 때문에, ‘유저’라는 하나의 부모 클래스를 두고 그 클래스를 각자 상속함으로써 하나의 코드를 재사용할 수 있다.

```python
class User:
    __friends = []
    __posts = []

    # 공통 메서드
    def addFriend(newFriend)
        self.__friends.append(newFriend)

    def addPost(content):
        self.__posts.append(content)

class FacebookUser(User):
    # 페북유저용 변수/메서드들...
    __groups = []

    def joinFacebookGroup(group):
        self.__groups.append(group)

class InstagramUser(User):
    # 인스타유저용 변수/메서드들...
    __stories = []

    def addInstagramStory(story):
        self.__stories.append(story)
```

## Polymorphism (다형성)

다형성이란, 객체나 함수가 여러 형태를 가질 수 있다는 것을 의미한다. 보통 **함수의 다형성**으로 많이 나타나는데, **다른 두 종류의 클래스가 같은 함수이름**을 가지고 있는 것을 말한다. 다른 두 클래스이기 때문에 함수의 구체적 로직에 차이점이 있지만, 다형성을 이용해 그에 상관하지 않고 동일하게 사용되어 질 수 있다. 이를 함수의 overriding, 오버라이딩이라고 한다.

```python
class User:
    def addFriend(newFriend)
        pass

class FacebookUser(User):
    friends = [] # 친구목록

    def addFriend(newFriend):
        if len(self.friends) < 1000:
            self.friends.append(newFriend)
        

class InstagramUser(User):
    followers = [] # 팔로워목록

    def addFriend(newFriend):
        if len(self.friends) < 100000000:
            self.followers.append(newFriend)


# 페이스북 인스타 앱
facebook1 = FacebookUser("율리")
insta1 = InstagramUser("순둥")

user1 = User("복순")

for user in [facebook1, insta1]:
    user.addFriend(user1) # 다형성 메서드 호출
```

또한, 같은 클래스 내에서도 같은 이름의 함수가 두 개 이상 있을 수 있는데, 이는 함수의 overloading, 오버로딩이라고 한다. 함수의 시그니처로 작용하는 함수이름과 파라미터로 구별되어진다.

```python
class User:
    def addFriend(newFriend)
        pass

class FacebookUser(User):
    friends = [] # 친구목록

    def addFriend(newFriend):
        if len(self.friends) < 1000:
            self.friends.append(newFriend)

    def addFriend(newFriend, sendAlert): # 같은 함수이름, 다른 파라미터
        if len(self.friends) < 1000:
            self.friends.append(newFriend)

        if sendAlert:
            sendAlert(newFriend)


# 페이스북 인스타 앱
yulie = FacebookUser("율리")
user1 = User("복순")

yulie.addFriend(user1)
yulie.addFriend(user1, True) # 같은이름의 다형성 함수
```

## Abstraction (추상화)

마지막으로 추상화라는 것은, 객체가 외부에 공개하는 **퍼블릭 메서드들은 메서드의 이름과 용도만 공개할 뿐, 구체적인 로직은 상관없이 사용할 수 있다**는 것이다.

이는 캡슐화랑 다형성이랑도 깊게 밀접이 되어있는 개념인데, 캡슐화에 따르면 객체의 데이터는 퍼블릭 메서드로만 조작 가능하며, 추상화를 통해 그 구체적인 조작로직은 사용자가 알 필요가 없고 그저 호출을 하기만 하면 되는 것이다. 

또한 다형성을 통해 그 객체에 따른 올바른 로직의 함수가 호출되게 되며, 함수를 호출하는 사용자는 해당 로직에 대해 추가로 더 확인하거나 할 필요가 없는 것이다.

위 다형성 예시를 보면 이 개념이 적용되어지는데, 외부 앱에선 사용자가 페북유저인지, 인스타그램 유저인지 if 문을 통해 확인하거나 할 필요 없이 그저 `addfriend` 함수를 호출하여 친구를 추가하기만 하면 되는 것이다.

## OOP의 장점과 단점

### 장점

- 비즈니스 도메인의 데이터를 객체화 하는 것을 통해 가독성을 높일 수 있다.
- 상속을 통해 코드의 재사용성을 높일 수 있고, 이를 통해 개발자의 시간을 아낄 수 있다.
- 캡슐화를 통해 데이터의 안전성을 확보할 수 있다.
- 캡슐화, 추상화를 통해 모듈러한 코드, 즉 수정과 테스트가 용이한 코드를 작성할 수 있다.

### 단점

- 데이터에 치중되어진 패러다임으로, 알고리즘이나 기능적인 면을 덜 중시한다.
- 클래스 위주로 코드를 작성해야 해서 시간이 더 걸릴 수 있으며 컴파일 시간이 늘어날 수 있다.