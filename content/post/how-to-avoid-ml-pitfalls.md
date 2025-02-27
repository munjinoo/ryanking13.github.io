---
date: "2021-09-11T01:01:00Z"
title: 머신러닝 연구자들을 위한 제언 (번역)
categories:
- Machine Learning
description: 머신러닝 연구자들을 위한 제언
summary: 머신러닝 연구를 시작하려는 연구자들이 알아야하는 팁을 소개합니다.
draft: False
---

> __원문:__ [*"How to avoid machine learning pitfalls: a guide for academic researchers"* (M. A. Lones)](https://arxiv.org/abs/2108.02497)

> __Note:__ 가볍게 읽으실 수 있도록 많은 부분이 생략 및 의역되어 있습니다. <br /> 이 글이 마음에 드셨다면 원문을 꼭 읽어보시는 것을 추천드립니다.

## 들어가며

이 글은 머신러닝 연구를 막 시작한 학생들과 풋내기 연구자들을 대상으로,
연구를 하면서 발생하는 여러 가지 실수들을
방지하는 데에 도움을 주고자 작성되었습니다.
이 글이 다른 많은 머신러닝 튜토리얼과 다른 점은,
이 글에서 소개하는 내용은 학계에서
머신러닝 연구를 하는 사람들을 주 독자로 한다는 점입니다.
즉, 연구 내용을 논문으로 출판하기 위해
실험 결과를 엄격하게 평가하고 정당하게 비교해야하는 사람들을 대상으로 합니다.

## 1. 모델을 만들기 전에 해야할 일

여러분이 오늘 새로운 연구를 시작했다면,
여러분이 생각한 반짝이는 아이디어를 바탕으로
곧바로 모델을 학습시키고 평가하고 싶을 것입니다.
그러나 두근거림을 가라앉히세요.
여러분이 가장 먼저 해야할 것은 시간을 두고 신중하게 프로젝트의 목표를 점검하고,
데이터를 완전히 이해하는 작업입니다.

### 1.1. 데이터를 살펴보세요

머신러닝 "연구"를 한다는 것은
최종적으로 여러분의 작업을 논문 등의 형태로 발표하고자 하는 것을 말합니다.
공개된 장소에 연구 결과를 발표하기 위해서는 연구에 사용하는 데이터가
신뢰할 수 있는 출처에서 나왔는지,
올바른 방법론을 이용해서 수집되었는지,
그리고 데이터의 퀄리티가 충분히 좋은지를 확인해야 합니다.

예를 들어,
인터넷에서 찾은 데이터를 연구에 사용한다면
그게 어디서 만든 데이터인지를 알아야 합니다.
다른 논문에서 공개된 데이터라면,
그 논문을 살펴보고 믿을만한 기관에서 출판된 논문인지,
저자들이 데이터의 한계점이나 퀄리티에 대해서 논문에 명시해뒀는지 살펴보아야 합니다.
데이터가 여러 논문에서 이미 사용되었다고해서
그 데이터가 좋은 퀄리티일 것이라고 의심없이 믿으면 안 됩니다.

머신러닝 업계에는 *"쓰레기가 들어가면 쓰레기가 나온다"* 는 유명한 격언이 있습니다.
이는 데이터가 안 좋으면 좋은 모델이 나올 수 없음을 의미합니다.
데이터를 살펴보면서, 빠지거나 불완전한 데이터가 있는지 확인하세요.
귀찮더라도 미리 하는 것이 나중에
논문 리뷰어들에게 왜 안 좋은 데이터를 썼는지 설명하는 것보다 쉽습니다.

### 1.2. 모든 데이터를 보지 마세요

데이터를 살펴본다는 것은
빠진 데이터가 없는지, 데이터의 한계점이 무엇인지 검증하는 기능도 있지만
데이터가 가지고 있는 패턴과 같은 요소들을 알 수 있게 해주어
여러분이 모델링을 할 때에 인사이트를 얻을 수 있기도 합니다.
 
그러나 이 때 주의해야 할 점은 테스트 용도로 사용할 데이터를
자세히 살펴보아서는 안 된다는 점입니다.
테스트 데이터를 살펴보게 되면,
의식적으로든 무의식적으로든 데이터에 대한 *가정*을 하게 되고,
이는 모델의 일반화 성능을 해치게 됩니다.
이를 테스트 데이터의 정보가 유출되었다고 표현하며,
이것이 많은 경우에서 테스트 때는 좋은 성능을 보이던 모델이
실제로 프로덕션에 적용했을 때 나쁜 성능을 보이는 이유입니다.
 
### 1.3. 충분히 많은 데이터를 확보하세요
 
충분한 학습 데이터가 없으면 모델이 일반화하기 어렵다는 것은 잘 알려져 있습니다.
그러나 얼마나 많은 데이터가 필요한지 사전에 판단하는 것은 어렵습니다.
대부분은 학습을 해보아야만 알 수 있는데, 
데이터가 학습에 유용한 정보(signal)와 그렇지 않은 정보(noise)를
어느 정도의 비율로 가지고 있느냐에 따라 필요한 데이터량이 달라집니다.
학습에 유용한 정보가 많으면 적은 데이터로도 잘 학습할 수 있지만,
그렇지 않으면 더 많은 데이터가 필요하게 됩니다.

물론 충분한 양의 데이터를 구하기 어려운 경우도 있는데요
(사실 대부분의 경우에 그렇습니다).
이때는 적은 양의 데이터를 잘 활용하는 방법을 고민할 필요가 있습니다.
대표적으로는 교차 검증(cross validation)을 사용해서
검증의 정확도를 높이는 방법이 있습니다.
혹은 데이터 증강(data augmentation) 기법을 활용해서
데이터의 수를 늘리는 효과를 주는 것도 방법입니다.
데이터 증강은 데이터의 전체적인 수는 많지만, 일부가 부족할 때에도 유용한데요.
예를 들면 분류 문제에서 특정 클래스에 해당하는 인스턴스 수만 적은 경우가 있습니다.
이를 클래스 불균형(class imbalance) 문제라고 하는데 이 때에도 데이터 증강이 해법이 될 수 있습니다.
 
또 한 가지 데이터가 적을 때 신경써야 하는 부분은 모델의 복잡도를 조절하는 것입니다.
딥 뉴럴네트워크 모델은 파라미터의 수가 굉장히 많은데,
데이터가 적으면 파라미터가 많은 모델일 수록 과적합되기 쉽습니다.
이러한 문제가 발생한다면 빠르게 알아채고 적절한 전략으로 해결하는 것이 중요합니다.
 
### 1.4. 도메인 전문가들과 소통하세요
 
여러분이 풀고자 하는 문제에 대한 도메인 지식이 부족하다면, 해당 도메인 전문가들의 의견을 경청하세요.
그들은 여러분이 풀고자 하는 문제를 이해하는데 도움을 줄 것입니다.
여러분이 데이터를 이해하고 유의미한 특성을 골라내는 데 도움을 줄 것이고,
가장 적절한 방법론과 모델을 찾는데 도움을 줄 것입니다.
또한 여러분의 연구를 투고하기에 가장 적합한 학회가 어디인지도 알려줄 것입니다.

도메인 전문가의 의견을 듣지 않은 채로 연구를 진행하다보면,
의미없는 문제를 풀거나, 의미있는 문제를 잘못된 방법으로 풀게될 수 있습니다.
예를 들어 의료나 금융처럼 모델의 결과를 해석하는 것이 굉장히 중요한 분야에서
블랙박스(black-box) 모델을 사용해서 문제를 풀었다면,
이는 잘못된 방법으로 문제를 푼 것에 해당할 것입니다.
 
### 1.5. 많은 사전 조사를 하세요
   
분명 여러분이 풀고 싶은 문제는 다른 누군가도 풀고 싶어했던 문제일 것입니다.
그러므로 이미 이루어진 연구과 안 이루어진 연구를 구분하는 것이 중요합니다.

다른 연구자가 이미 여러분이 하고자 하는 연구를 했다는 것은 나쁜 소식이 아닙니다.
지식의 발전은 점진적인 과정입니다. 과거의 연구는 다음 연구의 이정표가 됩니다.
다른 사람이 여러분의 좋은 아이디어를 이미 출판한 것을 발견했다면,
그 순간에는 좌절스러울 지도 모릅니다.
그러나 보통 한 연구는 여러 가지 후속 연구를 할 수 있는 지점들을 남겨놓기 마련입니다.
그들의 연구를 바탕으로 그들이 풀지 못한 문제를 풀어보세요.
또한 그들의 연구가 여러분의 연구의 필요성을 정당화시켜주기도 할 것입니다.

만약 여러분이 과거의 연구에 대해 미리 충분히 조사하지 않으면
중요한 정보들을 놓칠 수 있습니다.
그러므로 연구 시작 전에 조사를 많이 하는 것이 중요합니다.
이러한 과정을 연구 초반에 진행하지 않으면,
언젠가 왜 이미 했던 연구를 여러분이 또 했는지 설명하는 것이 힘들어질 것입니다.
   
### 1.6. 모델이 배포되는 상황을 고려하세요

머신러닝 모델을 만드는 이유는 최종적으로는 배포하기 위한 것입니다.
많은 수의 학계 연구들은 논문을 쓰기 위한 연구에 그치고
현실에서 쓸 수 있는 모델을 만드는데 목표를 두지 않는 경우가 많습니다.
이는 연구 측면에서는 괜찮을 수 있지만,
결국 모든 연구의 최종적인 목표는
현실에 적용될 수 있는 모델을 만드는 것이 되어야 합니다.

이를 염두에 두고 연구를 진행하려면
나중에 모델을 어떻게 배포할 지를 고려하여야 합니다.
예를 들어 하드웨어 리소스가 부족한 환경에 배포하는 경우,
대표적으로는 IoT 환경이나 로봇같은 시스템에 배포하여야 한다면
모델의 복잡도가 그에 맞춰 제한되어야 합니다.
혹은 자율주행처럼 실시간으로 판단을 내려야하는 경우라면
모델의 추론 시간을 주요한 요소로 고려하여야 합니다.

또 다른 측면에서는
머신러닝 모델이 다른 소프트웨어 시스템과
조합되어 배포되는 환경도 고려하여야 합니다.
이와 같이 머신러닝 모델의 배포와 관련된 부분은
굉장히 복잡하며, 최근에는 MLOps라는 이름으로 많이 연구가 되고 있습니다.
   
## 2. 신뢰할 수 있는 모델을 만드는 방법
   
모델을 만드는 것은 머신러닝 연구에서
제일 재미있는 부분 중 하나입니다.
텐서플로우나 파이토치와 같은 최신 머신러닝 프레임워크를 활용하면
코드 몇 줄로 온갖 종류의 알고리즘을 조합해
좋은 성능을 보이는 모델을 쉽게 만들 수 있습니다.

그러나 이것저것 다 해보고 제일 좋은 걸 고르는 방식의 접근은
전혀 통제되지 않은 수많은 실험을 낳게 되고,
결과적으로 여러분이 왜 그런 선택을 했는지를 정당화하기가 어렵습니다.
그러므로 모델을 만들 때에는 잘 조직된 방식으로 해야합니다.
데이터를 올바르게 쓰고 있는지 확인하고,
적절한 요소들을 고려해 모델을 만들어야 합니다.
   
### 2.1. 테스트 데이터의 정보가 유출되지 않게 하세요
   
여러분이 만든 모델이 얼마나 잘 일반화되는 지를 확인하기 위해
테스트 데이터를 두는 것은 아주 중요합니다.
문제는 테스트 데이터에 대한 정보가
학습 과정 또는 모델 선택 과정에 유출되는 것이
아주 흔하게 발생하는 실수라는 점입니다.
이러한 일이 발생하면, 해당 테스트 데이터는
더 이상 모델의 일반화 성능을 측정하기 위한 적절한 기준이 되지 못합니다.
이것이 많은 머신러닝 모델들이
현실 세계의 데이터에 좋은 결과를 보이지 못하는 흔한 이유입니다.

테스트 데이터에서 유출될 수 있는 정보의 종류는 아주 다양합니다.
흔한 예로는 데이터 준비과정에서
테스트 데이터의 평균과 분산을 알고 데이터 스케일링을 하는 경우가 있습니다.
테스트 데이터의 정보 유출을 방지하기 위해서는
학습 과정에서 모든 작업은 오로지 학습 데이터만을 이용해서 수행되어야 합니다.

다른 예로는 학습/테스트 데이터를 나누기 전에 학습에 사용할 특성(feature)를 고르는 것,
서로 다른 모델의 일반화 성능을 평가하기 위해
같은 테스트 데이터를 쓰는 것 등이 있습니다.
이러한 실수를 예방하는 가장 좋은 방법은 프로젝트가 시작하자마자
학습 데이터와 테스트 데이터를 나누고
테스트 데이터는 오로지 마지막에 나온 한 모델의
일반화 성능을 측정하는데만 사용하는 것입니다.
  
### 2.1. 다양한 모델을 사용해보세요
  
일반적으로, 어디에서나 가장 좋은 성능을 보이는 유일한 머신러닝 모델은 없습니다.
공짜 점심은 없다(*No Free Lunch*)는 유명한 법칙의 말대로,
특정 모델이 모든 문제에서 뛰어날 수는 없죠.

그러므로 여러분이 할 일은 특정한
한 가지 문제를 가장 잘 풀어내는 모델을 찾는 것입니다.
여러분이 하고자 하는 연구 분야에
이미 좋은 퀄리티의 사전 지식을 제공하는 선행 연구가 있었다면,
그것을 등불로 삼아 모델링을 진행하면 됩니다.
그러나 대다수의 경우 여러분은
스스로 어둠 속에서 빛을 찾아가야 하는 입장이 될 것입니다.

다행히도 최신 머신러닝 라이브러리를 사용하면 여러가지 모델을 조금의 코드 수정을 통해 쉽게 바꿔가며 실험하는 것이 가능합니다.
그러므로 여러 가지 다른 모델을 사용해보기를 바랍니다.
  
### 2.3. 부적절한 모델 사용하지 않기

다양한 모델을 사용해보는 것은 좋지만,
부적절한 모델을 사용해서는 안됩니다.
최신 머신러닝 라이브러리들은 간단한 API 형태로 모델을 사용할 수 있다보니,
모델에 대해 제대로 이해하지 못한 채 종종 여러분의 데이터와는 맞지 않는
부적절한 모델을 사용하게 되는 경우가 있습니다.
예를 들면 범주형(categorical) 데이터를 입력으로 받는 모델에
수치형(numeric) 값을 입력한다거나,
데이터 간의 종속성이 없다고 가정하는 모델에
시계열 데이터를 입력하는 것 등이 있을 수 있습니다.

또 다른 예시는 불필요하게 복잡한 모델을 사용하는 것입니다.
예를 들어 여러분이 가진 데이터의 수가 매우 적거나,
모델의 추론 결과에 대한 해석이 필요하다면
블랙박스 딥 뉴럴네트워크 모델을 사용하는 것은 적합하지 않을 것입니다.

마지막으로 "최신" 모델이라는 점을 여러분이 그 모델을 사용하는 것을
정당화 하는 이유로 사용하지 마세요.
오래되었어도 깊이 연구되고 만들어진 모델이 더 좋은 결과를 보이는 경우가 많습니다.
  
### 2.4. 하이퍼파라미터를 최적화하세요
  
대부분의 머신러닝 모델에는 하이퍼파라미터가 있습니다.
모델의 구조나 학습에 관계된 여러 가지 설정값들은 대부분
자동으로 최적화할 수 없는 하이퍼파라미터입니다.
이러한 하이퍼파라미터들은 모델의 성능에 아주 큰 영향을 주는 경우가 많고,
어느 경우에나 잘 들어맞는 값이 존재하는 경우는 드뭅니다.

그러므로 여러분이 가진 특정한 데이터에 맞는
적절한 하이퍼파라미터값을 직접 찾을 필요가 있습니다.
이 때, 여러 하이퍼파라미터를
마구잡이로 조정해보다가 운 좋게 만족스러운 결과가 나올 수도 있겠지만,
그렇게 하기보다는 적절한 하이퍼파라미터 최적화 전략을 사용하는 것이
나중에 여러분의 선택을 정당화하는데 더 도움을 줄 것입니다.

대표적인 하이퍼파라미터 탐색 전략은 랜덤 탐색, 그리드 탐색 등이 있는데요.
이는 하이퍼파라미터의 수가 많아지거나
모델을 학습시키는데 너무 오랜 시간이 든다면 현실적으로 적합하지 않을 수도 있습니다.
이 경우에는 최적의 설정을 찾기 위해 적합한 도구와 기법을 찾을 필요가 있습니다.
한편으로 또 다른 접근법은 AutoML 기법을 사용해서
모델 선택과 하이퍼파라미터를 함께 최적화하는 것입니다.
## 3. 모델을 올바르게 평가하는 방법
  
여러분의 연구 결과를 학계에 보고하려면,
유효한 결과로부터 얻어지는 유의미한 결론이 필요합니다.
그러나 안타깝게도 머신러닝 모델을 올바르고 공정하게
평가하는 것은 쉽지 않은 문제입니다.
그러므로 모델의 성능을 평가하는 데에는 아주 신중한 접근이 필요합니다.
 
 ### 3.1. 적절한 테스트 데이터를 사용하세요
 
 모델의 평가에 있어 가장 중요한 것은
 모델의 일반화 성능을 평가할 수 있는
 좋은 테스트 데이터를 사용하는 것입니다.
 학습 데이터에 모델이 좋은 성능을 보이는 것은 대체로 무의미합니다.
 충분히 복잡한 모델은 일반화된 정보는 얻지 않은 채로
 학습 데이터가 가진 모든 정보를 얻을 수 있기 때문입니다.

 테스트 데이터에 포함된 데이터가 적합한 지를 판단해보세요.
 테스트 데이터는 학습 데이터가 중복되어서는 안 되고,
 더 넓은 분포를 대표할 수 있어야 합니다.
 예를 들어, 사진 데이터를 분류하는 문제에서
 학습 데이터와 테스트 데이터가
 둘 다 야외의 햇살 좋은 날에 촬영된 사진이라면
 테스트 데이터가 충분히 다양한
 장소와 날씨의 분포를 고려하지 못하고 있다고 할 수 있습니다.
 또한 학습 데이터와 테스트 데이터를 촬영할 때
 완전히 똑같은 장비를 사용했다면,
 특정한 장비에서 발생하는 특징에 모델이 과적합 되어
 다른 장비에서 촬영된 데이터에는 맞지 않을 수 있습니다.

 위와 같이 잘못된 테스트 데이터를 사용하는 경우,
 모델의 일반화 성능에 대해 올바르지 않은 결론을 내게 됩니다.
 따라서 적절한 테스트 데이터를 선정하는 것이 무엇보다도 중요합니다.
 
 ### 3.2. 검증 데이터를 사용하세요
 
 머신러닝 연구에서
 여러 가지 모델을 학습하여 비교하는 것은 아주 일반적인 과정입니다.
 이 때 각 모델의 성능 실험에서 얻어지는 정보를
 다음 모델을 학습하고 실험할 때 활용하게 됩니다.

 이러한 반복적인 과정에서 테스트 데이터는 사용되어서는 안 되며,
 대신 별도의 검증(validation) 데이터를 만들어서 성능 평가에 사용해야 합니다.
 검증 데이터는 학습용 데이터와는 다르면서 학습 성능을 검증하기 위해 사용합니다.
 만약 테스트 데이터를 검증 목적으로 사용한다면,
 테스트 데이터가 학습 과정에 편입되고,
 이는 테스트 데이터가 더 이상 모델의 일반화 성능을 특정하는
 독립적인 데이터로 사용될 수 없음을 의미합니다
 (여러분의 모델이 점점 테스트 데이터에 오버피팅 될 것이니까요).

 검증 데이터를 사용했을 때 얻을 수 있는 다른 이점은
 학습 조기 종료(early stopping) 기법을 사용할 수 있다는 점입니다.
 조기 종료란 학습 과정에서 모델이
 검증 데이터에 대해서 최고 성능을 달성하고 점차 성능이 떨어지기 시작할 때,
 즉 학습 데이터에 오버피팅 되기 시작할 때,
 일찍 학습을 중단함으로써 가장 좋은 모델 성능을 얻는 방법입니다.
 
 ### 3.3. 모델을 여러 번 평가하세요
 
 많은 머신러닝 모델들은 불안정합니다.
 이는 학습 시의 랜덤 시드(random seed)가 달라지거나
 데이터에 미묘한 수정만 가해져도
 모델의 성능이 크게 차이날 수 있음을 의미합니다.

 그러므로 모델을 단 한 번 평가했을 때 나오는 결과는 신뢰하기가 어렵고,
 모델의 성능을 저평가 또는 고평가하게 될 위험이 있습니다.
 이 때문에 모델을 여러 번 평가하는 것이 중요합니다.
 모델을 여러 번 평가하는 방법은 여러 가지인데,
 대표적으로는 서로 다른 여러 학습 데이터를 이용해서
 모델을 학습하는 방법이 있고 그 중에서도 교차 검증(cross validation) 기법이 유명합니다.
 
 ### 3.4. 불균형한 데이터에는 정확도를 사용하지 마세요
 
모델 평가에 관하여 마지막으로 얘기할 것은,
모델을 평가하는 지표(metric)를 정할 때에 유의해야 할 부분입니다.

예를 들어, 분류 문제를 푸는 모델을 평가할 때,
가장 흔히 사용되는 지표는 정확도(accuracy)입니다.
이는 전체 데이터 중에서
올바르게 분류된 데이터의 비율을 바탕으로 모델을 평가하는 것인데요.
정확도는 클래스별 데이터의 개수가 균형 잡혀 있다면 괜찮은 평가 지표지만,
데이터의 개수가 불균형하다면 모델을 올바르게 평가할 수 없는 지표입니다.

예를 들어 이진 분류 문제에서 데이터의 90%가 한 클래스고 
10%만 다른 클래스라면,
분류기가 모든 데이터를 한 클래스로 추론하더라도
정확도는 90%가 나올 것입니다.
정확도는 높지만 이 분류기는 아무 쓸모가 없습니다.
이 경우 정확도 지표를 사용하여 모델을 평가했다가는
올바르지 않은 평가 결과가 나오겠죠.
이때는 클래스의 불균형에 영향을 받지 않는 지표를 사용해야만
모델을 올바르게 평가할 수 있습니다.
이와 같이 데이터의 특성에 따라 적절한 평가 지표를 선택해야만
모델을 올바르게 평가할 수 있습니다.
 
## 4. 모델을 공정하게 비교하는 방법 

 모델을 비교하는 것은 머신러닝 연구의 기본입니다.
 그렇지만 공정하게 모델을 비교하는 것은 매우 어려운 일이기도 합니다.
 만약 모델을 공정하게 비교하지 않은 채로 논문을 출판한다면,
 여러분의 논문이 좋지 않은 평가를 받을 뿐더러,
 나중에 여러분의 논문을 살펴볼 다른 연구자들에게까지 악영향을 끼칠 수 있습니다.
 
 ### 4.1. 더 큰 숫자가 더 좋은 모델을 의미하지 않습니다
 
 많은 논문들이 *"기존 연구는 정확도가 94%였는데 우리는 95%니까 우리 방법이 더 좋다"*
 라는 식으로 결론을 내리고는 합니다.
 그러나 단순히 높은 숫자가 더 좋은 모델을 의미하지는 않습니다.

 예를 들어, 모델이 같은 데이터를 사용했더라도
 학습 데이터와 평가 데이터를 나누는 방식이 달랐을 수 있습니다.
 이는 결과에 분명히 영향을 주는 요인으로,
 서로 다른 데이터를 사용했다면 당연히 성능에 큰 차이가 있을 것입니다.
 또 다른 이유로는 하이퍼파라미터의 최적화 정도에 차이가 있을 수 있습니다.
 한 모델은 기본적인 설정값을 사용했고,
 다른 모델은 철저하게 최적화된 하이퍼파라미터를 사용했다면
 성능에 차이가 있을 수밖에 없습니다.

 이와 같이 논문을 출판할 때
 사용하는 숫자들에는 굉장히 신중을 기울여야합니다.
 정말로 공정한 평가를 내리기 위해서는,
 두 모델을 완전히 새로 구현하고,
 둘 모두 같은 수준에서 최적화하고,
 여러 번의 평가를 수행해야 합니다.
 그리고 최종적으로 통계적으로 성능의 차이가 유의미한지를 분석해야합니다.
 
 ### 4.2 커뮤니티 벤치마크를 신뢰하지 마세요
 
 특정 도메인에서 연구를 수행하다보면
 새로운 모델을 평가하기 위해 사용되는
 벤치마크 데이터셋이 있는 경우가 많습니다.
 이는 모두가 같은 데이터를 사용함으로서
 모델의 성능을 투명하게 비교하기 위한 것입니다.

 그러나 벤치마크 데이터를 사용하는 방식은 몇 가지 한계점이 있습니다.
 먼저 테스트 데이터에 대한 접근이 허용되기 때문에,
 다른 사람들이 테스트 데이터에 대한 정보를
 학습 과정에 사용하였는지에 대한 여부를 알 수가 없습니다.
 테스트 데이터를 학습에 사용하게 되면 당연히 결과가 아주 이상적으로 나오게 되죠.

또 다른 미묘한 문제는,
모두가 테스트 데이터를 단 한 번만 사용해서 모델을 평가했더라도,
이러한 연구가 커뮤니티에 의해 모이고 결과를 비교하다보면,
결국 테스트 데이터에 오버피팅된 모델이 좋은 모델로 평가받게 됩니다.
이러한 이유로 벤치마크 데이터로부터 얻은 결과를
사용할 때는 매우 신중해야 하고,
약간의 성능 향상을 침소봉대하여 해석하는 것을 조심해야합니다.

## 5. 결과를 보고하는 방법

연구의 목표는 혼자 만족하는 것이 아니라,
세상의 지식에 기여하는 것입니다.
그러기 위해서는 전체 연구에 대한 청사진,
즉 여러분이 한 것과 하지 않은 것을 완전히 보여주어야 합니다.

대부분의 연구는 트레이드오프(trade-off)가 있습니다.
특정 모델이 다른 모델에 비해 모든 점에서 우수한 경우는 아주 드뭅니다.
그러므로 결과를 보고하고 결론을 제시할 때
어떤 점에서는 좋고, 어떤 점에서는 좋지 않은지
여러가지 요소들을 고려하여 투명하게 공개하여야 합니다.

### 5.1. 결과를 투명하게 공개하세요

결과에 대해 얘기할 때 가장 중요한 점은,
언제나 여러분이 한 것과 발견한 것에 대해 투명하게 알려야한다는 점입니다.
이는 다른 사람들이 여러분의 연구를 토대로 다른 연구를 하기 쉽게 만들어줍니다.

예를 들어, 여러분이 연구에 사용한 모델을 접근가능한 형태로 공개하는 것이 좋습니다.
여러분이 실험을 수행하기 위해 사용한 스크립트가 있다면,
결과를 공개할 때 그것을 함께 공개하세요.
이는 여러분의 연구 결과에 대한 신뢰성을 높여줄 것이고,
다른 연구자들이 모델을 비교할 때
여러분의 모델을 바닥부터 다시 구현하게 되는 수고도 덜어줄 것입니다.

또 여러분이 결과물을 공유하는 것을 전제로 하고 연구를 한다면,
모든 것에 더 조심스러워질 것입니다.
문서화도 더 열심히 할 것이고,
클린 코드를 작성하기 위해 노력하겠죠.
이는 여러분 자신에게도 도움이 되는 일입니다.

### 5.2. 여러가지 방법으로 성능을 측정하세요

모델을 엄격하게 평가하고 비교하기 위해서 사용되는 대표적인 방법은
여러 개의 데이터를 사용하는 것입니다.
이는 개별 데이터가 가지고 있는 한계점을 극복함으로써
모델의 일반화 성능을 평가하는 데에 도움을 줍니다.

각각의 데이터에 대해서도 여러 개의 평가 지표를 사용하면 더 좋습니다.
각각의 지표는 결과를 서로 다른 측면에서 해석할 수 있게 해주고,
이는 여러분의 연구의 투명성을 더해줄 것입니다.

예를 들어, 정확도 지표를 사용한다면,
클래스 불균형에 대해서 덜 민감한 지표를 추가로 사용하면 좋습니다.
혹은, 모델의 오류 정도를 측정할 때,
정밀도(precision), 재현율(recall)과 같은 부분적인 지표를 사용한다면,
오류에 대한 전체적인 정보를 알 수 있는 지표를 더해주면 좋습니다.

### 5.3. 데이터를 넘어선 일반화를 하지 마세요

연구에서 나온 결과를 바탕으로 잘못된 결론을 내지 않는 것도 중요합니다.
잘못된 결론은 여러분의 연구의 가치를 떨어트릴 뿐만 아니라,
다른 연구자들까지 길을 잃게 만들 수 있습니다.

이 부분에서 발생하는 대표적인 실수는
연구 과정에서 학습하고 평가한 데이터로부터는
얻을 수 없는 일반화된 결론을 내는 것입니다.
예를 들어, 모델이 한 데이터셋에 대해 좋은 성능을 보인다고 해도,
다른 데이터에 대해 좋은 성능을 보인다고는 말하지 못합니다.
여러 데이터 셋을 사용해서 검증한다면 더 단단한 결과를 얻을 수 있지만,
그래도 이것이 모든 경우에 대해 일반화된 결론이라고는 말할 수 없습니다.
데이터를 샘플링하는 과정에서 충분히 현실 세계를 반영하지 못했을 수도 있고,
서로 다른 데이터간에 겹침이 있을 수도 있습니다.
혹은 데이터의 퀄리티 자체가 떨어질 수도 있겠죠.

그러므로, 여러분의 결과를 확대해석해서는 안 됩니다.

## 결론

이 글이 머신러닝 연구를 갓 시작한 여러분이
알아야 할 모든 것을 알려주지는 않습니다.
일부 내용은 틀렸거나, 논쟁의 여지가 있기도 할 것입니다.

그러나 이것이 연구의 본질입니다.
많은 머신러닝 이론들은 실전에서 충분히 검증되지 않았고,
연구자들은 최선의 방법이 무엇인지 늘 논쟁합니다.
오늘 맞았던 것이 내일은 틀릴 수 있습니다.
그러므로 연구를 하는 여러분에게 바라는 것은 다음과 같습니다.

늘 열린 마음을 가지세요.
발전하는 최신 연구 내용을 따라잡으려고 노력하고,
여러분이 모르는 모든 것들을 받아들일 수 있는 겸손함을 가지세요.
