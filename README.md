# JSP 웹 프로그래밍 기초
JSP 같은 동적 웹 페이지는 클라이언트가 어떤 문서를 요청했을 때,
 해당 웹 페이지는 'JSP 컨테이너'를 거쳐 새롭게 해석된 후,
 HTML 태그로 바꿔 전송한다. 이런 처리를 통해 사용자들은 각각 다른 출력 결과를 볼 수 있다.
 
## 서버로 데이터를 전달하는 방법
### GET
* 웹 브라우저의 URL 창에 파라미터의 정보를 담아 전송하는 방식
* 보안에 취약하며 정보의 크기가 1024로 제한

### POST
* 정보의 크기에 제한 없이 전송 가능
* URL 주소창에 전송하려는 데이터의 정보가 없으므로 보안성에 좋음

---

## Wiki
* [JSP_페이지의_구성_요소](https://github.com/MinGOODdev/Web-Programming-Base/wiki/JSP-%ED%8E%98%EC%9D%B4%EC%A7%80%EC%9D%98-%EA%B5%AC%EC%84%B1-%EC%9A%94%EC%86%8C)
---

## 자바빈 (JavaBeans)
* 웹 프로그래밍에서 데이터의 표현을 목적으로 사용
* 일반적인 구성은 다음과 같습니다.
    * 값을 저장하기 위한 필드
    * 값을 수정하기 위한 setter
    * 값을 읽기 위한 getter
    
### 자바빈 프로퍼티
* 프로퍼티는 자바빈에 저장되어 있는 값을 표현
* 메소드 이름을 사용하여 프로퍼티의 이름을 결정
* 규칙: 프로퍼티 이름이 propertyName 일 경우
```java
setter: public void setPropertyName(Type Value);
getter: public Type getPropertyName();
boolean 타입일 경우 getter 에 get 대신 is 사용 가능
배열 지정 가능: 예) public void setNames(String[] values);
```
* 읽기/쓰기
    * 읽기 전용: get 또는 is 메소단 존재하는 프로퍼티
    * 읽기/쓰기: get/set 또는 is/set 메소드가 존재하는 프로퍼티
    
### jsp:useBean 태그
* JSP 에서 자바빈 객체를 생성할 때 사용
* 구문
```html
<jsp:useBean id="[빈이름]" class="[자바빈클래스이름]" scope="[범위]"/>
```
* id: JSP 페이지에서 자바빈 객체에 접근할 때 사용할 이름
* class: 패키지 이름을 포함한 자바빈 클래스의 완전한 이름
* scope: 자바빈 객체가 저장될 영역을 지정한다.
    > page, request, session, application 중 하나를 값으로 갖는다. 기본값은 page

### jsp:setProperty 태그
* 자바빈 객체의 프로퍼티 값 설정
* 구문
```html
<jsp:setProperty name="id" property="이름" value="값"/>
```
* name: 자바빈 객체의 이름
* property: 값을 설정할 프로퍼티
* value: 프로퍼티의 값
```html
<jsp:setProperty name="id" property="이름" param="파라미터이름"/>
```
* param: 프로퍼티의 값으로 사용할 파라미터 이름
```html
<jsp:setProperty name="id" property="*"/>
```
* 프로퍼티와 동일한 이름의 파라미터를 사용하여 값을 설정
* 폼에 입력한 값을 자바 객체에 저장할 때 유용하게 사용

### jsp:getProperty 액션 태그
* 프로퍼티의 값을 출력하기 위해 사용
* 구문
```html
<jsp:getProperty name="자바빈" property="프로퍼티"/>

```