---
title: Faster R-CNN
tags: 머신러닝/딥러닝

---

**현재 진행중인 가구 추천 프로젝트에서 객체 탐지에 사용한 Faster R-CNN에 대한 정리 글**

<br>

**R-CNN**
- CNN과 비슷하지만 Region이라는 개념이 추가된 방식

<img src="https://user-images.githubusercontent.com/71831714/107040802-12879c80-6803-11eb-8d65-cb649c5c20e5.png" width="60%" height="60%">

<br>

1. Region Proposal
   - 이미지에서 물체가 있을법한 위치를 2000개쯤 찾는다.
2. Feature Extraction
   - 위에서 찾아낸 박스들을 동일한 크기로 리사이즈하고 CNN 모델을 통과하여 특징 벡터를 추출한다.
3. Classification
   - 추출된 벡터를 클래스 별로 SVM Classifier를 학습시킨다.
4. Non-Maximum Suppression
   - IoU가 0.5보다 크면 동일한 물체로 판단하고 가장 스코어가 높은 박스만 제외하고 삭제한다.
5. Bounding Box Regression
   - region proposal ![P](https://s0.wp.com/latex.php?latex=P&bg=ffffff&fg=000000&s=0&c=20201002) 와 정답 위치 ![G](https://s0.wp.com/latex.php?latex=G&bg=ffffff&fg=000000&s=0&c=20201002)가 존재할 때, ![P](https://s0.wp.com/latex.php?latex=P&bg=ffffff&fg=000000&s=0&c=20201002)를 ![G](https://s0.wp.com/latex.php?latex=G&bg=ffffff&fg=000000&s=0&c=20201002)로 교정한다.

<br>
<br>

**Fast R-CNN**

<img src="https://user-images.githubusercontent.com/71831714/107045176-91330880-6808-11eb-835a-12694b30ea78.png" width="60%" height="60%">

<br>

**R-CNN 모델의 단점인 속도를 대폭 개선한 모델**

<br>

<img src="https://user-images.githubusercontent.com/71831714/107045181-91cb9f00-6808-11eb-8ffa-c6d2a061bef9.png" width="60%" height="60%">

<br>

Fast R-CNN에서는 Region Proposal과 Feature Extraction 과정을 image level이 아닌 Feature map level에서 수행하여 CNN 연산량을 크게 줄임

<br>
<br>

**Faster R-CNN**

<img src="https://user-images.githubusercontent.com/71831714/107048115-eae90200-680b-11eb-8f86-a6aa72f0078e.png" width="30%" height="30%">

<br>

Fast R-CNN에서는 CNN 외부의 알고리즘을 통해 수행했던 Region Proposal을 Faster R-CNN에서는 CNN 내부에 Region Proposal Network를 통해 수행하여 정확도와 속도가 향상됨

<br>
<br>

**프로젝트로 돌아가서..**

- Faster R- CNN은 YOLO나 MobileNet보다는 속도가 느리지만 정확도 면에서는 뛰어난 모델이다.
- 영상이 아닌 이미지 작업을 하고 있고 MobileNet을 사용할 환경도 아니고 최초 모델링은 Faster R-CNN으로 진행하는 중

<br>
