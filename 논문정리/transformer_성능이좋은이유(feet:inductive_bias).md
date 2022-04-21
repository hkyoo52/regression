## Inductive bias
* 사람의 개입이 들어감
* Ex. CNN : 이미지는 주변 픽셀로 판단 가능하다.
* Ex. RNN : 이후의 데이터는 과거 정보를 가지고 예측할 수 있다.

## transformer 성능이 좋은 이유
* inductive bias를 줄일 수 있다.
* 사실 글자가 바로 이전 정보에 많은 영향을 받지 않음
* 이미지도 멀리 떨어진 곳에 정보가 더 중요할 수도 있음
* 만약 데이터가 아주 충분히 많고 다양하다면 가장 기초적은 mlp가 더 성능이 좋을 수도 있음
* transformer는 inductive bias를 감소시키면서 학습속도도 빠르게 해 준 기술임

## Google의 증명 -> VIT
* google은 엄청나게 많은 데이터셋을 가지고 transformer를 진행함
* 학습할때 각 위치의 positioning encoding도 학습 가능하게 했더니 인접한 위치가 잘 학습한다고 말함
* 멀리 떨어진 것도 연관성이 존재하는데 떨어진다고 말함
* 즉 inductive bias를 감소시켰는데 성능이 더 좋다고 함
* 근데 이런 성능이 나올려면 **데이터셋이 충분히 많아**야함
