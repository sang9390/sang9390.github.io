---
date: 2021-11-04
title: "[Paper Review] CenterMask : Real-Time Anchor-Free Instance Segmentation (CVPR_2020)"
categories: [Paper_review]
---




#### Reference

+ paper: <https://openaccess.thecvf.com/content_CVPR_2020/papers/Lee_CenterMask_Real-Time_Anchor-Free_Instance_Segmentation_CVPR_2020_paper.pdf>





#### 1. Motivation  



최근 object detection task에 기반한 instance segmentation task는 높은 성능을 보이고 있다.

그 중 대표적인 모델은 Mask R-CNN이다.

Mask R-CNN기반의 instance segmentation task 모델은 inference speed를 높이는 연구가 많이 진행되었다.

이러한 inference speed를 높이는 연구중 real-time one-stage instance segmentation의 특징을 가지는 YOLACT model이 개발되었다.

그러나 YOLACR는 Mask R-CNN에 비하여 inference speed는 매우 빠르지만 정확도가 크게 떨어지는 모습을 보여주었다.

따라서 위 논문에서는 정확도와 속도간의 간극에 bridge 해주는 것에 초점을 두었다.



#### 2. Unique methology  

CenterMask에서 inference speed와 정확도를 높이는 key idea는 크게 세 가지이다. 

+ FCOS방법을 통한 anchor-free instance segmentation

  ![아키텍쳐](https://user-images.githubusercontent.com/76807432/140310553-2483ac32-3670-43f0-ada5-ddaf3987bddf.PNG)


  + FCOS 방법을 통해 anchor box 없이 bounding box를 predicts 할 수 있다.
  

+ spatial attention-guided mask(SAG-Mask) branch


  + FCOS 방법을 통해 추출된 bounding box마다 segmentation mask predicts
  + Mask R-CNN기반  

+ backbone 최적화(VoVNet)

  ![eSE](https://user-images.githubusercontent.com/76807432/140313601-3e7ce8e0-ba26-4eb2-966b-e1e43d2ef9da.PNG)

  + residual connection의 optimization problem을 크게 완화함
  + 기존 Squeeze-Excitation(SE)방법의 channel information loss problem을 완화함
  + 다양한 size의 backbone 모델을 만듬


#### 3. Results  

![fig_1](https://user-images.githubusercontent.com/76807432/140313392-c0d2f146-51ad-41cf-be3f-edb9349a777e.png)

![Tab_3](https://user-images.githubusercontent.com/76807432/140314708-9e173262-4a6b-4e60-9d77-6cb1b6aa6431.PNG)

![Tab_4](https://user-images.githubusercontent.com/76807432/140314729-041393c1-a5d6-4c67-a03b-e37ab5f8a9de.PNG)

![Tab_5](https://user-images.githubusercontent.com/76807432/140314750-1e5412e2-3214-47d6-872b-5e2cd9e308af.PNG)

![fig_4](https://user-images.githubusercontent.com/76807432/140314775-cd16a99e-88b2-400a-bdb9-6f1eec2eeaee.PNG)


Fig. 1: CenterMask모델과 다른 모델간의 AP/FPS 성능지표 비교 및 VoVNet backbone과 다른 backbone간의  AP/Inference time 성능지표 비교

Tab. 3: CenterMask 모델에 여러 backbone을 이용하여 Params, Time 및 AP score 수치 비교 

Tab. 4: 다양한 size의 VoVNet1에 residual, SE, eSE의 방법을 추가하며 수치 비교 

Tab. 5: CenterMask와 다양한 최신 모델간의 AP 성능지표 비교 

Fig. 4: CenterMask의 출력 이미지 



Mask R-CNN기반의 2-stage detector 이지만 1-stage detector 만큼의 inference speed를 보여줌 

효율적인 backbone 을 이용하여 resnet backbone보다 적은 parameters로 높은 AP 성능지표를 보임
