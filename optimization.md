# optimization 정리

![image](https://user-images.githubusercontent.com/63588046/167973790-e5e397e7-7efd-4f07-8666-0dc407f6ec57.png)

## 참고점
* 어느정도 성능이 수렴하면 학습속도 낮추는 것이 좋음
* 모든 지점에서 기울기가 0인 지점이 발생하기 어렵다. (차원수가 많기 때문에 모든차원 0인지점 거의 없음, 즉 saddle point에서 빠지는 것을 주의!!)
* Hessian 행렬(2차 미분)을 사용하면 saddle point에 빠지지 않을 수 있음... 그러나 미분을 구하는 것이 훨씬 복잡
* Lipschitz Assumption : 입력에 작은 변화를 주면 출력에 작은 변화를 가짐 -> 훈련하다가 성능이 나빠지면 곧 좋아짐



## GD (Gradient Descent)
![image](https://user-images.githubusercontent.com/63588046/167973829-73ee71b9-c12d-492f-89b2-eb811e4a37cd.png)

#### Batch Gradient Descent
* 파라미터 업데이트를 위해 데이터 전체를 계산에 이용하는 것
* 속도가 느림

#### Stochastic Gradient Descent
* 하나의 훈련데이터만 계산에 이용
* 속도가 빠름
* 일정하지 않은 gradient로 파라미터를 업데이트하는 것은 수렴을 방해할 수 있다
* 최종 수렴에는 batch size가 큰 것이 전체를 보기때문에 더 성능이 좋을 수 있음
* SGD에서 기울기는 여러개에서 얻은 기울기의 평균을 사용함



## Momentum

![image](https://user-images.githubusercontent.com/63588046/167974116-5da62090-cb67-4e96-8a7a-1fbb3e7ec78d.png)

* 파라미터 업데이트시 local minimum에 빠질 수 있게 된다
* 이전 gradient들도 계산에 포함해서 업데이트 한다. (이전에 이동한 양에 일부만큼 더 이동)

![image](https://user-images.githubusercontent.com/63588046/167974607-553fb0db-e390-446f-b801-d2a8bd0df1d3.png)


## Adagrad

![image](https://user-images.githubusercontent.com/63588046/167976918-1f6a0d97-e9e8-4240-b035-aebfadd818f3.png)

* 학습을 할때마다 계속 기울기를 더한다.
* 제곱을 더하므로 계속 커진다
* 학습을 많이 하면 h가 지속적으로 계속 커질것이다.


## RMSProp

![image](https://user-images.githubusercontent.com/63588046/167995685-57aec0d1-792c-4c06-946a-93896e99e672.png)

* 무작정 h값이 커지는 방식이 아닌 일부를 줄이면서 더함

## Adam

![image](https://user-images.githubusercontent.com/63588046/167995805-733fb522-e615-4ca9-857b-0864cf7ce325.png)

![image](https://user-images.githubusercontent.com/63588046/167995853-41f98c68-6742-430a-9c75-eb390dfceadf.png)

