# 4. 스프링 부트 애플리케이션 개발하기

## 4.1 프로젝트 생성

- 스프링 부트 프로젝트를 쉽게 만드는 방법으로
    1. ‘인텔리제이 IDEA 에서 프로젝트를 생성하는 방법’
    2. ‘Spring Initializr를 이용해 생성하는 방법’이 있다.

### 4.1.1 인텔리제이 IDEA에서 프로젝트 생성하기

- 인텔리제이 IDEA 얼티밋 버전은 커뮤니티 버전보다 많은 기능을 지원한다.
- 그 중 하나가 바로 내장된 Spring Initializr 이다.
- 이 기능을 이용하면 외부 프로젝트를 생성할 필요 없이 인텔리제이 IDEA 에서 곧바로 스프링 프로젝트를 생성할 수 있다.

- 인텔리제이 IDEA는 다양한 형식의 프로젝트를 지원한다.
- ‘Spring Initializr’ 는 원래 스프링 공식 사이트에서 제공하는 스프링 부트 프로젝트 생성 기능인데, 인텔리제이 IDEA에도 내장돼 있다.
- 아래와 같이 ‘Spring Initializr’를 선택하면 설정이 필요한 항목들이 나온다.

![스크린샷 2024-05-11 오전 12.42.42.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/1d90d5af-fa87-4872-8b0a-5ff9cca72a54/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.42.42.png)

- 각 항목에 대해 다음과 같이 설정한다.
    - Name : 프로젝트의 이름을 설정한다.
    - Location : 프로젝트를 생성할 위치를 설정한다.
    - Language : JVM 상에서 동작하는 언어를 선택한다. ‘Java’를 선택한다.
    - Type : 빌드 툴을 선택한다. 여기서는 Maven 으로 선택했는데 각자 익숙한 것을 선택해도 좋다.
    - Group : 이 프로젝트를 정의하는 고유한 식별자 정보인 그룹을 설정한다.
    - Artifact : 세부 프로젝트를 식별하는 정보를 기입한다.
    - Package name : Group과 Aritifact를 설정하면 자동으로 입력된다.
    - Project SDK : 11 버전으로 설정한다.
    - Java : 11 버전으로 설정한다.
    - Packaging : 애플리케이션을 쉽게 배포하고 동작하게 할 파일들의 패키징 옵션이다. ‘Jar’를 선택한다.
- 다음 단계로 프로젝트에서 사용할 의존성을 추가한다.
- 의존성은 초기에 추가할 수도 있고 개발을 진행 중에 추가할 수도 있다.
- 일단 아래와 같이 기본적인 의존성을 선택하고 넘어간다.

  ![스크린샷 2024-05-11 오전 12.46.54.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/94d81ee6-d211-4fbf-b95e-d28dfd6eddf1/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.46.54.png)

- 이 단계까지 마치면 인텔리제이 IDEA 우측 하단에 상태 표시줄이 나타나고, 그 사이에 인텔리제이 IDEA가 메이븐(Maven)을 통해 프로젝트를 초기화한다.
- 그리고 프로젝트에 필요한 의존성을 가져오고 필요한 색인 작업을 한다. 모든 작업이 완료되면 상태 표시중이 사라지면서 아래와 같은 화면을 볼 수 있다.

  ![스크린샷 2024-05-11 오전 12.47.49.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/de02f037-ed2d-4a05-b7d2-1fc5b9f32877/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.47.49.png)


### 4.1.2 스프링 공식 사이트에서 프로젝트 생성하기

- 만약 사용 중인 인텔리제이 IDEA가 커뮤니티 버전이라면 지금 소개하는 방법으로 프로젝트를 생성하는 것이 좋다.
- 스프링 공식 사이트에는 스프링 부트 프로젝트를 자동으로 만들어주는 서비스가 있다.
- https://start.spring.io

