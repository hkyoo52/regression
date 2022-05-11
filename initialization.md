# 표준편차가 너무 큰 경우
* activation이 sigmoid나 tanh이면 weight 값이 클경우 미분값이 거의 0에 수렴한다.
* 학습이 거의 되지 않는다.

![image](https://user-images.githubusercontent.com/63588046/166856702-96861ad3-d428-4a33-aa1b-53e96e4da144.png)


# 표준편차가 너무 작고 평균이 0 인 경우
* activation이 tanh일 경우 층이 깊어지면 0에 수렴해질것이다.
* 이렇게 될 경우 weight의 표현력이 매우 저하될 것이다.


# 모든 이미지에 해당하는 Wx 값이 음수가 될 경우
* optimizer가 GD or SGD이고 activation이 relu일 경우 그것에 해당하는 weight는 절대 학습이 되지 않는다.



# Xavier
![image](https://user-images.githubusercontent.com/63588046/167756926-1a161083-4fee-40c5-b539-3e3de56e453f.png)

* sigmoid, tanh에 효과적인 결과를 보여준다. 
* 다만 relu 사용시 0으로 수렴하게 된다.

# He

![image](https://user-images.githubusercontent.com/63588046/167757456-566948d9-c95e-4068-a144-82311508a100.png)

* relu에서 사용한다.

# 궁금증
* 왜 weight값이 일정하면 표현력이 작아질까?

## 왜 입력 값이 작으면 더 큰 가중치를 줄려고 할까?
* 더 적은 개수의 값으로 표현을 하기 위해서는 각각의 노드에서 나온 값이 커야하므로 더 큰 가중치를 줘야 한다.

## 왜 Xavier는 relu 가 안좋을까?
* relu는 출력에 절반이 학습이 되지 않는다. 그래서 더 적은 값으로 같은 효과를 내려면 값이 2배정도 더 커야한다.

## 균등분포 U
* U(a,b)는 a부터 b까지 분포가 존재하며 그 값이 동일하다.

![image](https://user-images.githubusercontent.com/63588046/167757741-be199071-5d70-4644-b68d-cdf331ef2e11.png)
