# JS Destructuring 비구조화

* 비구조화로 object저장하는 방법

```javascript
const Student = {
    name : '정승희',
    course : 'Vue.js',
    email : 'abc@com',
    phone : '01012345678'
    
}

//1. 기존방법
const name = Student.name
const course = Student.course
const email = Student.email
const phone = Student.phone

//2. key와 변수명이 같아야 한다.
const {name} = Student
const {course} = Student
const {email} = Student
const {phone} = Student

//3. 제일 간단. key와 변수명이 같아야 한다.
const {name, course, email, phone} = Student

console.log(name,course,email,phone)
```



```javascript
//들어오는 인자 1개다.(4개 아님). 하지만 함수 안에서는 4개로 흩어져 있는 것 처럼 쓸 수 있다.
function saveStudent({name,course,email,phone}) {
    return `${name}, ${course},${email}, ${phone}`
}
//들어오는 인자 1개. 그러나 object의 4개 속성 중 2개만 쓰겠다.
function saveStudent2({name,course}) {
    return `${name}, ${course}`
}
```