위 경로로 접속하면 아래와 같은 화면이 나온다. 이 페이지에서 각 항목을 선택하고 [Generate]버전을 누르면 설정이 적용된 프로젝트 파일을 내려 받을 수 있다.

![스크린샷 2024-05-11 오전 12.51.21.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/ad4a58c1-294d-4ac4-9dca-de109827702e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.51.21.png)

- 우선 각 항목에 대해 다음과 같이 설정한다.
    - Product : Maven Project
    - Language : Java
    - Spring Boot : 3.2.5
    - Project Metadata
        - Group : com.springboot
        - Artifact : hello
        - Name : hello
        - Description(자유롭게 서술 가능) : Demo project Spring Boot
        - Package Name(자동완성) : com.springboot.hello
        - Packaging: Jar
        - Java : 17
- 그리고 Dependencies 항목을 채우기 위해 [ADD DEPENDENCIES…]버튼을 클릭한다.
- 그럼 아래와 같이 의존성 추가 화면이 나온다.

![스크린샷 2024-05-11 오전 12.52.43.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/f3b69f45-9b12-4358-bcd6-05a60ba1f5d6/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.52.43.png)

- 맨 위 검색창을 활용하거나 마우스 스크롤을 내려 아래와 같이 항목을 추가한다.
    - Lombok
    - Spring Configuration Processor
    - Spring Web

![스크린샷 2024-05-11 오전 12.54.03.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/cb58fd6d-4043-4481-8ccc-b630332612b2/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.54.03.png)

- 모든 옵션을 선택하고 의존성까지 추가했다면 스프링 프로젝트를 생성할 준비가 끝났다.
- spring initializr 사이트 하단의 [GENERATE] 버튼을 클릭해 프로젝트를 내려 받는다.
- 내려받은 압축 파일을 프로젝트를 진행할 경로로 옮기고 압축을 푼 후 인텔리제이 IDEA를 실행하고 아래와 같이 프로젝트를 선택해 열어본다.
- 프로젝트를 처음 열면 몇 가지 초기화 작업이 진행된다.
- 그리고 아래와 같은 화면이 나오고 인텔리제이 IDEA 우측 하단에 표시된 진행 사항이 모두 완료되면 정상적으로 프로젝트를 이용할 수 있다

![스크린샷 2024-05-11 오전 12.56.27.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/9558d7a6-0e4e-475d-80b5-aff4087b0354/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12.56.27.png)

## 4.2 pom.xml(Project Object Model) 살펴보기

- pom.xml 파일은 메이븐의 기능을 사용하기 위해 작성하는 파일이다.
- 이 파일에는 프로젝트, 의존성 라이브러리, 빌드 등의 정보 및 해당 프로젝트를 관리하는 데 필요한 내용이 기술돼 있다.
- 이 파일을 살펴보기에 앞서 메이븐이라는 빌드 도구에 대해 먼저 살펴보겠다.

### 4.2.1 빌드 관리 도구

- 빌드 관리 도구는 JVM이나 WAS가 프로젝트를 인식하고 실행할 수 있게 우리가 작성한 소스코드와 프로젝트에 사용된 파일들(.xml, .jar. .properties)을 빌드하는 도구이다.
- 개발 규모가 커질수록 관리할 라이브러리가 많아지고 라이브러리 간 버전 호환성을 체크해야 하는 어려움이 발생하는데, 빌드 관리 도구를 이용하면 이 같은 문제를 해결할 수 있다.

### 4.2.2 메이븐

- 아파치 메이븐은 자바 기반의 프로젝트를 빌드하고 관리하는데 사용하는 도구이다.
- 초창기 자바 프로젝트의 대표적 관리 도구였던 Ant를 대체하기 위해 개발됐다.
- 메이븐의 가장 큰 특징은 pom.xml 파일에 필요한 라이브러리를 추가하면 해당 라이브러리에 필요한 라이브러리까지 함께 내려받아 관리한다는 점이다.
- 메이븐의 대표 기능을 다음과 같다.
    - 프로젝트 관리 : 프로젝트 버전과 아티팩트를 관리한다.
    - 빌드 및 패키징 : 의존성을 관리하고 설정된 패키지 형식으로 빌드를 수행한다.
    - 테스트 : 빌드를 수행하기 전에 단위 테스트를 통해 작성된 애플리케이션 코드의 정상 동작 여부를 확인한다.
    - 배포 : 빌드가 완료된 패키지를 원격 저장소에 배포한다.
