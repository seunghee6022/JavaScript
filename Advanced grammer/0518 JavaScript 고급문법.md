# JavaScript 고급

`shift`+`enter` : 줄바꿈

---



* JS 는 함수 인자개수

JS 는 함수 인자개수가 달라도 에러가 아니라 동작한다.

인자수가 적으면 undefined로 많으면 무시

* unpack : `...<언팩할 변수명>`

```javascript
numbers = [1,2,3,4,5]

function rest(...numbers){
	console.log(numbers)
}

-> 1,2,3,4,5
```



---

### Bootstrap card js ver

* boostrap card

```html

```

* js card

> * 생성 : `const card = document.createElement('div')`
> * 클래스 생성 : `card.classList.add('card','col-4')`

```html
<body>
    
</body>


<stript>
    # 카드 생성
	const card = document.createElement('div')
    card.classList.add('card','col-4')
    
    # 카드 상단 이미지
    const cardImage = document.createElement('img')
    cardImage.src = 'https://picsum.photos/200'
    cardImage.classList.add('card-image-top')
    cardImage.alt = 'ramdon-image'
    
    # 카드 바디
    const cardBody = document.createElement('div')
    cardBody.classList.add('card-body')
    
    # 카드 타이틀
    const cardTitle = document.createElement('h5')
    cardTitle.classList.add('card-title')
    cardTitle.innerText = 'Card Title'
    
    
    
    #
    
    const cardArea = document.querySelector('#cardArea')
    card.append()
    card.append()
    
    
</stript>
```



---

### Helper Method

> Array에서 주로 사용 
>
> `forEach`,  `map`, `filter`, `reduce`
>
> `forEach`,  `map`, `filter` => 인자로 함수 자체를 받는다. JS에선 자연스러움.(익명함수 주로 사용. 한번만 사용할 함수에 의해)

	#### 	Callback함수

​	인자로 넘어간 함수가 때가되면 실행된다.

​	`forEach`,  `map`, `filter` => 인자로 함수 자체를 받는다. JS에선 자연스러움.(익명함수 	주로 	사용. 한번만 사용할 함수에 의해)



1.  forEach : 주어진 배열에 있는 각 요소에 대해 오름차순으로 한번씩 실행.  for문보다 더 쉽게 사용가능

   * images각 요소를 img자리에 넣고 나머지는 알아서 하세요. 리턴 없습니다.

   ```javascript
   const images =[
   	{height: 10, width : 30},
   	{height: 20, width : 90},
   	{height: 40, width : 50},
   ]
   
   const area = []
   //이미지 안의 요소들로 반복을 하면서
   //img라고 매개변수 지정해주면 -> for문 돌면서 img에 값을 넣어줘서 사용 가능
   images.forEach(function(img){
                 area.push(img.height*img.width)
                 })
   ```

   `shift`+`enter` : 줄바꿈

   ```javascript
   const posts = [
         { id: 23, title: 'Daily JS News' },
         { id: 52, title: 'Code Refactor City' },
         { id: 105, title: 'The Brightest Ruby' }
       ]
   
   posts.forEach(function(post){
       console.log(post)
       console.log(post.id)
       console.log(post.title)
   })
   
   결과값
   {id: 23, title: "Daily JS News"}
   23
   Daily JS News
   {id: 52, title: "Code Refactor City"}
   52
   Code Refactor City
   {id: 105, title: "The Brightest Ruby"}
   105
   The Brightest Ruby
   ```

2.  map : 배열 내의 요소에 대해 주어진 callback함수를 실행하며, 그 함수의 return값을 요소로 하는 새로운 배열을 만들어줌

   ```javascript
   const numbers = [1,2,3]
   const double = numbers.map(function(num){
       return num*2 //이 리턴값을 가지고 map에서 새로운 배열을 만들어줌, 원본배열은 그대로. 새 배열을 리턴해줌
   })
   
   console.log(numbers)
   console.log(double)
   ```

   ```javascript
   const numbers = [0,9,99]
   function addOne(number){
       return number+1
   }
   const newNumber1 = numbers.map(addOne)
   //[0,9,99]를 순회하며, 각 요소를 (number) 자리에 넣는다.
   //그리고 리턴된 값을 새로운 배열에 넣고 마지막에 리턴한다.
   const newNumber2 = [0,9,99].map(function(number){
       return number+1
   })
   
   console.log(newNumber1, newNumber2) //=>둘다 [1,10,100]
   ```

   

3. filter : callback함수의 테스트를 통과하는 모든 요소를 모아서 새로운 배열로 반환

   ```javascript
   const products = [
       {name:'cucumber', type:'vegetable'},
       {name:'banana', type:'fruit'},
       {name:'carrot', type:'vegetable'}
                    ]
   
   const vegt = products.filter(function(product){
       return product.type === 'vegetable' 
       //비교된 값이 true인 경우에만 그 값들로 배열을 만들어 리턴해줌
   })
   
   const newNumber2 = [0,9,99].filter(function(number){
       return number%2 //홀수만 모아서 배열return
   })
   
   
   console.log(vegt)
   ```

