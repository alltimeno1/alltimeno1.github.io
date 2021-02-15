---
title: Cascade R-CNN
tags: 머신러닝/딥러닝
---

**기존의 Faster R-CNN에서 N개의 추가적인 classifier를 활용한 방식**

<img src="https://user-images.githubusercontent.com/71831714/107955487-3310dd00-6fe1-11eb-8f13-4dcb10e563ce.png" width="80%" height="80%">

<br>

Cascade R-CNN은 classifier가 만들어낸 Bounding Box를 받고 다음 classifier에서 분류 작업을 해서 새로운 Bounding Box를 만든다. 

<br>

이 작업을 여러 차례 반복하는데 BB의 정확도가 높아진다는 가정 하에 좀 더 높은 IoU를 기준으로 학습을 시키면서 성능을 극대화 함

<br>
