> 브라우저 저장소들의 차이를 설명해주세요.

- 1' 40

웹 브라우저의 저장소에는 *쿠키, 로컬 스토리지, 세션 스토리지*가 있습니다.

먼저, 쿠키는 만료 기한이 있는 키-값 저장소입니다. same site 옵션을 strict로 설정하지 않았을 경우 다른 도메인에서 요청했을 때 자동전송되며, **4KB**까지 데이터를 저장할 수 있는 작은 저장소이고, **만료 기한이 있기 때문에** 만료 기한을 정할 수가 있습니다. 쿠키를 설정할 때는 자바스크립트의 `document.cookie`로 볼 수 없도록 **`httponly` 옵션을 거는 것이 중요**합니다. 클라이언트와 서버 둘 다에서 만료 기한을 정할 수 있는데, 보통 서버에서 만료 기한을 정합니다.

다음으로 로컬 스토리지와 세션 스토리지가 있습니다. 둘 다 **만료기한이 없는** 키-값으로 구성된 저장소입니다. 

로컬 스토리지는 **10MB**까지 저장할 수 있으며, **도메인 단위**로 생성, 저장, 웹 브라우저를 닫아도 유지됩니다. HTML5를 지원하지 않는 웹 브라우저에서는 사용할 수 없으며 클라이언트에서만 수정이 가능합니다.

한편, 세션스토리지는 **탭 단위로** 세션 스토리지를 생성합니다. 그래서 탭을 닫을 때 저장돼있던 데이터가 삭제됩니다. 세션 스토리지 또한 HTML5를 지원하지 않으면 사용할 수 없고, **5MB**까지 저장이 가능합니다. 로컬 스토리지와 마찬가지로 클라이언트에서만 수정이 가능합니다.



> Promise에 대해 설명해 주세요.

- 1' 40

프로미스는 *자바스크립트 비동기 처리에 사용되는 객체*입니다. 프로미스는 *`pending`, `fulfilled`, `rejected` 상태*를 가집니다.

`new Promise()` 메서드를 호출하면 프로미스가 생성되면서  `pending` 상태가 됩니다. 

비동기 처리가 **성공할 경우** 메서드의 인자로 전달한 콜백함수  `resolve` 함수가 호출되면서 `fulfilled` 상태가 되고, **실패한 경우** 두 번째 인자로 전달한 `reject` 함수가 호출되면서 프라미스는 `rejected` 상태가 됩니다.

`fulfilled` 상태가 된 프로미스는 `then()` 메서드로 비동기 처리의 결과 값을 받을 수 있고, 실패하여 **`rejected` 상태가 된 프로미스**는 `then()` 메서드의 두 번째 인자로 받거나 `catch()` 메서드로 받을 수 있습니다. 보통은 `catch()` 메서드로 실패 결과를 받아 비동기 처리 중 발생한 에러를 처리합니다.



> "attribute"와 "property"의 차이점은 무엇인가요?

- 0' 47

 *`attribute`는 HTML 문서 안에서 쓰이고, `property`는 DOM 객체에서 쓰입니다.* 브라우저는 HTML을 파싱해 DOM 객체를 만들 때, 표준 `attribute`를 인식하여 DOM 프로퍼티를 만듭니다. 

HTML은 텍스트 문서이기 때문에 `attribute`는 항상 문자열이고, 대, 소문자를 구분하지 않습니다.

DOM 노드는 자바스크립트의 객체이기 때문에, `property`는 어떤 타입의 값이든 가질 수 있고, 대, 소문자를 구분한다는 차이점이 있습니다.



> redux가 무엇인지와 장단점에 대해 설명해 주세요.

- 1' 17

리덕스란 전역 상태관리 라이브러리입니다. 모든 상태를 Store에 저장하고, `dispatch`를 통해서만 상태를 업데이트 할 수 있습니다.

상태를 공유할 때 *다른 컴포넌트를 거치지 않고 Store를 통해 전달*이 가능해서 props 드릴링 현상을 방지할 수 있습니다.

