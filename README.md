# JDD (Ju-Dung-A-Li Driven Development/주둥아리 주도 개발)
![image](https://user-images.githubusercontent.com/10369528/130068355-049861db-ce6e-45cd-a74c-a262ee4fb01a.png)

JDD 는 코드 작성보다 변명거리를 미리 생각하여 수많은 버그를 양성할 수 있는 개발 방법론이다.

JDD 는 아래와 같은 중요 가치를 따른다.

```
우리는

- 남이 쓰는 기술보다는 내 것을

- Clean 한 코드보다는 Tricky 한 것을

- 버그 Fix 보다는 변명을

- 귀찮음보다는 편함을

가치있게 여긴다. 이 말은, 왼쪽에 있는 것들은 귀찮고 오른쪽에 있는 것들은 편하기 때문에 더 높은 가치를 둔다는 것이다.
```

JDD 를 실천하기 위해서는 쉬지 않고 험난한 길이지만 꾸준하게 노력해야한다.
중요한 것은 관련된 힙한 용어를 들먹이면서 실제 문제에 대한 답변을 회피하는것이다. 꾸준한 연습이 필요하다.


# JDD 를 위한 지침서

## JDD 를 위한 소양

JDD 의 기초가 되는 소양을 항상 명심하자.

### 참된 리더
잠든.. 아니 참된 리더는 부하직원을 괴롭히지 않는다. 

```
- 누군가 PR 을 했다는 사실 자체가 보기 좋은 일이다. LGTM(Looks Good To Me).

- 누군가 PR 을 날리면 자동으로 LGTM 를 날리는 CI/CD 를 활용해라
```

### 방어적 프로그래밍
방어적 프로그래밍은 개발자의 기본 소양이다.

```
- 방어적 프로그래밍을 해라 코드로 방어하지 말고 너에게 들어오는 일감을 방어해라

- 작업량이 많은가? 그냥 특정 테스트 케이스에서만 돌아가게 짜고 나머지는 "고도화" 작업에서 한다고 해라. "고도화" 작업 전에 이직하자.
```

## 성과 위주 회피

일 잘하는 척 편안한 생활을 위해 성과 위주로 행동해야 한다.

### 멀티 쓰레드
동시성은 어렵고, 성과가 눈에 띄지 않는다.
```
- 멀티 쓰레드 환경에서 가변 변수 사용으로 인한 오류는 가끔 발생한다.
가끔 발생한다는 거에 비하여 사용은 너무 편하다. 누가 뭐라고 하면 그럴 일 없다고 하면 그만이다.

- 어쩔 수 없이 멀티 쓰레드 업무가 들어오면 언어를 욕하면서 이 작업이 왜 어려운지 설명해라,
아 이 언어는 Actor 모델이 빈약해서요, CSP(Communicating Sequential Processes) 구현체가 없어서요, STM(Software Transactional Memory) 이 지원 안 돼서요.
욕을 할수록 작업 기한이 늘어난다.

- 비동기 흐름 내에서 동기함수를 몰래 써도 된다. 나중에 병목 찾는 작업 + 비동기로 개선하는 추가 작업 기한까지 함께 받을 수 있다.
```

### 문서화
우리의 본분을 잊지 말자.

```
- 주석은 절대 작성하지 않는다. 누가 뭐라고 하면 클린코드를 들먹이자. 물론 그렇다고해서 코드가 리더블하지는 않다.

- 우리는 개발자다, 어떠한 이유에서든지 문서 작성은 금물. 누가 뭐라고 하면 "코드가 곧 문서".

- 히스토리는 필요 없다. 과거에 연연하지 말자

- 인수인계 문서는 필요 없다. 누가 뭐라고 하면 내 코드는 보면 바로 이해가 간다고 하자. 미련없이 떠나자.
```

### 협업
단어부터 현기증이 온다.

```
- 여럿이서 동시에 같은 코드를 작성해야 한다면 어떻게든 나눠서 따로 작업한 뒤 합치자고 하자. 상대방도 하나를 두고 부대끼며 작업할 생각따위 없다.

- 브랜치 머지(Merge) 중 충돌 날 것 같은 시점에 휴가를 쓰는 건 필수다.

- 페어코딩은 의외로 괜찮다. 내가 코드를 짤 때에는 머리를 좀 비워도 되고, 다른 사람이 코드를 짤 때에는 오타 정도만 잡아주면 충분하다. 최대 장점은 작성된 코드에 대한 책임이 줄어든다는 점이다.

- 무슨 작업인지 별로 알리고 싶지 않다면 커밋 메시지는 `chore: trivial`이라고 하자. 변태가 아니고서야 이런 커밋을 읽어보는 사람은 없다.

- PR 을 머지(Merge)할 때에는 Squash merge 를 최대한 활용해서 중간중간에 들어간 뻘짓들을 숨긴다. 누가 뭐라고하면 '커밋 로그를 간략하게 유지하기 위해서'라고 하자.

- 커밋은 나눌 때는 작업이나 기능 단위가 아니라 내가 한 번에 고친만큼을 기준으로 한다. 어차피 머지 되면 다 Squash 돼서 잘 안보인다.

- PR Description 은 작업 관리 툴의 task 링크만 티켓으로 넣어 준다. 물론 링크를 타고 가도 설명 같은건 없다.

- 협업에는 커뮤니케이션 스킬이 필수다. 풍둔 주둥아리의 술로 상대방을 현혹시켜 PR 에 내 게으름이 토론 내역으로 남겨지지 않도록 대화를 유도한다. 

- 허락보단 용서가 쉽다. 어떻게든 빠르게 머지(Merge) 해야한다.

- 동료의 코드에서 오류나 오타, 간단한 실수(중복된 변수, 팀 코드 규칙, Lint와 같은)를 찾더라도 공유하지마라. 동료가 당신이 조화롭게 어울린다는 것을 은은하게 눈치채게하라. 동료도 내 실수를 눈 감아 줄 것이다.
```

## 뭐든 프로그래밍

세상은 0과 1로 이루어졌다고 할 수 있다. 그러니까 뭘 하든지 내가 하는 것은 프로그래밍인 것이다.

### 모던 프로그래밍
모던은 현재이다. 즉 지금 내가 쓰는 기술이 곧 모던한 기술이다.

```
- 예외 처리를 하지 않는다. 누가 뭐라고 하면 Let it crash 전략이라고 한다.

- 언어의 Feature 를 최대한 사용하지 않는다. 누가 뭐라고 하면 유지보수를 위해 누구나 알 수 있게 짜둔 거라고 한다.

- 언어의 Feature 를 최대한 활용하자. 누가 뭐라고 하면 모던 프로그래밍이라고 하면 된다.

- 의존성이 복잡하게 연결되어 있으면, 패턴이라고 한다.

- 체이닝(Chaining)이 하나라도 있으면, Fluent API 스타일

- 체이닝이 하나도 없으면, 디미터 법칙

- 함수들만 호출하는 함수가 있으면, 미니 언어로 DSL 을 구축했다고 해라

- 데이터를 넘겨주는 함수가 있으면, Data-Driven Programming 이라고 해라

- 함수 파라미터가 너무 많아졌다? 누가 뭐라고 하면 보다 "순수"하게 짠 거라고 해라

- 람다 함수로만 구성한다. 누가 뭐라고 하면 고차함수 함수형 프로그래밍이라고 한다.

- 패턴을 전혀 쓰지 않는다. 누가 뭐라고 하면 단순성의 원칙이라고 한다.

- Map-Reduce-Filter 같은 고차함수는 일절 사용하지 않는다. 누가 뭐라고 하면 이 역시 단순성의 원칙이라고 한다. Keep it simple, Stupid!

- 어노테이션과 같은 메타데이터를 수십개는 달자. 누가 뭐라고 하면 메타 프로그래밍 기법이라고 한다.

- OOP(Object-Oriented Programming)로 개발하는 사람들 사이에서 FP 패턴(Functional Programming)을 적극 활용하자.
라이브러리까지 쓰면 더 좋다. Maybe 클래스를 만드는건 기본 중의 기본. 누가 뭐라고 하면 "이게 요즘 스타일이예요"

- FP 로 개발하는 사람들 사이에서 OOP 패턴과 가변변수를 적극 활용하자. 누가 뭐라고 하면, "FP는 실용적이지 않다"

- 내 코드 보다 길면 장황(verbose), 내 코드보다 짧으면 난해(esoteric)

- 콜백 헬을 보고 뭐냐고 물어보면 CPS(Continuous Passing Style) 라고 답해줘라.

- 모든 if 문은 삼항 연산자로 써라, 누가 뭐라고 하면, "아 if 는 문이고 삼항은 식이니까요"

- 리스트 컴프리헨션, 옵셔널 체이닝, 리엑티브 등을 쓰고 자랑스럽게 말해라 "모나딕하게 해결했다고",
그게 뭐냐고 물어보면 "모나드의 저주로 인하여 설명하기 힘들다" 까지 말하는 거까지 해야한다.

- 두 개 이상 실행되는 서비스가 있으면 MSA(Micro-Service Architecture) 다.
테스트를 돌려주는 스크립트만 따로 있어도 MSA 다.
거기에 언어가 다르면 폴리글랏(polyglot)까지 했다고 말할 수 있다.
```

### 언어
내 언어가 우월하다
```
- 언어논쟁에서는 선빵필승의 문장이 있다 "언어는 도구다"

- TypeScript, CoffeeScript, ClojureScript 등 JS 의 슈퍼셋은 일절 사용하지 않는다. 누가 뭐라고 하면 JS는 애초에 그렇게 설계된 언어이고 그것이 곧 근본이라 하자.

- 몇몇 언어는 굳이 내가 불평할 필요가 없다. wtfjs / golang.sucks 등 다른사람의 불평을 인용하자.
```

### 설계
어떻게 설계해도 돌아는 간다.
```
- 클래스, 인터페이스, 이넘, 맴버등 구조 설계에 대해서 뭐라고 하면, ADT 에서 합타입이 어쩌고 곱타입이 어쩌고

- 클래스에 기능이 너무 적으면, 아 그건 레코드로 쓰려고 했습니다.

- 상속이 합성보다 편하다. 누가 뭐라고 하면 OOP 에서는 당연히 상속을 써야하는게 맞다고 하면된다.

- null 은 10억불의 가치가 있다. 뭐든 애매하면 null 을 리턴해라

- Object 나 Any 는 폴리몰피즘의 극의이다. 뭐든 애매하면 Object 타입을 리턴해라,
Object 타입을 리턴하는 함수에서 null 을 리턴하도록 하는게 베스트
```

### 테스트
솔직히 테스트코드 짜는 건 재미없다
```
- 테스트코드를 전혀 작성하지 않는다. 누가 뭐라고 하면 repl 로 테스트가 끝났다고 해라.

- 테스트가 어떨때는 성공하고 어떨때는 실패하면, "속성 기반 테스트" 를 작성해서 그렇다고 해라

-  테스트코드가 없어도, 코드가 제대로 동작한다는 것을 내가 설명할 수 있다고 해라. 누가 테스트코드를 요구한다면 내 코드는 너무 복잡해서 테스트 할 수 없다고 해라
```

### 성능최적화
CPU 성능은 내 실력과 달리 날로 발전한다.
```
- DTO/VO 변환은 쓰지 않는다. 누가 뭐라고 하면 성능 최적화라고 해라

- DTO/VO 는 물론 어떤 Model 도 만들지 않는다. 모두 Map (Dictionary) 자료구조를 사용하자. 누가 뭐라고 하면 Data Oriented Programming 라고 해라.
물론 Validation 같은건 안한다.

- DB 는 그때 그때 필요한 필드를 추가 해라. 정규화나 규칙은 생각조차 하지말아라. 누가 뭐라고 하면 이 또한 성능 최적화

- 패턴이나 아키텍처는 쓰지 않는다. 클래스로도 나누지 마라. N 중 포문과 if 문으로 절차적으로 작성해라,
누가 뭐라고 하면 이건 진짜 성능 최적화라고 해라

- 성능최적화는 그 어떠한 경우에도 금물, 누가 뭐라고 하면 요즘은 "컴파일러" 한테 맡기는게 대세라고 해라

- 개"발적 화"합을 추구한다.
```

## 휴먼 오토(Human Automation)

내가 편하기 위해선 일을 최대한 오토로 돌려야한다. 

어차피 누군가는 그 일을 맡을 것이다. 

그 말은 즉 나만 아니면 자동화(Human Automation)를 이뤘단 것이다.

### 백엔드
백앤드는 모던 비즈니스의 핵심이다. 엄한데 힘빼지 말자
```
- 그건 프론트엔드가 해야 할 일이라고 해라.
- 그건 원래 백앤드가 프론트엔드보다 바쁘다고 해라.
- 그건 DBA 가 해야 할 일이라고 해라.
- 그건 DevOps 엔지니어가 해야할 일이라고 해라.
- 그건 기획팀에서 먼저 기획해야할 일이라고 해라.
- 그건 운영팀에게서 먼저 확인받아야할 일이라고 해라.
```

### 프론트엔드

프론트엔드는 유저가 마주하는 첫인상이다. 엄한데 힘빼지 말자
```
- 그건 백엔드가 해야 할 일이라고 해라.
- 그건 원래 프론트엔드가 백엔드보다 바쁘다고 해라.
- 그건 앱 개발자가 해야 할 일이라고 해라.
- 그건 퍼블리셔가 해야 할 일이라고 해라.
- 그건 디자이너가 해야 할 일이라고 해라.
- 그건 유저가 해야 할 일이라고 해라.
- 그건 버그가 아니라 이스터에그라고 해라.
- 그건 디자인이 원래 그렇다고 해라.
```
### DBA

DBMS 개발자를 믿자

```
- N+1 문제가 자동으로 해결되지 않는 이 세상이 이상한거다. 개발자는 신경쓰지 말자.

- fetch join + paging 문제가 자동으로 해결되지 않는 이 세상이 이상한거다. 개발자는 신경쓰지 말자.

- slow query 문제가 자동으로 해결되지 않는 이 세상이 이상한거다. 개발자는 신경쓰지 말자.

- SQL / ORM 등에서 힘겹게 쿼링하는것보다 그냥 다 불러와서 map/reduce/filter 쓰는게 더 편하다.
```

### 머신러닝
요즘 기계는 대충 가르쳐도 알아서 잘 배운다.

```
- 데이터 하나가 소중한 시점에 Validation set 에 떼줄 데이터 따위 없다. 죄다 학습에 넣어버리자.

- 오버피팅이 일어나면 오히려 좋다. 누군가 딴지를 걸면 "실험 환경에서는 성능이 좋았는데요."라고 말하자.

- 성능이 너무 낮으면 데이터가 부족하기 때문이라고 하자.

- 모델이 너무 크다면 딥러닝이 원래 그런거라고 하자.

- 모델이 너무 작다면 모델 최적화의 결과라고 하자. 최적화의 부작용으로 성능이 조금 떨어질 수 있다는 점도 곁들여주면 좋다.

- training 이 너무 오래 걸린다고하면, 더 좋은 GPU 를 쓰면 된다고 하면서 NVIDIA DGX A100 같은 것을 보여주자.

- inference 가 너무 오래 걸린다고하면, 더 좋은 GPU 를 쓰면 된다고 하면서 NVIDIA V100 같은 것을 보여주자.

- Productization 은 DevOps, MLOps 엔지니어의 역할이다. 모델 리서처는 신경쓰지 말자.
```

### 기획

IT 서비스 기획자는 서비스에 계획 및 로드맵 수립 + 협의를 주도하고 프로젝트를 관리한다. 모두 개발자에게 맡기면 된다.

```
- 그건 개발자가 알아서 해야 할 일이라고 해라.

- 그건 개발자의 실력이 부족해서 그런거라고 해라.

- 잘못된 기획을 해도 그거는 개발자들이 알아서 잘 만들면 된다고 해라.

- 기획이 변경되어도 그거는 개발자들이 알아서 잘 만들면 된다고 해라.

- 내 일정은 소중하지만 전체 일정은 관심이 없다 나만 야근 안하면 된다. 

- 그냥 PPT 를 빨리 찍어서 개발자와 디자이너에게 업무요청을하고 설명해주고 손털면 끝이다. 이후에 질문들은 바쁘다고 최대한 피하던가 휴가를 사용하자.

- 위에서 이 기획안으로 진행해야한다고 결정했다고만 말해라.

- 위에서 결과물을 가지고 쪼으면 개발자들이 퍼포먼스가 안나온다고 말해라.

```

## 기타
솔직히 좀 뇌절인듯
```
- 그 날 배운 기술은 그 날 회사 프로젝트에 적용해라. 누가 뭐라고 하면 그 날 배운 지식을 자랑하면된다

- 기술 스택을 공부 하지 말고, 해당 기술 스택의 단점리스트만 공부해라. 누가 해당 기술 스택을 물어보면, 단점을 들먹이자

- 도커같이 가상화가 조금이라도 들어간건 사용하지 말아라. 누가 뭐라고하면 네이티브 환경에서의 확인이 필요하다고 해라

- 간단한 기능만 짜놓고 열심히 하는 척 게으름 피우자. 누가 뭐라고 하면 '린Lean'하게
```


# Reference
놀랍게도 꽤 많이 참고했다
- [유지보수하기 어렵게 코딩하는 방법: 평생 개발자로 먹고 살 수 있다](https://www.hanbit.co.kr/store/books/look.php?p_code=E2375873090)
- [애자일 선언](https://agilemanifesto.org/iso/ko/manifesto.html)
- [프로그래밍의 정석](http://www.yes24.com/Product/Goods/55254076)
- [7가지 동시성 모델](http://www.yes24.com/Product/Goods/29331038)
- [폴리글랏 프로그래밍](http://www.yes24.com/Product/Goods/12204890)
- [클린 코드](http://www.yes24.com/Product/Goods/11681152)
- [클린 아키텍쳐](http://www.yes24.com/Product/Goods/77283734)
- [클로저 프로그래밍의 즐거움](http://www.yes24.com/Product/Goods/24555451)
- [프로그래밍 스칼라](http://www.yes24.com/Product/Goods/27767797)
- [FSharp Fun and Profit 블로그](https://fsharpforfunandprofit.com/)
- [로버트 C 마틴 블로그](https://blog.cleancoder.com/)
- [마틴파울러 블로그](https://martinfowler.com/)
- [wtfjs](https://github.com/denysdovhan/wtfjs) / [golang suck](http://www.golang.sucks/)
- [코딩 호러의 이펙티브 프로그래밍](http://www.yes24.com/Product/Goods/8611802)
- [Data Oriented Programming](https://www.manning.com/books/data-oriented-programming)
- 그외 언젠가 한번쯤 읽어본 책들 다수
- 그외 언젠가 한번쯤 읽어볼 책들 다수
- 나무위키

# Contributing
더 좋은 주둥아리 방법을 알고있다면 PR 을 날려주세요

# License
JDD 는 어떠한 제약조건도 없습니다.
단 책임도 지지 않습니다.
