# 0519 exercise

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>exercise</title>
</head>
<body>
  <h1>Dog Image(s)</h1>
  <hr>

  <h2>강아지</h2>
  <div class="dogs"></div>
  <button id="dog">강아지</button>

  <script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
  
    <script>
    // 밥상
    
    const dogs = document.querySelector('.dogs')
    const dogBtn = document.querySelector('#dog')

    dogBtn.addEventListener('click',function(event){
      console.log('버튼이 눌렸습니다.')
      // event.preventDefault()
      axios.get('https://dog.ceo/api/breeds/image/random')
      .then(function(img){
        console.log(img.data)
        const dogImage = document.createElement('img')
        dogImage.src = img.data.message
        dogImage.style.height = '300px'
        dogs.append(dogImage)
        
      })
      .catch(function(err){
        console.log(err)
      })
    })


//---------------------------cat----------------------------

const cats = document.querySelector('body')
const border = document.createElement('hr')


const catTitle = document.createElement('h2')
catTitle.innerText = "고양이"

const catDiv = document.createElement('div')
catDiv.classList.add('d-flex')

const catBtn = document.createElement('button')
catBtn.innerText = "고양이"

cats.append(border,catTitle,catDiv,catBtn)


catBtn.addEventListener('click',function(event){
  axios.get('https://api.thecatapi.com/v1/images/search')
  .then(function(img){
      //고양이는 배열이기 때문에 인덱스로 접근 img.data[0]
      //배열의 원소가 오브젝트라서 .속성명 으로 접근
    console.log(img.data[0].url)
   
    const catPics = document.createElement('img')
    catPics.src = img.data[0].url
    catDiv.append(catPics)
  })
  .catch(function(err){
    console.log(err)
  })
})

  </script>
</body>
</html>
```

* 객체 접근(dog)

```javascript
console.log(img.data)
        const dogImage = document.createElement('img')
        dogImage.src = img.data.message
        dogImage.style.height = '300px'
        dogs.append(dogImage)
```

* 배열 접근(cat)

```javascript
//고양이는 배열이기 때문에 인덱스로 접근 img.data[0]
      //배열의 원소가 오브젝트라서 .속성명 으로 접근
    console.log(img.data[0].url)
   
    const catPics = document.createElement('img')
    catPics.src = img.data[0].url
    catDiv.append(catPics)
```