- **메이븐의 생명주기**
    - 메이븐의 기능은 생명주기 순서에 따라 관리되고 동작한다.
    - 인텔리제이 IDEA에서 생성한 프로젝트의 경우 인텔리제이 IDEA에서 우측에 있는 ‘Maven’ 탭을 클릭하면 아래와 같이 메이븐의 생명주기를 확인할 수 있다.
- 메이븐의 생명주기는 크게 기본 생명주기(Default Lifecycle), 클린 생명주기(Clean Lifecycle), 사이트 생명주기(Site Lifecycle)의 3가지로 구분한다.
- 각 생명주기에는 아래와 같은 단계(phase)가 존재하며, 특정 단계를 수행하기 위해서는 이전 단계를 마쳐야 한다.

!https://user-images.githubusercontent.com/13410737/179552311-51e1ffd0-fbd1-4287-9a34-a4f940b70a8d.png

- 각 단계는 메이븐에서 제공하는 플러그인이 설정된 목표(goal)를 수행하는 방식으로 동작한다.
- 또한 그림에서 표현되지 않은 세부 단계들이 존재한다.
- 메이븐의 생명주기 단계를 순차적으로 실행되며, 각 생명주기 단계의 역할은 다음과 같다.

**클린 생명주기**

- clean : 이전 빌드가 생성한 모든 파일을 제거한다.

**기본 생명주기**

- validate : 프로젝트를 빌드하는데 필요한 모든 정보를 사용할 수 있는지 검토한다.
- compile : 프로젝트의 소스코드를 컴파일한다.
- test : 단위 테스트 프레임워크를 사용해 테스트를 실행한다.
- package : 컴파일한 코드를 가져와서 JAR 등의 형식으로 패키징을 수행한다.
- verify : 패키지가 유효하며 일정 기준을 충족하는지 확인한다.
- install : 프로젝트를 사용하는데 필요한 패키지를 로컬 저장소에 설치한다.
- deploy : 프로젝트를 통합 또는 릴리즈 환경에서 다른 곳에 공유하기 위해 원격 저장소에 패키지를 복사한다.

**사이트 생명주기**

- site : 메이븐의 설정 파일 정보를 기반으로 프로젝트의 문서 사이트를 생성한다.
- site-deploy : 생성된 사이트 문서를 웹 서버에 배포한다.

## 4.3 Hello World 출력하기

### **4.3.1 컨트롤러 작성하기**

- 먼저 앞에서 생성한 프로젝트에 패키지를 생성해야 한다.
- 이 예제에서는 레이어드 아키텍처에 맞춰 도메인 구분 없이 패키지를 구성하겠다.
- `com.springboot.hello` 패키지에 마우스 오른쪽 버튼을 클릭한 수 [New] → [Package]를 차례로 선택해 `'controller'` 라는 이름의 하위 패키지를 생성한다.
- 그리고 나서 `'controller'` 패키지에 마우스 오른쪽 버튼을 클릭한 후 [New] → [Java Class]를 클릭하고 `HelloController`라는 이름의 컨트롤러를 생성한다.

  ![스크린샷 2024-05-11 오전 1.04.47.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/0b4c5ff6-e6f7-4128-baba-4092db5ae54c/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1.04.47.png)

