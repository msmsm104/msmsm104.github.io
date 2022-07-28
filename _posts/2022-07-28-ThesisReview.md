# 2022-07-28-ThesisReview.md

---
layout: post
title: Sequence to Sequence Learning with Neural Networks
---

# ![face](/images/face.jpeg)


Abstract

 - general한 end to end 접근을 제시.
 - Encoder 와 Decoder에 서로 다른 LSTM(MultiLayerd = 4)model을 사용.  - 영어를 불어로 번역하는 task에서 ‘BLEU’ score 34.8 <사용된 Dataset ‘WMT’14>
 - SMT(통계기반전통적인 기계번역)을 사용했을때는 BLEU score 33.3 과 비교했을때 더 높은 성능을 보여준다.
 - 입력문장의 순서를 바꿔주는것이 경험적으로 성능을 향상시킨다 (학습의 난이도를 낮춘다고 말하고 있다.)

Introduction

 - 해당 논문이 나온 시점, 딥러닝 모델의 경우 입력과 출력의 차원이 동일하게 고정되어있다. 이와같은 특성을 speech recognition, machine translation등 sequential한 문제를 해결함에 있어 문제점이된다.

 - 이와같은 문제점을 해결하기 위해 본 논문에서는 LSTM만으로 Sequence to Sequence문제를 잘 해결할 수 있다고 주장하고 있다. (Encoding(LSTM)을 통해 큰 크기의 고정된 차원의 context vector를 뽑은 후 Decoder(Another LSTM)를 통해 output sequence를 뽑아내는 방법.)


The model

 - 기존의 RNN model같은경우 입력과 출력의 길이가 다른 경우 사용하기 어렵다. 또 한 Long Term dependencies를 처리하기 어렵다. -> LSTM을 사용

 - Encoder part, Decoder part 사용되는 각각의 LSTM은 서로 다른 parameters를 가진다.
 - LSTM의 layer를 4개 쌓음으로써 모델의 capacity 증가시킴(너무 깊게 쌓게되면 비용이 증가.)


Training

 - mini-batch를 사용하여 학습을 진행(한 mini-batch에 들어가는 문장들의 길이를 최대한 비슷하게 구성함으로서 불필요한 padding을 최소화 -> 학습속도 향상)



Conclusion
 => 해당 논문이 나온 시점, 딥러닝 모델의 경우 입력과 출력의 차원이 동일하게 고정되어있다. 이와같은 특성을 speech recognition, machine translation등 sequential한 문제(입력과 출력의 길이가 다른)를 해결함에 있어 문제점이된다. 이를 해결하기 위해 본 논문에서는 Encoder(LSTM [mutilayer=4])를 통해 고정된 차원의 context vector를 뽑아내고 그 후 Decoder(LSTM [mutilayer=4])를 통해 context vector를 원하는 길이의 output sequence로 뽑아냄. 이러한 과정을 통해 기존에 입력과 출력의 길이가 다른 문제를 (기존의 모델과 비슷한 수준으로) 해결할 수 있고 또한 Encoder와 Decoder에 LSTM을 사용함으로써 입력 sequence의 길이가 긴 경우에도 잘 작동함을 해당 논문에서 보여준다.
