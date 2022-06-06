## PCA란
* PCA는 차원 축소 방법 중 하나
* 가장 정보를 많이 담는 축을 구한다.
* 그 축과 수직이면서 그 다음으로 정보를 많이 담는 축을 구한ㄷ.
* 위 과정을 반족

## PCA 구하는 법
1. X를 센터링한다. (평균을 0으로 만듬, 각 열의 평균만큼 뺌)
2. SVD 분해 진행 -> X = USV^T
 - Z = US : 주성분 점수 (PC score)
 - V 열벡터 : 주축
3. S의 대각선의 값이 (s1,s2,,,,sn)이라고 할 때 si^2/n이 i 번째 PC의 분산 => eigen value가 크다 = 분산이 크다


## SVD 구하는 법


* U, V가 직교행렬(orthogonal matrix)이라 함은 UU^T = VV^T = E, U^-1=U^T, V^-1=V^T
 
* U의 열벡터(ui): left singular vectors of A (AA^T의 eigenvector)
* V의 열벡터(vi): right singular vectors of A (A^TA의 eigenvector)
