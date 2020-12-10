# Django

### Django란 무엇일까

* 웹을 `쉽고 빠르게` 만들 수 있도록 도와주는 웹 프레임워크
* `Python 기반 웹 프레임워크`, 풀스택 프레임워크이다. 일반적으로 파이썬을 웹 사이트 구축에 쓴다면 django 또는 flask를 사용한다. 

### 주요 특징

* MVC 패턴이 아닌 MTV 패턴을 사용
* ORM 기본 제공

  * 이는 아래에서 자세히 다뤄보자.

* DBMS의 경우 SQLite를 사용
* Django Admin을 통해 관리자 페이지로 간편하게 CRUD를 할 수 있게 해줌
* 로그인, DB, 관리자 기능 등 기본적으로 제공하는 기능들이 많기 때문에 이를 잘 익혀서 사용만 하면 됨

### ORM?

* ORM(Object-Relational Mapping)객체 관계 매핑이란 무엇일까?

### 장고 템플릿 언어

* 파이썬의 변수 및 문법을 HTML 문서 안에서 사용할 수 있게 장고에서 지원하는 언어

* 따라서 기존 HTML, 파이썬과 조금씩 다르다.

* 변수는 {{ 변수 }} :  띄어쓰기는 불허용.  _ 와 대소문자를 이용해서 표현 해줌. 또한 ' . ' 을 이용해서 변수의 속성으로 접근 가능 e.g.) {{ article.headline }}

* 필터 | 파이프 :  필터를 적용해 변수에 효과를 줄 수 있음. 장고에서는 약 30개의 필터 제공  e.g.)  {{ article.pub_date|date:"F j, Y" }}

* 태그 {% Tag %}: 일반적으로 if문, for문 등에 쓰이며 장고에서는 약 24개의 기본 태그 제공

  e.g.) 

  ```html
  {% for athlete in athlete_list %}
      <li>{{ athlete.name }}</li>
  {% endfor %}
  ```
  
* 템플릿 상속

  : 장고 템플릿에서 가장 유용한 부분이 바로 템플릿 상속. 네비게이션바 또는 하단 바와 같이 웹사이트의 공통이 되는 부분을 모든 하위 템플릿에서 상속 받아 사용할 수 있게끔 해줌. 

  

  * base.html -> 상속이 될 상위 템플릿 👇
  * 이때 {%  block %} {% endblock %} 태그 안에는 하위 템플릿의 내용이 삽입됨.

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <link rel="stylesheet" href="style.css">
      <title>{% block title %}My amazing site{% endblock %}</title>
  </head>
  
  <body>
      <div id="content">
          {% block content %}{% endblock %}
      </div>
  </body>
  </html>
  ```

  * 상속을 받는 하위 템플릿👇
  * 기본적으로 base.html이나 nav.html에 정의를 해서 하위 템플릿에서 extends태그('확장의 의미')를 통해 -> {% extends "base.html" %} 상속받음.
  * 블록 태그 안에 있는 내용이 화면에 출력

  ```html
  {% extends "base.html" %}
  
  {% block title %}My amazing blog{% endblock %}
  
  {% block content %}
  {% for entry in blog_entries %}
      <h2>{{ entry.title }}</h2>
      <p>{{ entry.body }}</p>
  {% endfor %}
  {% endblock %}
  ```

  

[참고문헌](https://docs.djangoproject.com/ko/3.1/ref/templates/builtins/#std:templatetag-block)

