---
date: 2022-05-25
title: "[3분 SOTA Key Idea] VarifocalNet (CVPR 2021)"
categories: [3분 SOTA Key Idea]
comments: true
---




#### Reference

+ paper: <https://openaccess.thecvf.com/content/CVPR2021/papers/Zhang_VarifocalNet_An_IoU-Aware_Dense_Object_Detector_CVPR_2021_paper.pdf>





#### 1. Motivation  



dense object detector가 고성능을 달성하기 위해 요구되는 것 중 하나는 많은 양의 candidate detaction에 대한 정확한 ranking을 매기는 것이다.

prior work에서는 classification score 또는 combination of classification and predicted localization score를 통해 ranking을 매긴다.

그러나 두가지 option은 reliable할 수 있는 rank가 아니다. 따라서 detection 성능이 저하된다.

VarifocalNet에서는 이 부분을 해결하고자 한다.





#### 2. Unique methology  

VarifocalNet의 key idea는 크게 두 가지이다.

+ Iou Aware Classification Score

  ![01](https://user-images.githubusercontent.com/76807432/170201396-2d1a3767-f317-4f2c-b21b-d3510fd52afe.PNG)

  + IACS를 통해 object presence confidence와 localization accuracy에 대한 joint representation을 얻을 수 있음 
  + IACS를 통해 candidate detaction에 대한 보다 정확한 ranking을 얻을 수 있음
  + Varifocal loss를 통해 IACS를 예측하도록 dense object detector를 학습

+ star-shaped bounding box feature representation

  ![03](https://user-images.githubusercontent.com/76807432/170204889-eedc4ac2-f453-492a-9ef7-df5c7386f468.PNG)

  + IACS prediction및 bounding box refinement
  + 두가지 key idea를 통해 IoU-aware dense object detector(VarifocalNet)를 구축함



#### 3. Results  

![04](https://user-images.githubusercontent.com/76807432/170205874-4107c9c4-ae60-4a28-8f93-c13ed095482e.PNG)
![06](https://user-images.githubusercontent.com/76807432/170205892-962fbb4c-8a4a-4bb9-b407-8225416a7449.PNG)
![05](https://user-images.githubusercontent.com/76807432/170205910-18706951-b1d8-46f6-914e-ff4ae014aa36.PNG)

Table 3: VFL, Star Dconv및 BBox Refinement가 적용 되었을 경우에 대한 ablation study

Table 5: SOTA methods에 FL, GFL및 VFL가 적용 되었을 경우에 대한 ablation dtudy

Table 4: SOTA methods와 VFNet간의 AP score comparison(COCO test-dev)



candidate detaction에 대한 보다 정확한 ranking을 통해 큰 성능 향상을 이끌어냄(다양한 object detector에 적용 가능)
