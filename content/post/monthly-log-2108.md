---
date: "2021-08-30T01:01:00Z"
title: 월간 기술 스크랩 21/08
categories:
- Newsletter
description: 흥미롭게 읽은 글이나 새로 알게 된 기술 등을 소개합니다. (2021년 8월)
summary: 흥미롭게 읽은 글이나 새로 알게 된 기술 등을 소개합니다. (2021년 8월)
draft: false
hiddenfromhomepage: true
---

## ✍️ 글

### [페이스북은 이제 메타버스 기업](https://c-rocket.net/facebook_mark_zuckerberg_metaverse_the_verge/)

The Verge에서 마크 주커버그 페이스북 CEO와 진행한 인터뷰의 한국어 번역본.

페이스북에서 VR/AR 관련 사업을 하는 직원의 수가 30% 가까이 된다는 글을 얼핏 본적이 있는데,
페이스북이 무엇보다 메타버스와 VR 사업에 진심임을 알 수 있는 주커버그의 인터뷰입니다.

2010년대가 스마트폰의 시대였다면, 2020년대는 VR의 시대가 될지도 모르겠네요.

### [70만번 다운로드 된 NPM 패키지: `-`](https://www.bleepingcomputer.com/news/software/empty-npm-package-has-over-700-000-downloads-heres-why/)

NPM에서 `-`라는 이름의 내용 없는 패키지가 70만번이나 다운로드 되었는데,
그 원인을 살펴보는 아티클.

원인은 단순히 사람들이 패키지를 설치하는 과정에서
플래그를 지정하다가 실수로 띄어쓰기를 삽입해서 (`-P` --> `- P`) 발생했을 것이라고 하는데요.
해당 패키지의 개발자는 NPM의 패키지 명명 규칙을 확인하는 차원에서 `-` 패키지를 업로드했었다고 합니다.

누구나 자유롭게 패키지 업로드가 가능한 NPM이나 PyPI에서 악성코드가 발견되는 경우가 심심찮게 발생하고 있는 상황에서,
사람들의 실수로 발생할 수 있는 이번 경우와 같은 케이스를 예방하는 기능이 필요하지 않을까 싶기도 하네요.

### [Git switch and restore](https://www.banterly.net/2021/07/31/new-in-git-switch-and-restore/)

Git 2.23에서 생긴 커맨드인 `git switch`와 `git restore`를 소개하는 글.

`git switch`는 브랜치를 전환하는 기능, `git restore`는 파일을 복원하는 기능을 합니다.
기존에는 두 기능 모두 `git checkout`을 이용해서 수행했었는데요.

`git checkout` 커맨드는 git의 원리를 잘 이해하는 사람에게 있어서는 문제가 없었으나,
처음 git을 배우는 사람에게는 대체 왜 이 커맨드가 때로는 브랜치를 생성하고, 때로는 파일을 복원하는지
이해하기 어려운 측면이 있었습니다.

아직 많은 git 튜토리얼에서 checkout을 많이 사용하는데요.
git 2.23이 공개된지 벌써 2년이 넘었으니, 이제는 checkout대신 switch와 restore를 많이 사용해보시면 어떨까 싶네요.

### [깃헙 엔지니어링 팀은 이제 Codespaces를 이용해 개발합니다](https://github.blog/2021-08-11-githubs-engineering-team-moved-codespaces/)

깃헙 Codespaces 정식 런칭과 함께 공개된 깃헙 블로그 아티클.

깃헙 엔지니어링 팀이 Mac 노트북에서 로컬로 개발하다,
깃헙에서 제공하는 클라우드 개발환경인 Codespaces로 옮겨갔다는 이야기입니다.

전체적인 글 내용은 클라우드 환경으로 옮기면서,
Mac용 스크립트를 리눅스 환경에 맞추어 포팅하고,
빠른 초기화를 위해서 여러가지 기법들을 활용했다는 이야기인데요.

내용 자체보다는 앞으로 이렇게 클라우드를 사용해서 개발을 하는 일이 굉장히 흔해지지 않을까 하는 생각이 들어 글을 가져와봤습니다.
작은 프로덕트를 만드는 작은 기업에서야 굳이 클라우드 개발 환경을 쓸 필요가 없겠지만,
계속 엔지니어가 들어오고 나가고,
프로덕트의 크기도 커서 개발 환경 구축에 이슈가 자주 발생하는 큰 프로젝트라면,
클라우드 기반의 접근법이 굉장히 유효할 것 같네요.

