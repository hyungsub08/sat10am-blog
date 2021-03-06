---
layout: post
title: "Angular 학습자료 - 00. Before Starting"
---

# Angular
- [Angular](#angular)
    - [Angular 버저닝](#angular-%EB%B2%84%EC%A0%80%EB%8B%9D)
        - [AngularJS --> Angular](#angularjs----angular)
        - [Angular 버저닝 정책](#angular-%EB%B2%84%EC%A0%80%EB%8B%9D-%EC%A0%95%EC%B1%85)
    - [컴포넌트 기반](#%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-%EA%B8%B0%EB%B0%98)
    - [모듈 로딩](#%EB%AA%A8%EB%93%88-%EB%A1%9C%EB%94%A9)
        - [모듈과 모듈 로딩](#%EB%AA%A8%EB%93%88%EA%B3%BC-%EB%AA%A8%EB%93%88-%EB%A1%9C%EB%94%A9)
    - [zone.js 변경 감지](#zonejs-%EB%B3%80%EA%B2%BD-%EA%B0%90%EC%A7%80)
        - [기존의 변경 감지](#%EA%B8%B0%EC%A1%B4%EC%9D%98-%EB%B3%80%EA%B2%BD-%EA%B0%90%EC%A7%80)
        - [zone.js](#zonejs)
            - [무엇](#%EB%AC%B4%EC%97%87)
            - [Angular에서는](#angular%EC%97%90%EC%84%9C%EB%8A%94)
            - [보다 빠른 변경 감지](#%EB%B3%B4%EB%8B%A4-%EB%B9%A0%EB%A5%B8-%EB%B3%80%EA%B2%BD-%EA%B0%90%EC%A7%80)
            - [immutable](#immutable)


## Angular 버저닝  
> *AngularJS에서 Angular로, Angular 2에서 3을 뛰어 넘어 Angular 4로, 중간 중간 마이너 버전과 메이저 버전의 업데이트까지 Angular의 버저닝은 개발자들에게 혼란을 줄 수 있는 여지가 많다. 왜 이렇게 복잡할까?*

### AngularJS --> Angular

**AngularJS의 등장**  
Angular는 2009년 구글의 미시코 헤브리가 처음 개발하여 2010년 0.9버전으로 정식 릴리즈되었으며 2012년 6월에 1.0 버전이 릴리즈 되었다. 단 몇 개월만에 혁신적인 생산성으로 가장 인기있는 프론트엔드 프레임워크로 자리잡았으며, 그 후 1.6.9 버전까지 릴리즈되었다.(더이상 지원하지 않는다.)

**Angular로 업그레이드**  
그 후 약 4년 뒤인 2016년 9월에 Angular 2.0 버전이 정식 릴리즈 되었다. AngularJS 1.x와 전혀 호환이 되지 않으며 기반 언어도 타입스크립트를 타겟으로 구현이 되어 있다. 기존 1.x 버전을 익힌 것은 모두 무용지물이 되고 새로운 프레임워크와 언어를 다시 습득해야하기에 개발자들은 혼란에 빠진다. 기존 버전과 혼란을 막기 위해 2.0 버전부터는 새로운 이름을 달아야 한다는 의견이 대세가 되고 AngularJS에서 Angular로 JS가 삭제 되었다.(Angular는 더이상 라이브러리 수준이 아닌 프레임워크로 진화했기 때문이다.)

### Angular 버저닝 정책

**시맨틱 버전**  
Angular는 기본적으로 시맨틱 버저닝 정책을 따른다. 시맨틱 버저닝 정책은 다음과 같다.
* 메이저 버전: 과거 버전과 호환되지 않음
* 마이너 버전: 과거 버전과 호환이 되며 새로운 기능이 추가
* 패치 버전: 버그 픽스

![https://q.vtable.org/semantic-versioning-cool-concept-buuuut/](/img/semantic_versioning.png)  

**Angular 3은 어디에?**   
@angular/router의 버전이 2.0 개발 중 대규모 변경이 이루어지고 다른 모듈은 2.0인 시점에 3.0으로 업데이트해야만 했다. 이렇게되면 개발자들은 Angular 모듈 버전에 대해 더 큰 혼란을 가져다 온다고 판단하여 메이저 3버전을 건너뛰고 4버전으로 이어갔다.

## 컴포넌트 기반  
> *사람의 사고능력은 제한적이라서 전체를 한꺼번에 세부적으로 처리할 수 없다. 그래서 무언가를 만들 때 큰 단위로 추상화를 한 후에 부분 별로 작업하거 이를 결합하는 사고방식에 익숙하다. 이를 Angular는 컴포넌트 단위로 개발 할 수 있도록 하였다.*

**복잡한 HTML들**  
기존에는 페이지 별로 복잡한 HTML 파일들을 수십개씩 처리해야 했다. 이것을 한꺼번에 처리하는 것은 매우 복잡하며 인내가 필요할 것이다. 적절히 추상화를 하여 구조를 만들 수 있는 도구가 없었기 때문이다. 이 때의 개발 방식과 도구는 자연스러운 사고 방식을 반영하지 못한다고 볼 수 있다.

**AngularJS의 방식**  
AngularJS를 사용하더라도 상황은 마찬가지이다. 가장 많이 하는 작업이 컨트롤러를 생성하고 HTML에 붙이는 작업이다. 뷰와 컨트롤러를 잘 분리해주고 데이터 바인딩을 자동화하여 매우 번거롭던 일들을 대폭 줄여준 것은 맞지만 우리의 자연스러운 사고 방식을 반영하지 못하였다.

**컴포넌트 기반 구조**  
![https://www.slideshare.net/mrg7211/angular2-63442250](/img/component_tree.png)  
웹 어플리케이션의 부분 부분을 컴포넌트로 구분하고 각 컴포넌트는 자신만의 클래스, 태그 등으로 나타내지기 때문에 HTML의 나열이 아니라 컴포넌트 단위의 UI로 구성되게 된다.
또한 컴포넌트는 컴포넌트 별로 또 하위 컴포넌트들을 조합하여 자체적인 구조를 만들게 되며 전체적으로 컴포넌트 트리를 이루게된다.
이렇게 되면 트리의 각 단계에서 보는 추상화 단위로 어플리케이션을 보기 때문에 구조 파악이 쉬워지며 작업의 단위도 컴포넌트로 분리할 수 있어 유지보수나 수정이 용이하다.

**Angular의 컴포넌트 구조**  
Angular에서는 어플리케이션을 컴포넌트로 개발할 수밖에 없게 되어 있다. UI를 구성하려면 무조건 컴포넌트를 정의해야한다. 다음은 간단한 Angular 컴포넌트의 예시이다.
```javascript
@Component({
	selector: "sat10amApp",
    	template: 
		<h1>App Component</h1> 
		<button (click)="onClick()">click</button>,
    	styles: [
    		h1 { background-color: red }
	]
})
export class AppComponent {
	onClick() { alert("Clicked")}
}
```
Angular가 위와 같은 컴포넌트 구조를 도입하였기 때문에 다음과 같은 이점을 얻을 수 있다.
* Angular의 컴포넌트를 하나의 클래스로 다루도록 해서 훨씬 객체지향적이다. 코드로 모두 표현하기 힘든 설정은 데코레이터를 적절히 사용해 클래스에 추가하기도 했다.

* AngularJS에서는 scope를 통해 템플릿과 컨트롤러의 중간 저장 공간이 있어 임의로 삽임될 때 바인딩이 의도와 다르게 동작하는 경우가 많았지만 Angular에서는 템플릿에 대한 모든 바인딩이 컴포넌트 클래스의 멤버 변수 또는 함수로 고정되어 있다. 따라서 어플리케이션의 구조가 명확해지고 작동 결과를 예상하기가 쉬워졌다.  
![http://frontend.diffthink.kr/2016/05/angular-02-angularjs.html](/img/angularjs_scope.png)  


* Angular는 Shadow Dom을 지원하여 컴포넌트에 정의된 CSS 스타일 요소가 지역적으로 적용되도록 구현되어있다. 컴포넌트의 디자인 요소까지 지역화 할 수 있기 때문에 컴포넌트의 독립성과 재사용성이 크게 증가한다.

* 라우터 설정에서도 컴포넌트 기반이 유용하다. Angular의 라우팅 정의는 라우팅에 따라 변경되는 부분을 컴포넌트로 설정한다. 라우팅에 대해 변경되는 부분이라는 것은 독립된 UI와 독립된 기능이라는 것이기 때문에 이런 부분은 컴포넌트라는 단위로 표현하는 것이 더 자연스럽고 적절하다.
```javascript
const routes: Routes = [
  { path: '', redirectTo: '/dashboard', pathMatch: 'full' },
  { path: 'dashboard', component: DashboardComponent },
  { path: 'detail/:id', component: AccountDetailComponent },
  { path: 'accounts', component: AccountComponent }
];
```

* 이 외에도 변경 감지나 기타 설정들이 컴포넌트 단위로 이루어지도록 하고 있다.
## 모듈 로딩
> *어플리케이션을 개발할 땐 처음하는 작업은 아마 검색일 것이다. 누군가가 그런 기능을 이미 구현해 놓지 않았을까 해서 말이다. 이처럼 많은 부분이 외부 라이브러리에 의존한다.
> 이 외부 라이브러리도 누군가가 개발한 코드이며 이 코드 역시 다른 라이브러리를 참조한 경우가 많다
> 따라서 라이브러리 간의 의존성이 부가되고 중복되기도 한다. 중복된 라이브러리의 버전이 다르다면 추적하기도 쉽지 않다.
> 어플리케이션이 커질 수록 이런 라이브러리 관리는 필수적이 된다.*

### 모듈과 모듈 로딩
**언어 차원의 모듈**  
ES5 이전에는 모듈에 대한 개념이 부족했다. 단순히 window 객체에 등록하고 어디에나 사용할 수 있도록 하였다. 이런 상황에서는 라이브러리 간의 전역 변수, 함수 등에 이름 충돌이 있으므로 겹치지 않을 법한 이름을 찾아야 했다. 혹은 즉시 실행 함수의 형태로 작성되기도 했다. 그러나 이런 방식은 체계적으로 모듈을 관리하기 어렵다.

ES6부터는 언어 내에 import, export와 같은 모듈 관련 스펙이 추가되었다. 모듈은 파일 단위로 구분되고 각 모듈에 선언한 변수, 함수 등은 해당 모듈에서만 동작한다. 외부에 기능이나 값을 노출하기 위해서는  export를, 외부에 기능이나 값을 가져오기 위해서는 import를 사용한다.
Angular의 타겟 언어인 타입스크립트 역시 ES6와 같은 모듈 시스템이 언어 내에 포함되어 있다.

**모듈 로딩**  
![https://bertrandg.github.io/the-javascript-module-mess/](/img/javascript_module_load.png)  
언어 차원에서 모듈을 적절히 처리할 수 있도록 하였지만 이것을 실행 환경에서 별개로 처리해야한다. Node.js같은 경우에는 런타임에 이런 모듈 로딩에 관련된 기능이 포함되어 있다. 그러나 모듈 개념이 없는 ES5까지만 지원하는 브라우저에는 자체적으로 이런 모듈 로딩 기능이 없다. 이렇다 보니 자바스크립트 환경에서는 언어와 별도로 모듈 로딩 시스템이 같이 발달하였다.

타입스크립트를 가지고 Angular를 개발한다면 다음과 같은 과정이 있어야 브라우저에서 실행할 수 있다.
* 타입스크립트로 작성된 모듈들은 ES5 문법으로 컴파일한다.
* 이렇게 컴파일된 모듈과 외부 모듈들은 모듈 로더에 의해 브라우저에서도 로딩할 수 있도록 한다.

타입스크립트 컴파일의 설정을 담고 있는 tsconfig.json 설정을 보자  
```json
{
	"compilerOprions": {
    	"target": "es5",
        "module": "commonjs",
	,,,
    }
}
```  
target은 브라우저나 Node.js와 같이 실행될 환경을 설정하는 것이고 module은 어떤 모듈 로더를 사용하도록 컴파일 할지 설정하는 것이다.

모듈 로딩에 관련해서는 두 개의 큰 표준이 있다. CommonJS와 AMD이다(두 표준에 대해서는 [여기에](http://d2.naver.com/helloworld/12864)). 이와 더불어 이런 모듈을 직접 로딩해 줄 모듈 로더 구현체가 있어야 한다. requireJS, browserify, systemJS, webpack등이 이에 해당한다.

**Webpack을 이용한 모듈 로딩**  
![](/img/webpack_module_bundle.png)  
정확히 말하면 webpack은 모듈 로더 + 모듈 번들러이다. 모듈 로더는 앞서 말한 실행 환경에서 동작이 가능하도록 각각의 모듈을 로딩하는 구현체라는 것이고 모듈 번들러는 이렇게 로드된 모듈을 하나의 번들 파일로 생성하는 구현체라는 것을 의마한다.
HTTP 특성 상 작은 파일을 여러 번 로드하는 것 보다 큰 파일을 한번 로드하는 것이 성능 상 이점이 있기 때문이다. Angular도 초창기 개발에서는 systemJS를 통해 모듈 로드만 하였지만 현재는 이를 webpack으로 대체하고 번들링까지 수행한다.  
```javascript
var path = require('path');
module.exports = [
    //패키징 시작 파일
    entry: './src/main.ts',
    //패키징 출력 파일
    output: {
    	filename: 'bundle.js',
        path: path.resolve(__dirname, 'dist'),
        libraryTarget: 'var' //브라우저를 타겟으로 함
    },
    //브라우저에서 실행되도록 타겟을 web으로
    target: 'web',
    //모듈을 만났을 때 모듈의 위치와 이름을 찾기 위한 설정
    resolve: {
    	extensions: ['.ts', '.js', '.json'],
        modules: [path.resolve(__dirname, 'node_modules')]
    },
    //패키징 할 파일을 만났을 때 사용할 로더 설정
    module: {
    	rules: [
        	{ test: /\.ts$/,
              use: ['awesome-typescript-loader',
                  	'angular2-template-loader',
                    'angular-router-loader']},
            { test: /\.html$/, user: 'raw-loader'},
            { test: /\.css$/, user: 'raw-loader'},
            { test: /\.json$/, user: 'json-loader'}
        ],
    }
]
```
webpack은 필요한 모듈을 한꺼번에 패키징한다. 이 패키징 과정이라는 것이 모듈을 로드하는 개념과 같다. 즉 맨 처음 모듈을 시작으로 참조하는 모듈들을 찾는 것은 마찬가지이고, 이를 하나하나 로드하는 것이 아니라 모두 모아 하나의 파일로 만들어 준다는 것만 다를 뿐이다.   

**자바스크립트 모듈과 Angular 모듈의 차이**  
Angular 어플리케이션을 작성하다 보면 불가피하게 하나 이상의 NgModule을 만들게 된다(모든 Angular 어플리케이션에는 루트 모듈이 반드시 있어야 하기 때문에). 그럼 앞서 말한 자바스크립트 모듈과 NgModule은 같은 것인가? --> 그렇지 않다. 엄연히 다른 개념이다.

Angular 모듈은 Angular의 다양한 기능 요소들을 묶는 단위이다. 즉 Angular 모듈은 관련이 있는 컴포넌트, 파이프, 디렉티브, 서비스 등을 병합해 재사용성을 높이는 Angular만의 고유 기능이다. 자바스크립트의 모듈과는 다른 개념이다. 자바스크립트 모듈은 기본적으로 파일 단위로 구분되는 반면, Angular의 모듈은 하나의 자바스크립트 모듈에 여러 개가 들어갈 수 있는 것만 봐도 둘이 같지 않다는 점을 알 수 있다.

## zone.js 변경 감지
> Angular는 데이터와 뷰 간의 바인딩을 통해 상호 갱신을 자동화한다.  
> 여기서 상호 갱신이란 한 요소에 변경이 생기면 다른 요소에도 그 변경을 반영한다는 것이다.  
> 자, 그렇다면 한 요소가 변경되는 것은 어떻게 감지할 것인가?, 기능성이나 효율성을 따지게 된다면 이것은 꽤나 어려운 문제이다.   
### 기존의 변경 감지
* HTML 엘리먼트에는 사용자의 조작이나 기타 상황에 대해 이벤틀 통지하는 메커니즘이 존재한다.  
* 예를 들어, onclick 속성이나 addEventListener 메소드를 통해 이벤트 핸들러를 등록하고 해당 이벤트 발생 시 핸들러를 호출해 주는 방식이 있을 것이다.  
* 이렇게 뷰는 자신이 변경되는 것을 통지해주는 장치가 있다. 하지만 데이터가 변경되었다고 통지해주는 메커니즘은 자바스크립트에서 존재하지 않는다.
* AngularJS의 경우에서는 데이터가 변경되는 것을 통지해 주는 것이 아니라 데이터가 변경될 만한 상황이 되면 AngularJS가 변경된 것이 있는지 확인하는 방식으로 감지를 했다.
* 웹 어플리케이션에서 데이터가 변경될 만한 상황은 다음의 경우가 대부분이기 때문이다.   

| 구분        | 예시                    |
|-------------|-------------------------|
| DOM event   | onclick, onchange       |
| Ajax event  | XMLHtppRequest          |
| Timer event | setTimeout, setInterval |

* 그래서 AngularJS API에서는 각종 상황에 대한 디렉티브나 서비스들이 구현되어 있고, 개발자는 이것들을 이용해 처리하게 되면 변경 감지 프로세스를 구동시켜 주는 것이다.
* 하지만 AngularJS 외의 라이브러리에서 데이터를 변경하는 상황이라면 변경 감지는 할 수 없다. 그렇기 때문에 scope.$apply()를 호출해야 하는 번거로움이 있었다.
* 또한 변경될 만한 상황이 잘 감지 되었다해도 scope라는 중간 저장공간에 있는 것들에 대해 모두 변경 여부를 확인하는 작업을 거치게 된다.
### zone.js
#### 무엇
* zone.js는 비동기 요청 등을 발생시키는 브라우저 Native API에 대해 몽키패치를 한다. 그래서 호출되는 모든 Native API 요청을 추적한다. 그래서 일련의 비동기 요청들을 하나의 컨텍스트로 묶어 준다.
* zone.js는 일련의 컨텍스트를 구역(Zone)이라는 용어로 분리하며 하나의 구역 안에서 실행되는 비동기 요청들은 모두 하나의 컨텍스트로 추적할 수 있다.
* zone.js의 브라우저 Native API에 대해 몽키패치하는 이런 구현 덕에 브라우저 Native API 호출이 되었을 때 이를 통지받을 수 있는 기능도 제공한다.
#### Angular에서는
* Angular는 어플리케이션 시작 시 zone.js의 구역(zone)을 하나 만들어 이 구역에서 어플리케이션을 구동시킨다.
* 따라서 브라우저 Native API 호출에 대해 통지를 받을 수 있게 되고 변경 감지(Change Detection)이 가능하게 된다.
* 하지만 이것은 변경 감지를 수행할 시점을 알려 줄 뿐이고 어떤 것이 변경되었는지는 알지 못하는 상태이다.
* Angular 역시 AngularJS처럼 변경 감지 시점에 루트에서부터 차례로 검사해야 한다.
* Angular는 클래스 멤버가 바인딩 컨텍스트이기 때문에 컴포넌트를 대상으로 변경 감지를 한다.
* Angular에서 변경 감지 대상은 Input 데코레이터가 붙어 있는 변수, 컴포넌트 클래스의 @Input 멤버 변수이다.
#### 보다 빠른 변경 감지
* 그렇다면 어떻게 Chage Detection을 효율적으로 실행할 수 있을까?
* 앞서 설명했듯이 CD는 Runtime시 각 컴포넌트마다 생성되기 때문에 다양한 형태를 가질 수 있다. 각 컴포넌트의 구조에 맞게 CD 클래스를 정의 하고 생성하기 때문에, CD가 감시해야할 대상을 줄이면 성능을 높일 수 있다. 
* Angular는 CD가 감시해야 할 대상을 줄이기 위해 Immutable 객체와 Observable 객체를 알아보고 감시 대상에서 제외해 할 수 있는데, 이런 최적화는 Angular의 OnPush 전략(컴포넌트에 바인딩된 Input 값의 변화가 없는 경우에는 Subtree 에 대해 Change Detection을 하지 않음)으로 설정하여 처리한다.
#### immutable
* Immutable 객체는 값의 변화가 없음을 보장한다. 새로운 값을 지정하고 싶으면 객체를 변경하는 것이 아니라 새로 생성 해야만한다.
* 객체를 새로 생성한다는 것은 Angular 입장에서 값(상태) 비교가 필요 없다는 것을 뜻한다. Immutable 객체를 사용하는 바인딩된 컴포넌트들은 변경된 객체의 상태를 비교해 볼 필요 없이 객체의 레퍼런스만으로 변화를 감지할 수 있다. 
* (Javascript Immutable lib들을 이용하여 손쉽게 Immutable 객체를 생성해 볼 수 있는다. Immutable.js Github)


![https://q.vtable.org/semantic-versioning-cool-concept-buuuut/](/img/zone.png)  
