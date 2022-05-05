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


# He




# 궁금증
* 왜 weight값이 일정하면 표현력이 작아질까?
