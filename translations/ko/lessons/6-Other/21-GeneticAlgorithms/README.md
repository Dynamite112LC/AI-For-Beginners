# 유전 알고리즘

## [강의 전 퀴즈](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/121)

**유전 알고리즘** (GA)은 AI에 대한 **진화적 접근**에 기반하여, 인구의 진화 방법을 사용하여 주어진 문제에 대한 최적의 솔루션을 얻는 방법입니다. 이 개념은 1975년 [John Henry Holland](https://wikipedia.org/wiki/John_Henry_Holland)에 의해 제안되었습니다.

유전 알고리즘은 다음과 같은 아이디어에 기반합니다:

* 문제에 대한 유효한 솔루션은 **유전자**로 표현될 수 있습니다.
* **교차**는 두 개의 솔루션을 결합하여 새로운 유효한 솔루션을 얻을 수 있게 합니다.
* **선택**은 일부 **적합도 함수**를 사용하여 더 최적의 솔루션을 선택하는 데 사용됩니다.
* **돌연변이**는 최적화를 불안정하게 하여 지역 최소값에서 벗어날 수 있도록 도와줍니다.

유전 알고리즘을 구현하려면 다음이 필요합니다:

* **유전자** g∈Γ를 사용하여 문제 솔루션을 인코딩하는 방법을 찾아야 합니다.
* 유전자 집합 Γ에 대해 **적합도 함수** fit: Γ→**R**을 정의해야 합니다. 더 작은 함수 값은 더 나은 솔루션에 해당합니다.
* 두 개의 유전자를 결합하여 새로운 유효한 솔루션을 얻기 위해 **교차** 메커니즘 crossover: Γ<sup>2</sub>→Γ를 정의해야 합니다.
* **돌연변이** 메커니즘 mutate: Γ→Γ를 정의해야 합니다.

많은 경우, 교차와 돌연변이는 유전자를 숫자 시퀀스나 비트 벡터로 조작하는 간단한 알고리즘입니다.

유전 알고리즘의 구체적인 구현은 사례에 따라 다를 수 있지만, 전반적인 구조는 다음과 같습니다:

1. 초기 집단 G⊂Γ를 선택합니다.
2. 이 단계에서 수행될 작업 중 하나를 무작위로 선택합니다: 교차 또는 돌연변이
3. **교차**:
   * 무작위로 두 유전자 g<sub>1</sub>, g<sub>2</sub> ∈ G를 선택합니다.
   * 교차를 계산합니다: g=crossover(g<sub>1</sub>,g<sub>2</sub>)
   * 만약 fit(g)<fit(g<sub>1</sub>) 또는 fit(g)<fit(g<sub>2</sub>)라면 - 해당 유전자를 g로 대체합니다.
4. **돌연변이** - 무작위 유전자 g∈G를 선택하고 mutate(g)로 대체합니다.
5. 충분히 작은 적합도 값이 얻어질 때까지 또는 단계 수의 한계에 도달할 때까지 2단계부터 반복합니다.

## 일반적인 작업

유전 알고리즘으로 해결되는 일반적인 작업에는 다음이 포함됩니다:

1. 일정 최적화
2. 최적 포장
3. 최적 절단
4. 포괄적 검색 속도 향상

## ✍️ 연습문제: 유전 알고리즘

다음 노트북에서 학습을 계속하세요:

[이 노트북](../../../../../lessons/6-Other/21-GeneticAlgorithms/Genetic.ipynb)으로 가서 유전 알고리즘을 사용하는 두 가지 예제를 확인하세요:

1. 보물의 공정한 분배
2. 8 퀸 문제

## 결론

유전 알고리즘은 물류 및 검색 문제를 포함하여 많은 문제를 해결하는 데 사용됩니다. 이 분야는 심리학과 컴퓨터 과학의 주제를 통합한 연구에서 영감을 받았습니다.

## 🚀 도전

"유전 알고리즘은 구현이 간단하지만 그 동작을 이해하기는 어렵습니다." [출처](https://wikipedia.org/wiki/Genetic_algorithm) 스도쿠 퍼즐 해결과 같은 유전 알고리즘의 구현을 찾기 위해 연구하고, 그것이 어떻게 작동하는지 스케치 또는 흐름도로 설명하세요.

## [강의 후 퀴즈](https://red-field-0a6ddfd03.1.azurestaticapps.net/quiz/221)

## 복습 및 자기 학습

[이 훌륭한 비디오](https://www.youtube.com/watch?v=qv6UVOQ0F44)를 시청하여 컴퓨터가 유전 알고리즘으로 훈련된 신경망을 사용하여 슈퍼 마리오를 플레이하는 방법에 대해 이야기하는 내용을 확인하세요. 우리는 [다음 섹션](../22-DeepRL/README.md)에서 이러한 게임을 플레이하는 컴퓨터 학습에 대해 더 배울 것입니다.

## [과제: 디오판틴 방정식](../../../../../lessons/6-Other/21-GeneticAlgorithms/Diophantine.ipynb)

당신의 목표는 **디오판틴 방정식** - 정수 해를 가진 방정식을 해결하는 것입니다. 예를 들어, 방정식 a+2b+3c+4d=30을 고려해보세요. 이 방정식을 만족하는 정수 해를 찾아야 합니다.

*이 과제는 [이 포스트](https://habr.com/post/128704/)에서 영감을 받았습니다.*

힌트:

1. 해를 [0;30] 구간에 있다고 가정할 수 있습니다.
2. 유전자로서 해 값 목록을 사용하는 것을 고려해보세요.

[Diophantine.ipynb](../../../../../lessons/6-Other/21-GeneticAlgorithms/Diophantine.ipynb)를 시작점으로 사용하세요.

**면책 조항**:  
이 문서는 기계 기반 AI 번역 서비스를 사용하여 번역되었습니다. 정확성을 위해 노력하고 있지만, 자동 번역에는 오류나 부정확성이 포함될 수 있음을 유의해 주시기 바랍니다. 원본 문서는 해당 언어로 된 권위 있는 출처로 간주되어야 합니다. 중요한 정보에 대해서는 전문적인 인간 번역을 권장합니다. 이 번역 사용으로 인해 발생하는 오해나 잘못된 해석에 대해서는 저희가 책임지지 않습니다.