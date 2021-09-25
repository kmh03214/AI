# DNN

<a href = 'http://taewan.kim/post/nn_notation/'> DNN 참고링크 </a>  
<a href = 'http://taewan.kim/post/error_in_hidden/'> 오차계산 참고 </a>
- DNN은 히든레이어가 1개 이상인, Neural Network

- 다음 식을 따른다.

    Z = Wx + b  
    x' = activation(Z) = activation(Wx + b)

    > Where, W(k)행렬의 하나의 원소 W(k,j,i) => k번째 레이어에서 j번쨰 노드와 곱해져 k+1번째 레이어의 i로 가는 가중치  
    > activation은 활성화함수 (ex : sigmoid / relu / tanh ...)  



- 기존 NN에서 Hidden Layer가 많아지면서, 파라미터가 증가하고 표현할 수 있는 구분선이 많아지면서 성능이 올라감
- Backpropagation을 통해 오차가 계산되어 W가 업데이트 되는데, Gradient Vanishing 문제를 해결하면 (relu) 깊게 쌓을 수 있음


# CNN

<a href = 'https://umbum.tistory.com/223'> CNN 참고링크 </a>  

## 특징
- convolution 연산을 사용하는 Neural Network
- convolution을 사용하면 3차원 데이터의 공간적 정보를 유지한 채 다음 레이어로 전달 가능
- 대표적 CNN은 LeNet(1998) / AlexNet (2012)이 있다.
- VGG, GoogleNet, ResNet 등은 층을 더 깊게 쌓은 CNN기반 NN이다.

## CNN의 네트워크 구조
이전 계층의 모든 뉴런과 결합된 형태의 Layer를 fully-connected layer(FC layer / Dense layer)라고 한다.  

CNN에서는 FC(Dense) 대신 다음 두 레이어를 활성화 함수 앞 뒤에 배치한다.
- Convolution layer
- Pooling layer

마지막 출력층에서는 FC - activation(Softmax / uniform) 그대로 간다.

결과적으로는
Conv - Conv - Pooling ... 반복 ...(Fatten) - FC - FC ...반복... - Softmax (Pooling layer는 생략하기도 한다.)

## FC layer의 문제점
1차원 데이터만 입력 받을 수 있기 때문에, 3차원 데이터를 평탄화해서 입력해야 한다.
즉, 3차원 공간상의 구조적 정보를 잃어버린다는 문제가 있다.

> Conv layer는 형상을 유지한다. 

## Convolution layer
<a href = 'https://brunch.co.kr/@chris-song/24'> Convolution 연산 이해 </a>

Convolution은 "두 함수 중 하나를 반전(reverse)하고 이동(shift)시켜가며 다른 하나의 함수와 곱한 결과를 적분해 나간다." 는 뜻이다.


## CNN에서 학습되는 Weight

CNN연산을 하기 위해 필터가 사용되는데, conv layer에서는 이 필터가 weight이며 필터의 값들이 학습되는 것이다.

따라서, 필터의 값을 무작위로 초기화 시킨 후 학습하게 되면, 각 필터들은 학습되어 여러가지 특징(feature)들을 추출하는 필터로 학습(수렴) 된다.

AlexNet의 각 층의 필터를 예로 들면
- 1번째 Conv layer에서는 Edge / Blob을 잡는 필터
- 3번째 Conv layer에서는 texture
- 5번째 Conv layer에서는 Object Parts
- 8번째 FC layer에서는 Object Classes를 잡아낸다.

layer를 거듭할 수록 더 추상적인 정보를 잡아낸다.
즉, 뉴런이 반응하는 대상이 단순한 패턴에서 사물의 의미를 나타내는 고급정보로 변환한다.
층을 깊게 쌓을 수록 더 추상적인 정보를 추출할 수 있다.