리덕스는 **redux dev tools 등을 활용해서** **쉬운 디버깅**이 가능하고, saga, thunk, persistent와 같은 **미들웨어 기능을 제공**하여 비동기 작업을 훨씬 효율적으로 관리할 수 있습니다.

하지만, **구조가 복잡**하고, 상태를 다룰 때마다 action을 따로 작성해줘야 하는 번거로움이 있습니다.



> 호이스팅에 대해 설명해 주세요.

- 1' 35

호이스팅이란 변수나 함수를 선언했을 때, 선언 부분만 스코프의 최상단으로 끌어올리는 것을 의미합니다. `var`, `let` `const` 세 키워드 모두에서 호이스팅이 일어납니다.

`var` 키워드를 사용해 선언한 변수는 선언과 초기화가 동시에 일어나기 때문에, 아직 선언되지 않은 상태에서 변수에 접근을 해도 참조 오류가 발생하지 않습니다.

 하지만, `let` 이나 `const` 키워드로 변수를 선언하면 코드 실행 시점에 초기화가 일어납니다. 때문에, 선언되지 않은 시점에서 변수에 접근하면 참조 오류가 발생합니다. 호이스팅으로 선언부는 상단으로 끌어올려졌지만, 초기화가 일어나지 않은 일시적 사각지대에 있을 때 변수에 접근하려고 했기 때문입니다.

함수의 호이스팅은 함수 선언식은 호이스팅이 일어나 선언 전에 실행이 가능하나 함수 표현식은 변수의 경우와 마찬가지로, 선언 전에 호출하면 실행은 되지 않습니다. `var` 키워드로 선언했다면 초기화된 값인 `undefined`를 가지게 되고, `let` 이나 `const` 로 선언했다면 참조 오류가 발생합니다.



> DOM과 가상 DOM은 무엇인가요?

- 0' 51

Document Object Model의 약자로, HTML이나 XML 문서의 ***프로그래밍 인터페이스***를 의미합니다. DOM 표현을 통해 *웹 페이지를 조작*할 수 있습니다.

가상 DOM은 변경 사항이 생겼을 때 *실제 DOM에서 처리하는 방식이 아닌*  Virtual DOM과 메모리에서 미리 처리하고 저장한 후 *<u>실제 DOM과 비교하여 동기화</u>하는 **프로그래밍 개념***입니다.

가상 DOM은 DOM을 직접 업데이트하는 것보다 상대적으로 빠릅니다.



> useMemo와 useCallback을 비교해서 설명해 주세요.

- 0' 47

둘다 **메모제이션 훅**입니다. 메모제이션 훅은 *<u>연산된 값을 캐싱해서 재사용시 계산을 반복하지 않고</u>* 꺼내서 사용 가능하게 해 줍니다. 

메모제이션 훅은 리액트의 불필요한 렌더링을 방지해서 **성능 최적화**에 사용됩니다.

`useCallback`은 전달된 ***함수 그 자체를 캐싱***하기 위해 사용하고, `useMemo`는 전달된 함수가 실행되고 반환된 ***결과***를 캐싱하기 위해 사용합니다.

`useCallback`은 함수 그 자체를 캐싱하기 때문에 메모제이션된 캐싱된 **콜백을 반환**하고, `useMemo`는 **캐싱된 값을 반환**한다는 차이점이 있습니다.



> NPM이란 무엇인가요?

- 0' 54

**Node Packaged Manager**의 약자로, `npm`은 *`Node.js`로 만들어진 모듈*을 <u>웹에서 받아서 설치하고 *관리해주는 프로그램*</u>입니다.

자바스크립트 매니저이고, 설치한 모듈들을 패키지화해서 모아둔 저장소 역할을 하며 설치, 관리할 수 있는 CLI를 제공합니다.

많은 자바스크립트 프로그래머들이 *유용한 패키지*들을 만들어 npm에 코드를 공개합니다.

이와 별개로 `yarn`이라는 패키지 매니저도 있습니다. `yarn`은 facebook에서 만든 것으로 `npm` 서버에 비해 속도가 빠릅니다.



> 리액트의 생명주기에 대해 말씀해 주세요.

