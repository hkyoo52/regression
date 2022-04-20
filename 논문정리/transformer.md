## 이전 회귀 모델
* Markov chain
* 시퀀스 마지막 요소로 다음 요소 예측
* RNN
* CNN – 장기 종속성 문제
* Attention – 마지막 토큰이 아니라 다른 토근들도 보는 것

# transformer
* 이전 모델은 단어와 단어 사이의 길이가 길어지면 recurrence(순환) 발생
* Attention으로 대체 -> 연산량 감소


#### attention
* 단어 벡터간에 내적 실행 -> 단어들중에 가장 강한 관계 결정

#### multi-head attention
* 시퀀스에 대한 보다 광범위하고 철저한 분석   -> ??
* recurrence 배제에 따른 연산 축소
* 병렬화 구현 -> 훈련 시간 축소
* 각 어텐션 메커니즘이 같은 입력 시퀀스에 대해 서로 다른 관점 학습   -> ??


## Encoder
* multi-head attention, feed forward 2개 존재
* residual skipping 사용 -> positioning ecoding의 정보가 중간의 손실되지 않게 하려고

#### 입력 임베딩
* tokenizer 진행(단어를 토큰화로 만듬) (소문자로) -> 
* embedding : skip-gram 방식으로 진행 (입력 토큰을 512차원으로 만듬)
* 코사인 유사도로 embedding된 것들끼리 유사도 구할 수 있음

//9쪽 진행중








## skip-gram ??
* word(i)를 학습하려면 word(i-2),word(i-1),word(i+1),word(i+2) 분석
