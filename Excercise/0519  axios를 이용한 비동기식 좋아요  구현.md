# 0519  axios를 이용한 비동기식 좋아요  구현

### 기존 방식

좋아요 구현을 위해 버튼 대신 <a>태그를 이용했기 떄문에 누를 때마다 새로고침을 해야했다.

### 비동기식 방법

1. <a>태그를 없애고 <i>태그에 바로 클릭했을 때 addEventListener를 이용하여 클릭을 감지

   ```html
   {% if user in article.like_users.all %}
        <i class="fas fa-heart fa-lg like-btn" data-pk="{{article.pk}}" style="color:crimson"></i>
       {% else %}
       <i class="fas fa-heart fa-lg like-btn" data-pk="{{article.pk}}" style="color:black"></i>
       {% endif %}
   ```

   

2. qeurySelector로 모든 <i>들을 가져옴 -> class이름으로. 

3. forEach로 버튼(i) 하나하나에 이벤트 달아줌

4. 버튼을 누를대마다 Django server에 axios.get(url)으로 views.py에 함수를 호출함

5. `dataset`을 이용해서 장고 속성값을 이용. -> article.pk와 같은 url위해서도 사용됨

   #### JS에서 Django 데이터 속성 이용하기 -` dataset`

   > data-pk에서 data-빼고 뒤에꺼 lowerCamel이름컨벤션으로 가져와서 dataset.뒤에 붙이면 JS에서 사용 가능 

   ```javascript
   {% if user in article.like_users.all %}
        <i class="fas fa-heart fa-lg like-btn" data-pk="{{article.pk}}" style="color:crimson"></i>
       {% else %}
       <i class="fas fa-heart fa-lg like-btn" data-pk="{{article.pk}}" style="color:black"></i>
       {% endif %}
   //data-pk="{{article.pk}}"을 추가하였다.  
       
   axios.get(`/articles/${btn.dataset.pk}/like/`)
        //그래서 btn.dataset.pk사용가능
   ```

   