- 0' 46

리액트는 **컴포넌트 기반의 라이브러리**로, 리액트의 생명주기란 곧 **컴포넌트의 생명주기**라고 할 수 있습니다. *화면에 나타났다 사라지기까지의 과정*이며 `Mout`, `Update`, `Unmount` 단계로 나뉩니다.

`Mount` 단계에서는 컴포넌트가 *DOM에 로드*되어 화면에 보이게 됩니다.

`Update`는 컴포넌트가 업데이트되는 단계로, update는 *state나 prop의 변경이 일어났을 때* 발생합니다.

`Unmount` 단계는 컴포넌트가 *DOM에서 해제*되어 화면에서 사라지는 단계입니다.



> async/await이 무엇인가요?

- 0' 54

`async` 와 `await`은 *비동기 처리하는 코드를 동기적으로 작성할 수 있도록 도와주는 키워드 연산자*입니다.

`async` 키워드를 일반 함수 앞에 추가하면 해당 함수는 **프로미스를 반환하는 함수**가 됩니다.

`await` 키워드는 async 함수 안에서만 쓸 수 있습니다. `await` 키워드는 **프로미스가 처리될 때까지 함수 실행을 기다리게 만들어** 동기적으로 작동하는 것처럼 비동기 코드를 작성할 수 있도록 합니다.



> JWT란 무엇인가요?

- 0' 57

JWT란 JSON Web Token의 약자로, 데이터가 JSON으로 이루어져있는 토큰을 말합니다.

토큰은 로그인 이후 서버가 만들어주는 문자열이고, 문자열 안에는 사용자의 로그인 정보와 서버의 서명이 들어 있습니다.

JWT 방식은 서버가 요청과 함께 들어온 토큰의 유효성을 검사해서 인증을 하고, 요청에 응답을 하는 방식입니다.



> undeclared에 대해 null과 undefined를 비교해서 설명해주세요.

- 0' 27

`undeclared` 는 <u>변수가 선언되지 않았음</u>을 의미합니다. 코드 전체에 변수가 존재하지 않는 경우를 예로 들 수 있습니다. `undefined` 는 <u>변수가 선언되었지만</u> 아무 값도 할당 받지 않았음을 나타냅니다. `null` 은 변수에 명시적으로 ''값이 없음''을 나타내기 위해 <u>할당하는 값</u>입니다.



> 비동기 함수에 대해 설명해주세요.

- 0' 18

비동기 함수는 동기 함수와는 다르게 호출 시점에서 실행 결과를 기다리지 않는 함수를 말합니다.



> 크로스 브라우징에 대해 아는 대로 설명하세요.

- 0' 50

웹 페이지를 제작할 때 모든 브라우저에서 깨지지않고 의도한 대로 화면이 나오게 하는 작업을 말합니다.

각 브라우저는 렌더링 엔진이 다르기 때문에 동일한 코드를 작성하더라도 브라우저마다 화면이 다르게 보일 수 있기 때문입니다.

이러한 크로스 브라우징 작업에는 CSS 코드를 작성할 때 브라우저별 접두사인 벤더 프리픽스를 추가하거나, 브라우저가 가진 default 값을 초기화하기 위해 CSS를 초기화하는 방법 등이 있습니다.



> this의 용법을 아는대로 설명하세요.

자바스크립트의 this는 호출하는 방식에 따라 참조값이 달라지는 키워드입니다.

전역 범위에서 사용되는 this는 전역 객체를 가리키고, 함수에서 사용될 때도 전역 객체를 가리킵니다.

객체에 속한 메서드에서 사용될 때는 자신이 속한 객체를 가리키지만, 객체에 속한 메서드의 내부함수에서 사용될 때는 다시 전역 객체를 가리킵니다.

생성자에서 사용될 때는 생성자로 인해 생성된 새로운 객체를 가리킵니다.



> 원시값과 참조값의 차이는 무엇인가요? 메모리 관점에서 설명해 주세요.

