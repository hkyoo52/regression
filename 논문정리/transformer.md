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

#### Position Encoding
* 위치를 표현함
* 학습하지 X (값이 매우 크므로 만약 requires_grad = True로 할 시 학습이 position encoding에 취중)
* 512차원
* word embedding의 cos 유사도 > position embedding의 cos 유사도

![image](https://user-images.githubusercontent.com/63588046/164379495-c65c3f99-ed45-4f77-9817-169f5ae74dba.png)


#### encoder 입력값
* 입력 값 = word embedding + position embedding  <= 이런식으로 하면 word embedding이 너무 작음...
* word embedding = word embedding * math.sqrt(d)로 바꿈 (word_embedding 가중치 곱함)

```python
for i in range(1,512,2):
  p0[0][i] = math.sin(pos/(10000**((2*i)/d_model))))
  pc[0][i] = (y[0][i] * math.sqrt(d_model))+p0[0][i]
```

(https://colab.research.google.com/github/d2l-ai/d2l-en-colab/blob/master/chapter_attention-mechanisms/self-attention-and-positional-encoding.ipynb)   <- 코드 참조

#### multi head attention
* 512 차원은 계산하려면 너무 많은 시간이 걸림
* 8개의 64차원으로 바꿔서 계산 (**8개의 서로 다른 부분 공간**을 얻어서 학습)

* Ex. 단어의 수가 3개, 단어 차원 512
* Q,K,V : (3 * 512) * (512 * 64) = 3 * 64
* attention : somftmax(3 * 64) = 3 * 64
* sum of attention : 1 * 64 ?????
* 이 과정을 8번을 진행 : 3 * 64 8개 만듬
* concat -> 3*512

![image](https://user-images.githubusercontent.com/63588046/164510272-107db9bc-2551-4901-a5e1-6d2e6bd0b661.png)

![image](https://user-images.githubusercontent.com/63588046/164585231-a70afcf0-7227-433e-9c08-6b0be5f856cb.png)




## skip-gram ??
* word(i)를 학습하려면 word(i-2),word(i-1),word(i+1),word(i+2) 분석


## 궁금증
attention 결과값을 왜 더하지??
1개의 attention은 그 단어가 다른 단어와의 관계가 있는 것인 그것을 더하면 정보 손실이 될듯 
