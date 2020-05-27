# 0518 JS Exercise  

### : DOM 조작을 활용한 Todo List 뼈대 코드 작성하기

---

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>0518 exercise & workshop</title>
</head>
<body>
  <h2>Add New Todo</h2>
  <p id='newToDo'></p>
  <hr>

  <h2>Todo List</h2>
  <ul id='toDoList'></ul>
  <hr>

  <h2>Completed Tasks</h2>
  <ul></ul>
  <hr>

  <script>
    //밥상을 가져오고
    //밥그릇을 가져와서
    //밥을 채우고
    //밥상위에 놓기
    const newToDo = document.querySelector('#newToDo')

    const newToDoForm = document.createElement('form')

    const newToDoLabel = document.createElement('label')
    newToDoLabel.innerText = 'Add New Todo:'

    // input tag에 타입 부여해야
    const newToDoInput = document.createElement('input')
    newToDoInput.type = 'text' 

    const newToDoButton = document.createElement('button')
    newToDoButton.innerText = 'Add'

    // newToDoForm해당 메모리의 주소값을 가리키는 참조를 하기 때문에 순서 상관 없다.
    
    newToDoForm.append(newToDoLabel,newToDoInput,newToDoButton)
    newToDo.append(newToDoForm)
  
    //----------------Todo List----------------
    const toDoList = document.querySelector('#toDoList')
    
  function createTodo(labelText){
      const toDoListForm = document.createElement('form')
      const toDoListElement = document.createElement('li')

      const modelFormCheck = document.createElement('input')
      modelFormCheck.type = 'checkbox'

      const modelFormLabel = document.createElement('label')
      modelFormLabel.innerText = `[${labelText} :]`

      const modelFormInput = document.createElement('input')
      modelFormInput.type = 'text' 

      const modelFormEditButton = document.createElement('button')
      modelFormEditButton.innerText = 'Edit'

      const modelFormDeleteButton = document.createElement('button')
      modelFormDeleteButton.innerText = 'Delete'

      toDoListElement.append(toDoListForm)
      toDoListForm.append(modelFormCheck,modelFormLabel,modelFormInput,modelFormEditButton,modelFormDeleteButton
      )
      return toDoListElement
  }

  const myTextList = [
    'Django ModelForm 복습',
    'Javascript DOM 조작 복습',
    'Django static, media 복습'
  ]
  myTextList.forEach(function(text){
    console.log(text)
    const toDoListElement = createTodo(text)
    toDoList.append(toDoListElement)
    
  })
  </script>
</body>
</html>
```

