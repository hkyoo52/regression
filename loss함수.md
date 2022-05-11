* MSE : 오차의 제곱의 평균
* MAE : 오차의 절대값의 평균
* RMSE : MSE^(1/2)

![image](https://user-images.githubusercontent.com/63588046/166140489-fe228db6-1bbb-447d-a329-2eef0072d7c2.png)

### MSLE (Mean Squared Log Error)
* MSE에 log 적용 
* log(y)가 아닌 log(y+1)을 적용 (y=0일때 -무한이 되는 것을 보정하기 위해서)

![image](https://user-images.githubusercontent.com/63588046/167776486-a4f2476c-59fe-41d1-9a24-7bc8a4ca0683.png)

### RMSLE (Root Mean Squared Log Error)
* RMSE에 로그 적용

![image](https://user-images.githubusercontent.com/63588046/167776563-d2c947f9-d855-4362-acee-21c778840ed4.png)

### R² (R Square)
* 분산 기반 예측 성능 평가
* 1에 가까울수록 정확도 높음
* R² = 예측값 Variance / 실제값 Variance

## 특징
* MSE 
    * 이상치가 있을 경우 크게 반응을 한다
    * 학습이 불안해질 가능성 높다
    * 미분이 가능하다
* MAE 
    * 이상치에 robust
    * 모든 오차에 동일한 가중치
* RMSE 
    * MSE보다는 이상치에 덜 반응한다.

### RMSE와 비교해서 RMSLE가 가진 장점
1. 아웃라이어에 강건하다
   * 예측값 = 67, 78, 91, 실제값 = 60, 80, 90일 때, RMSE = 4.242, RMSLE = 0.6466입니다.
   * 예측값 = 67, 78, 91, 102, 실제값 = 60, 80, 90, 750일 때 RMSE = 374.724, RMSLE = 1.160입니다.
2. 상대적 Error를 측정해준다.
   * 예측값 = 100, 실제값 = 90일 때, RMSLE = 0.1053, RMSE = 10입니다.
   * 예측값 = 10,000, 실제값 = 9,000일 때, RMSLE = 0.1053, RMSE = 1,000입니다.
   * 즉 상대적인 크기가 동일하면 동일한 값이 나옴!!
3. Under Estimation에 큰 패널티 부여
   * 예측값이 실제보다 더 클때보다 예측값이 실제보다 더 작을때 더 큰 패널티 부여
   * 예측값 = 600, 실제값 = 1,000일 때 RMSE = 400, RMSLE = 0.510입니다.
   * 예측값 = 1,400, 실제값 = 1,000일 때 RMSE = 400, RMSLE = 0.33입니다.