4. reduce : 배열의 각 요소에 대해 callback 함수를 실행하고, 하나의 결과 값을 반환

   > `arr.reduce(callback(acc, element,index,array){}, initialValue)`
   >
   > 1. `accumulator`, 맨 마지막에 초기값을 지정해줄 수 있다. 아니면 배열의 맨 첫번째 값 자동설정됨
   >
   > 2. `currentValue` : 현재 받아오는 값
   >
   > 3. `currentIndex`  (optional) : 현재 받아오는 값의 인덱스 , initialValue적용한 경우 0부터 시작 아니면 1부터 시작
   >
   > 4. `array` (optional) : 받아오는 배열
   >
   > `initialValue`(optional) 지정안해주면 배열의 첫번쨰 값이 초기값
   >
   > 어떤 값을 계속 저장할 수 있다. 다른 것들은 각각의 요소에 대한 결과값을 보냈다면 reduce라는 helpmethod는 누적을 할 수 있게끔 하나의 변수(accumulator e.g. total)를 사용할 수 있다. 뒤에 오는 매개변수는 currentValue()

   ```javascript
   const tests = [90,91,80,100,95,79]
   
   //콜백함수의 첫번쨰 매개변수값이 누적되어질 변수, 뒤가 배열에서 하나씩 받을 값
   const sum = tests.reduce(function(total,test){
       return total+test //최종 total값이 sum으로 반환되어짐
   }, initialValue(accumulator의 초기값(안적으면 배열의 첫번째 요소가 초기값됨 e.g. 90))
   
   console.log(sum)
   ```

5.  find : 배열에서 콜백함수를 만족하는 첫번째 요소의 값을 반환. 만족하는 값이 없으면 undefined

6. some : 배열안의 어떤 요소라도 판별함수(콜백에서 특정 조건을 만족)를 통과하는지 테스트 하는데 하나라도 통과하면 true return

7. every : 배열안의 모든 요소가 판별함수를 통과해야 true





---

## Live2 - 콜백함수, EventListener , this

### 콜백함수

인자로 함수를 넘긴다.

미래에 조건이 맞아서 때가되면 알아서 실행된다.

---

### EventListener

* eventListener : 이벤트가 생기길 기다렸다가 생기면...
  * 재사용성 떨어짐
  * 유지보수 떨어짐

```html
<body>
    <button id='myButton' onclick="confirmMessage">얍</button>
    <script>
        function confirmMessage(event){
            confirm('얍?')
        }
    </script>
    
</body>
```



* addEventListener

```html
<body>
    <button id='myButton' onclick="confirmMessage">얍</button>
    <script>
        const myButton = document.querySelector('myButton')
        function confirmMessage(event){
            confirm('얍?')
        }
        //요소 .addEventListener('이벤트',이벤트 발생시 실행할 함수)
        // 1번
        myButton.addEventListener('click',confirmMessage)
        // 2번 - 함수 인자로 바로 주기
        myButton.addEventListener('click',function(event){
            confirm('얍?')
        })
    </script>
    
</body>
```

* 버튼 실행 위해
  * 버튼을 잡아서
  * 버튼이 눌리면
  * 실행해야

```html

```

* Input 태그 내용 잡을 때 `.value` 사용



---

### this

>  무조건 어떤 object를 지칭

* JS는 OOP 언어이다. ( 파이썬에서 객체는 인스턴스를 말함. 자바스크립트에서 객체는 object말함,,,배열도 객체고 객체 아닌게 없는 수준)

* 무조건 어떤 object를 지칭

* method => 객체안에 정의된 함수.(.methodName()으로 실행하는 함수)

* function=> (이해를 위해 지금만) method가 아닌 모든 함수

* this가 주의해야하는시점  : function( ){} 정의할 때, 

* this가 window가 아닌 경우.

  1. method안의 this --> 해당 method가 정의된 객체(object)
  2. 생성자 함수 안의 this

  이걸 제외하고는 무조건 window나옴

  ```javascript
  const obj = {
      name:'obj',
      method1 : function(){
      sonsole.log(this) //this : obj
      },
      objInObj:{
          name:'oio',
          //oioMethod : function(){} -> 아래와 완전히 같음
          
          oioMethod(){ //syntectic sugar 
          console.log(this) // objInObj : 해당 method가 정의된 객체
          }
      },
      //--------------------------------------------
      arr:[0,1,2],
      newArr : [],
      method2(){
          //console.log(this) //해당 method가 정의된 객체 : obj
          
          //arr사용하고 싶다.
          this.arr.forEach(
              function(number){
              this.newArr.push(number*100) 
                  //실행불가 this : window로 뜸 -> 왜? (.methodName()으로 실행하는 함수
          }.bind(this) //로 해결가능 . 한 스코프 위로 올려준다는 의미. 		this.arr.forEach(의 this를 가리키게 됨
              
          //화살표 함수 사용 : 똑같이 동작
              (number) => {
                  this.newArr.push(number*100)
              }
          
          )
      }
  }
  ```

* 화살표 함수 역할 : this의 bind를 알아서 한 스코프 위로 잡아줌

  ```javascript
   //화살표 함수 사용 : 똑같이 동작
              (number) => {
                  this.newArr.push(number*100)
              }
  ```

  



#### 정리

* method 정의할 때 반드시 function(){}로 정의한다.

* syntectic sugar 

  ```javascript
  oioMethod(){ //syntectic sugar 
          console.log(this) // objInObj : 해당 method가 정의된 객체
          }
  ```

  