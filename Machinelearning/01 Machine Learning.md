# Machine Learning
가장 정확하게 예측할 수 있는, 최적의 parameter를 찾는 작업  
처음에는 임의의값 -> 성능 개선 -> 최적

## 목표
Train Set에 없는 새로운 sample에 대한 error를 최소화  

Test set에 대한 높은 성능을 generalization이라 한다.

> [Def] Feature space : 특징공간  
> 데이터가 존재하는 공간 (x공간)

> [Def] bias와 분산  
> Overfitting & underfitting
비선형 예측함수
- 2차 -> bias 높음, but 비슷한 모델 -> 분산 낮음  
- 12차 -> bias 낮음, but 크게 다른 모델 -> 분산이 높음

즉, bias와 분산은 trade off 관계  
> [목표]
 낮은 bias, 낮은 분산을 가진 예측기 제작 (왼쪽 아래)  
> <img src = img/01/img1.png>  
> bias와 분산은 trade off 이므로, bias희생을 최소로 유지하며 분산을 최대로 낮춤

## 평가 방법
1. Cross validation
<img src = img/01/img2.png>  

    model = {m1, m2, m3, m4 ..... mk} -> k개의 모델  
    Dataset : {x1,x2,x3...... x1000} -> 1000개의 데이터

    (1) Dataset을 k 등분을 한다.  
    ex) k == 10 이면, {x1...x100},{x101...x200},...{x901...x1000} : 10등분

    (2) i번째 데이터를 validation set 나머지 9개를 train set으로 하면 1개의 모델 당, k개(10개) 의 accuracy가 나옴.

    (3) 이를 평균내어 각각의 model의 accuracy를 계산하여 가장 성능이 좋은 모델을 택하거나, 각 모델 성능의 평균을 내거나 등의 방법을 사용할 수 있음.

2. Boot Strap

    0 < p <= 1 인 p를 정하여 확률적으로 sampling을 하고 p만큼 validation set으로 나머지 1-p만큼을 train set으로 하여 T번 반복하여 모델을 학습시켜 accuracy를 구하는 방법.

## 현실적인 model 선택 방법
1. 용량이 충분히 큰 모델을 선택한다.
2. 정상을 벗어나지 않도록 regularization 기법을 적용한다.

> __Regularization__  
> 1. Data 확대  
> 데이터를 더 많이 수집하면 일반화 능력이 향상됨
> 데이터 수집은 사람이 일일이 레이블링 해야 하므로 비용이 커짐  
> 인위적 데이터 확대 : 훈련집합에 있는 샘플을 변형(Augmentation), 약간 회전 하거나 와핑을 함, 이 때, class(정답 레이블)가 변하지 않도록 주의해야함.  
> 2. 가중치 감쇠  
> 이에 대한 자료는 많으므로 찾아볼 것.


