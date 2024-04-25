# JavaScript_prototype

### 소개
- 프로토타입 간의 관계를 이해하기 위해서 프로토타입를 기본 베이스로 만든 후 주제를 커피 주문 시스템으로 정하여 간단한 프로젝트를 만들었습니다. 

<br/> 

### 객체지향 프로토타입 모델링 ↓
![](https://velog.velcdn.com/images/sungwbs/post/3e501eb2-55d1-4b67-a322-d6b12a0bfab2/image.png)

<br/> 

### 1. 프로토타입으로 커피 주문 시스템 설계 내용
- Coffee 함수안에 있는 속성들을 Coffee_Shot prototype에 다중 프로토타입 체인을 하여 Coffee_Shot에서 속성을 사용하여 인스턴스를 생성할 수 있게 만들었습니다.

- Coffee_shot.prototype.constructor = Coffee_shot; 이 부분은 Coffee_shot 생성자 함수의 prototype.constructor 속성을 Coffee_shot으로 설정하기 위해 작성되었습니다. Shot을 얼마나 추가해 주었느냐에 따라 에스프레소 도피오가 될 수도 있고, 에스프레소 룽고가 될 수도 있습니다.

- 즉, Coffee에 있는 속성으로 "에스프레소", "tall" 객체를 만든 것을 사용 예시로 보여주고, Coffee의 속성을 Coffee_shot에서 받아오고 추가로 this.shot = shot; 속성을 추가하여 손님이 원하시는 커피 샷 횟수에 따른 새로운 인스턴스(커피)를 만들어 줍니다. 

( 실제로 에스프레소 2샷 = 도피오커피, 3샷 = 룽고커피가 됩니다 )
```c
const Coffee = function(name, size, ) {
    this.name = name;
    this.size = size;
    
  };
  
  Coffee.prototype.make = function() {
    return this.name + this.size;
  };
  
  const Espresso = new Coffee("에스프레소", "tall"); 
  console.log(Espresso);
  
  const Coffee_shot = function(name, size, shot) {
    Coffee.call(this, name, size, shot);
    this.shot = shot;
  };
  
  Coffee_shot.prototype = Object.create(Coffee.prototype);
  Coffee_shot.prototype.constructor = Coffee_shot;
  
  const Espresso_doppio = new Coffee_shot("에스프레소 도피오", "grande", 2);
  console.log(Espresso_doppio);
  
  const Espresso_Lungo = new Coffee_shot("에스프레소 룽고", "vante", 3);
  console.log(Espresso_Lungo);
  
```

<br/> 

### 참조한 코드와 모델링 ↓
![](https://velog.velcdn.com/images/sungwbs/post/af722ba9-5007-48fa-8429-34bdf95514e7/image.png)

![](https://velog.velcdn.com/images/sungwbs/post/2547f6d5-7e5d-4564-b1eb-9416b0f5e3df/image.png)

### 프로토타입 그림 자료 ↓
![](https://velog.velcdn.com/images/sungwbs/post/80d2235a-ae97-4e83-8a9c-486374f6390b/image.png)


> 커피의 기본 베이스가 에스프레소이기에 다양한 커피를 인스턴스로 뽑아내기 위해서는 코드에 샷 추가가 아닌 여러 요소들을 추가시켜서 다양한 커피를 만들 수도 있습니다.

![](https://velog.velcdn.com/images/sungwbs/post/2e23144c-cf9a-4b15-91ab-790e679b297f/image.jpg)