여담으로, 개인적으로 Codespaces를 아주 잘 쓰고 있었는데
이제 엔터프라이즈를 대상으로 유료로 운영한다고 하니 아쉽습니다 ㅎㅎ..

### [스카이림의 수레와 벌, 여우와 보물](https://imseongkang.wordpress.com/2021/08/22/skylimdevstory/)

명작 RPG 게임 스카이림 개발 과정에서 있었던 흥미로운 사실들에 대한 개발자들의 뒷 얘기.

"도망치는 여우를 따라가면 보물이 나온다"라는 플레이어들 사이에서의 팁이 있었는데,
이는 개발자들의 의도한 것이 아니라 NPC의 이동 AI 로직에 따라 발생한 특수한 현상이었다고 합니다.


## 📌 북마크

### [WebRTC에 대해서 당신이 알고싶어 할 모든 것](https://blog.openreplay.com/everything-you-ever-wanted-to-know-about-webrtc)

클라이언트간 실시간 통신이 가능하게 해주는 WebRTC 기술의 주요 API를 소개해주는 문서입니다.

### [Relate SaaS 리스트](https://saas.relate.kr/)

스타트업에서 유용하게 사용할 수 있는 SaaS 리스트입니다.

## 📰 기술 뉴스

### [스택 오버플로우 2021년 개발자 설문조사](https://stackoverflow.blog/2021/08/02/2021-stack-overflow-developer-survey-results/)

매년 진행하는 스택 오버플로우 개발자 설문조사.

코로나의 여파로 온라인을 이용하여 개발을 배우는 사람이 많이 늘어난듯한 모습이네요.

한가지 흥미로운 건 웹 프레임워크에서 Svelte와 FastAPI의 인기가 굉장히 높았다는 점인데요.
실제 업무에 많이 사용되는지와는 별개로 "힙"한 프레임워크를 사람들이 많이 좋아하는 현상이라고 볼 수 있지 않을까 싶습니다.

### [지구온난화가 GPS를 마비시킬 수도 있다](https://mobile.twitter.com/ariadneconill/status/1422163289518313474)

지구의 자전속도는 일정하지 않고 점진적으로 느려지는 것으로 알려져 있는데요.
이 때문에 종종 자전속도의 변화에 맞춰 일초를 추가하는 윤초를 삽입하고는 합니다.

지난 십수년동안에는 평균적으로 1년에 한번 정도 윤초가 발생했고,
그래서 GPS 소프트웨어가 "2021년도에는 윤초가 대략 몇개 이상 쌓였을 거고, 그렇지 않으면 버그니까 시간을 초기화하자",
라는 로직을 가지고 있었다고 하는데요.

문제는 지구온난화가 지구의 자전을 가속시켜 최근에는 윤초가 발생하지 않았고, 오히려 마이너스 윤초를 발생시킬 수도 있는 상황이라고 합니다.
이 때문에 GPS의 해당 로직이 오작동해서 큰 버그를 발생시킬 수도 있다는 소식입니다.

이 소식을 보고 드는 생각은 두 가지인데,
윤초와 같이 인간이 전혀 예상할 수 없는 사건을 처리하는 것이 개발자 입장에서 참 고역이겠구나 하는 것과,
지구온난화가 정말 생활 곳곳에 영향을 미칠 수 있구나 하는 것입니다.

### [Vue.js가 위키미디어 재단의 새 프레임워크로 선택되다](https://lists.wikimedia.org/hyperkitty/list/wikitech-l@lists.wikimedia.org/thread/SOZREBYR36PUNFZXMIUBVAIOQI4N7PDU/)

Vue.js가 위키미디어 재단의 차세대 프레임워크로 선택되었습니다.
몇년 뒤면 Vue.js로 만들어진 위키피디아를 볼 수 있겠네요.