- 컨트롤러에 포함된 로직에서는 애플리케이션의 사용자 또는 클라이언트가 입력한 값에 대한 응답을 수행한다.
- 특별한 경우를 제외한 모든 요청은 컨트롤러를 통해 진행돼야 한다.
- 이번 예제는 컨트롤러 내부에서 모든 로직을 처리했지만 데이터를 다루거나 별도의 로직을 처리해야 하는 경우네는 서비스 또는 데이터 액세스 레이어까지 요청을 전달하는 경우가 일반적이다.
- `HelloController` 클래스에는 아래와 같은 코드를 작성한다.

```java
package com.springboot.hello.controller;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
    @RequestMapping("/hello")
    public String hello(){
        return "Hello World";
    }
}
```

### 4.3.2 애플리케이션 실행하기

- 애플리케이션을 실행하는 방법은 다른 자바 프로젝트와 같다.
- 아래와 같이 인텔리제이 IDEA 우측 상단부에 위치한 실행 버튼을 누르면 애플리케이션이 실행된다.

![스크린샷 2024-05-11 오전 1.13.53.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/db3a7c12-eb56-498a-9a31-7fa8d2475686/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1.13.53.png)

- 8080번 포트를 통해 웹 서버가 열린 것을 로그의 세번째 줄에서 확인할 수 있다.

### 4.3.3 웹 브라우저를 통한 동작 테스트

- 웹 브라우저로 스프링 부트가 설정한 URL에 접속하면 간단하게 실행 결과를 확인할 수 있다.
- 아래와 같이 웹 브라우저의 주소창에 `'http://localhost:8080/hello'` 를 입력하면 Hello World가 출력되는 것을 확인할 수 있다.

![스크린샷 2024-05-11 오전 1.15.48.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/8c04b720-7f11-4f8f-b73a-69a5f0ae708a/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1.15.48.png)

### 4.3.4 Talend API Tester를 통한 동작 테스트

- 웹 브라우저를 통한 동작 테스트는 간편하지만 상세한 응답을 확인할 수 없다는 단점이 있다.
- 구글 크롬의 확장 프로그램인 Talend API Tester를 사용하면 이 같은 문제를 해결할 수 있다.
- 크롬 브라우저의 주소창에 https://chrome.google.com/webstore/category/extensions?hl=ko 에서 ‘Talend API Tester - Free Edition’을 찾아 설치한다.
- Talend API Tester 는 HTTP 통신을 테스트하는 프로그램이다.
- GET, POST, PUT, DELETE 등의 다양한 HTTP 메서들를 설정하고 쿼리(query) 와 파라미터(parameter)를 담아 요청을 보낼 수 있다.
- 크롬 브라우저에서 Talend API Tester를 실행하면 아래와 같은 화면이 표시된다.

![스크린샷 2024-05-11 오전 1.18.33.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/8d5e6c65-3934-4312-a038-b4d49d07a41a/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1.18.33.png)

- 이 화면에서 HTTP 요청을 보내려는 경로와 메서드를 설정하고 [Send] 버튼을 클릭해 요청을 보내면 같은 화면의 아래 부분에 위치한 ‘Response’ 화면에 결괏값이 출력된다.
- 한 가지 주의해야 할 점은 URL 입력란에 ‘https’가 기본값으로 설정돼 있는데 이를 http로 변경해야 한다는 점이다.
- 테스트를 진행하면 아래와 같은 응답 화면이 출력된다.
- 앞서 웹 브라우저에서 확인했을 때와 마찬가지로 ‘Hello World’가 정상적으로 출력되는 모습을 확인할 수 있다.

![스크린샷 2024-05-11 오전 1.21.21.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/f4b917bb-af79-49e7-a149-2d362964fbfb/94356961-7285-44a0-85a0-83fb2a2b0709/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2024-05-11_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1.21.21.png)

- Talend API Tester의 장점은 HTTP 헤더를 볼 수 있다는 점이다.
- REST 통신에서는 Body 값뿐만 아니라 헤더에도 값을 추가해서 요청에 필요한 데이터를 담아 보내는 경우가 많다.