원시 값은 변수에 할당하면 변수에 실제 값이 저장되지만, 참조 값은 변수에 할당하면 객체가 저장된 메모리 공간의 주소가 할당됩니다.

원시 타입의 값은 변경 불가능한 값으로, 메모리에 저장된 원시 값 자체는 변경되지 않습니다.

참조 타입의 값은 객체의 프로퍼티를 변경, 추가, 삭제할 수 있으므로 변경 가능한 값이라고 할 수 있습니다.



> 깊은 복사와 얕은 복사의 차이는 무엇인가요?

**얕은 복사**는 객체를 복사할 때. 원본 값과 복사한 값이 **동일한 참조를 가리키는 것**을 말합니다. 중첩 객체처럼 객체 안에 객체가 있는 경우에도 안에 있는 객체 중 하나라도 <u>원본 객체를 참조하고 있다면</u> 이는 얕은 복사라고 합니다.

**깊은 복사**는 객체를 복사할 때. 복사된 객체가 **다른 주소를 참조하여** 원본 객체의 <u>내부의 값만 복사</u>되는 것을 말합니다. **중첩 객체라도 원본과의 참조가 완전히 끊어졌다면** 깊은 복사라고 합니다.



> 타입스크립트를 사용하는 이유가 뭐라고 생각하나요?

<u>컴파일 단계에서 오류를 발견할 수 있어서 오류 대응이 쉽기</u> 때문입니다.

또한 코드의 **예측 가능성**을 높여서 디버깅이 쉽고 정적 타입 선언으로 코드의 의도를 기술할 수 있어서 개발자 경험 개선에도 도움이 됩니다.



> useEffect hook에 대해 설명해 보세요.

useEffect hook은 컴포넌트의 생애주기별 시점에 따라 기능을 실행시키기 위한 리액트 훅입니다.

**<u>컴포넌트의 특정 값이 업데이트될 때</u>** 기능을 실행해야 한다면, 두 번째 매개변수 배열에 값을 넣어주면 됩니다. 

**<u>컴포넌트가 언마운트되거나 업데이트 되기 직전</u>**에 원하는 작업을 하고 싶다면 뒷 정리 함수를 리턴하면 됩니다.



> ES6 문법에 추가된 것들을 설명해주세요.

문자열 리터럴, 객체 비구조화 할당, 객체 리터럴, 화살표 함수, `let`과 `const`

전개 연산자(SpreadOperator), `for...of` 반복문, 나머지 연산자가 있습니다.



> forEach와 Map의 차이점이 무엇인가요?

`forEach`와 `map()` 둘다 배열의 모든 원소를 돌면서 해당 요소에 대한 콜백함수를 실행합니다.

`forEach`는 반환값이 없고, `map()`은 함수 실행의 결과가 담긴 배열을 반환합니다.



> CSR과 SSR의 차이는 무엇인가요?

**초기 로딩 속도 측면에서** 서버 사이드 렌더링은 필요한 HTML 파일을 서버에서 완성해서 보내기 때문에 사용자는 더 빨리 화면을 볼 수 있지만, 

클라이언트 사이드 렌더링은 빈 HTML을 받고 자바스크립트의 실행으로 DOM이 동적으로 변경되며 <u>브라우저에서 렌더링</u>되기 때문에 사용자는 빈 화면을 보고 있을 수도 있어, 서버 사이드 렌더링에 비해 **진입이 느리다**고 볼 수 있습니다. 

물론, 서버 사이드 렌더링에서는 자바스크립트 코드 실행 시점에 따라 사용자가 화면을 보는 시간과 실제 상호작용할 수 있는 시간에 차이가 있지만, 화면을 렌더링하는 시간은 서버 사이드 렌더링이 빠릅니다.

**SEO 측면에서도** 서버에서 페이지에 필요한 정보를 HTML에 모두 담아서 넘겨주는 서버 사이드 렌더링이 유리합니다.

**서버 부하 측면**에서는 클라이언트 사이드 렌더링이 페이지를 이동할 때도 새로운 HTML을 서버에 요청해야 하는 서버 사이드 렌더링에 비해 서버 요청이 적기 때문에 서버 부하가 적게 일어납니다.