프레임워크 선택에 관해서 논의한 [RFC를 보면](https://phabricator.wikimedia.org/T241180),
React와 비교해서 Vue를 선택한 이유를 살펴볼 수 있는데요.
특정 회사(Facebook)의 목표에 따라 굉장히 빠르게 Best practice가 변하고, breaking changes도 잦은 React는,
아주 천천히 진행될 위키미디어 재단의 프로젝트 속도와는 맞지 않는 면이 있다고 합니다.


## ⚙️ 소프트웨어 / 프로젝트

### [Brython](https://github.com/brython-dev/brython)

Browser Python. 파이썬을 브라우저 환경에서 실행시키는 프로젝트.

비슷한 프로젝트로 이전에 [pyodide](https://github.com/pyodide/pyodide)를 소개 한 적이 있는데요.
두 프로젝트의 목표는 비슷하지만 방식은 다릅니다.

pyodide는 CPython 인터프리터를 Wasm으로 컴파일해서 파이썬 코드를 실행하는 방식이라면,
brython은 파이썬 코드를 js로 트랜스컴파일하는 방식을 사용합니다.

스타 수로 봤을 때 두 프로젝트의 인기도는 비슷한데,
확장성 측면에서는 pyodide의 손을 들어주고 싶네요.

### [StackOverflow Importer](https://github.com/drathier/stack-overflow-import)

파이썬 import 시스템을 오버라이딩하여, 스택 오버플로우에서 코드를 검색해서 임포트 해주는 파이썬 라이브러리.
당연히 실사용 용도는 아니고, 재미로 만든 프로젝트.

import 시스템을 이런 식으로 변형할 수 있다는 점도 흥미롭고, 아이디어가 참 재밌습니다.

### [Earthly](https://github.com/earthly/earthly)

컨테이너 시대의 빌드 자동화 도구라고 자신을 소개하는 프로젝트.

Makefile과 Dockerfile이 결혼해서 아이를 낳았다(?) 라고도 자신을 표현하는데,
직관적으로 이해하기에는 이 표현이 꽤나 적절합니다.

빌드하기 위해서 복잡한 디펜던시가 필요한 프로젝트의 경우,
빌드에 필요한 디펜던시를 설치한 컨테이너 개발 환경을 만들고,
그 안에서 빌드를 하는 방식을 종종 사용합니다.
즉, 이 경우에는 컨테이너 개발 환경 구성에 필요한 Dockerfile과, 빌드에 필요한 Makefile 두 개가 필요하게 되죠.

Earthly는 이 둘을 합친 Earthfile을 제시합니다.
문법만 살펴봐도 Dockerfile과 Makefile을 합쳐놓은 듯한 느낌이 물씬 풍깁니다.

이렇게 하면 언제 어디서나 Earthfile 하나로 똑같은 환경에서 빌드할 수 있고,
더 CI friendly 하다는 것이 요지입니다.

아직 1년 조금 넘은 굉장히 젊은 프로젝트인데, 앞으로 더 발전할 수 있을지 지켜볼만한 프로젝트인듯 합니다.

### [neverinstall](https://neverinstall.com/)

크롬, VS Code와 같은 데스크톱 앱을 브라우저 상에서 실행해주는 서비스.

간단히 생각하면 한 가지 프로그램만 사용 가능한 크롬 원격 데스크탑을 띄우는 느낌입니다.
서버가 미국에 있어서 인지 한국에서 실행하면 다소 레이턴시가 느려서 답답한 느낌이 있습니다.

ProductHunt에서 인기를 끌었는데, 아무래도 이런 서비스는 보안이나 개인정보가 꽤 중요한 요소라
이런 작은 서비스를 쓰는 건 좀 꺼려지는 부분이 있는데요.
무료로 제공하는 인스턴스가 있으니 가끔 필요할 때는 사용해봄직 합니다.

## 📙 책 / 강의 / 영상

### [How to avoid machine learning pitfalls: a guide for academic researchers](https://papers.labml.ai/paper/2108.02497)

학술계에서 머신 러닝 연구를 하는 연구자들을 위한, 함정에 빠지지 않는 법.

머신 러닝을 실제 업무에 적용하는 경우에야 사실 결과 지표만 잘나오면 괜찮지만,
연구를 한다면 정확하고 엄밀한 결과를 리포팅하기 위해 고려해야하는 요소들이 참 많습니다.
머신 러닝 연구를 하면서 발생할 수 있는 다양한 실수(함정)들을 방지하는 방법을 알려주는 페이퍼인데요.
머신 러닝 연구를 처음 시작하는 학생, 대학원생들이 참고해보면 좋을 듯 합니다.


