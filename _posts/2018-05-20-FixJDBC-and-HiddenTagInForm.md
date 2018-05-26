---
layout: post
title: "hidden 태그 사용과 db 에러 처리"
---
 
HTML 의 Form 태그를 이용해서 원하는 값을 jsp / Servlet 으로 넘겨줄 수 있다. 그때 hidden 태그를 사용하여 보이지 않는 값을 넘길 수 있다.
jsp 강의 예제 중 19번째 강의 예제에 있는 소스에 문제가 있었다. 
문제는 두가지인데 하나는 테이블 한 항목을 수정하면 전체가 바뀌는 것이었고, 그것을 수정하기 위해서는 SQL 의 where 구문을 사용해야만 했다.
두번째는 form 으로부터 id 값을 받아와야만 수정할 항목을 찾을 수 있는 데 그 부분이 빠져있었다.

예제로 하나의 항목에 대한 간단한 수정만 하면 되는 것이라 그냥 넘어가도 되겠지만 2 이상의 입력이 주어졌을때 한 항목을 수정하면 전체가 고쳐져서 덮어써지는 현상은 교육적으로 넘어가기가 어렵다.

(참고: 이후에 다른 문법으로 아래 내용을 쉽게 쓸 수 있다. )<br/>

<pre><code>String query = "select * from jsp_address";</code></pre>

위처럼 where가 없는 문장을

**String query = "select * from jsp_address where id = '" + id + "'";**

로 고쳐쓴다.

당연히 그 앞부분에서 id 를 가져온다.

id = (String)session.getAttribute("id");

---
```jsp
<form action="ModifyOk" method="post">
  이름 : <input type="text" name="name" size="10" value=<%=name %>><br />
  아이디 : <%=id %><br />
  비밀번호 : <input type="text" name="pw" size="10"><br />
  전화번호 : <select name="phone1">
    <option value="010">010</option>
    <option value="016">016</option>
    <option value="017">017</option>
    <option value="018">018</option>
    <option value="019">019</option>
    <option value="011">011</option>
  </select> - 
  <input type="text" name="phone2" size="5" value=<%=phone2 %>> - 
    <input type="text" name="phone3" size="5" value=<%=phone3 %>> <br />
  <%
  if(gender.equals("man")) {
  %>
  성별구분 : <input type="radio" name="gender" value="man" checked="checked">남  &nbsp;
    <input type="radio" name="gender" value="woman">여 <br />
  <%
  } else {
  %>
  성별구분 : <input type="radio" name="gender" value="man" >남 &nbsp;
    <input type="radio" name="gender" value="woman" checked="checked">여 <br />
  <%
  }
  %> 
  <input type="submit" value="정보수정"> <input type="reset" value="취소">
</form>
```
---

위의 기본 form 에서 <form> 과 </form> 사이에 적당한 곳에 행을 추가해서 

```jsp
<input type="hidden" name="id" value=<%=id %>>
```

를 넣는다.

hidden 타입은 화면에는 나오지 않지만 name 과 value 를 가지고 submit 을 했으때 값이 전달된다. 수정하고자하는 내용은 입력해야 하지만 항목번호인 id 값은 입력하지 않고 앞에서 가져온 값을 그대로 쓰고, 그대로 전달해주면 된다. 이때 hidden 태그를 사용할 수 있다.

단, 위의 내용은 소스보기를 통해 보여질 수 있고, 악의적인 접근이 가능하므로 id 값을 화면에 보여주지 않고 처리하기 위해서는 세션등을 사용할 수 있다.

전체소스 : https://github.com/eventia/jsp_lecture_2018/tree/master/zbc19

![View the Light](https://user-images.githubusercontent.com/3831276/40279649-1018e714-5c81-11e8-862b-7691f3719d0f.jpg "Girl with Light")




### Small image

![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)
![](https://guides.github.com/activities/hello-world/branching.png)

### Large image

![](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