> 리액트의 상태관리 방법에 대해 말씀해 주세요.

리액트의 상태관리 방법 세 가지를 예시로 들어보자면, 

리액트가 제공하는 context API와 redux, react-query 라이브러리가 있습니다.

contextAPI는 리액트에서 제공합니다. 리액트 컴포넌트 트리 안에서 전역 상태를 공유할 수 있도록 만들어진 툴입니다.

원하는 범위를 정확히 지정하지 않으면 불필요한 리렌더링이 발생할 수 있습니다.

redux는 어플리케이션 전부에 대한 중앙 저장소를 두고 관리하는 전역 상태관리도구입니다.

자바스크립트 앱을 위한 상태 관리 도구로 개발자들이 가장 많이 사용하는 상태관리 라이브러리입니다.

react-query는 서버와 클라이언트 간 비동기 작업을 쉽게 다룰 수 있게 도와주는 라이브러리입니다. 

클라이언트에서 보이는 서버 데이터는 항상 최신으로 보장할 수 없기 때문에 서버 상태 관리를 위해 등장한 서버 상태 관리 라이브러리입니다.



> Box model에 대해 설명해 주세요.

모든 HTML 요소는 BOX 모양으로 구성되며, 이것을 박스모델이라고 합니다.

문서의 레이아웃을 계산할 때, 브라우저의 렌더링 엔진은 표준 CSS 기본 박스 모델에 따라 각각의 요소를 사각형 박스로 표현합니다.

박스 모델은 총 네 부분(영역)으로 이루집니다. 패딩, 테두리, 마진, 내용입니다. 내용은 텍스트나 이미지처럼 요소의 실제 내용이 들어가는 부분으로, 색상이나 너비, 높이 등을 지정할 수 있습니다. 

패딩은 내용과 테두리 사이의 간격을 말합니다. 패딩은 눈에 보이지 않습니다.

테두리는 내용영역과 패딩 영역을 감싸는 경계선입니다. 마진은 요소의 경계선인 테두리와 이웃하는 다른 요소 사이의 간격이고, 패딩처럼 눈에 보이지 않습니다.

마진이 요소의 주변에 여백을 생성한다면, 패딩은 요소의 내부에 여백을 생성합니다.



> 브라우저의 렌더링 원리에 대해 말씀해 주세요.

브라우저는 가장 첫 번째 단계로 HTML 파일을 파싱하여 DOM 트리를 구성하고, CSS 파일을 파싱하여 CSSOM 트리를 구성합니다.

DOM 트리와 CSSOM 트리를 바탕으로 Render 트리를 구성합니다. 렌더트리에는 스타일 정보가 설정돼 있고, 실제 화면에 표현되는 노드들로 구성이 됩니다.

렌더트리를 구성한 뒤에는 레이아웃 단계를 거치게 됩니다. 해당 단계에서는 각 요소들이 화면의 어디에 위치해야 하는지 계산하는 단계입니다. %, vw, vh 등의 상대적 단위들은 모두 px로 변환되어 뷰포트 상의 위치를 계산합니다.

width 나 height 등의 속성 변화로 인한 reflow 현상을 최소화하는 것이 좋습니다.

레이아웃 계산 후에는 색을 입혀서 사용자에게 보여줍니다. 이를 페인트 과정이라고 합니다.



> HTTP와 HTTPS의 차이점을 말씀해 주세요.

HTTP는 서버-클라이언트 모델을 따라 데이터를 주고받기 위한 프로토콜입니다.

HTTPS는 HTTP에 데이터 암호화가 추가된 프로토콜로, 공개키-개인키 암호화 방식을 이용해서 데이터를 암호화합니다.

HTTPS와 달리 HTTP는 암호화가 추가되지 않았기 때문에 보안에 취약하고, HTTPS는 안전하게 데이터를 주고받을 수 있습니다.

하지만 HTTPS는 암호화와 복호화 과정이 필요하므로 HTTP보다 속도가 느리고, 인증서를 발급하고 유지하기 위한 추가 비용이 발생합니다.