---
date: 2021-10-14
title: "[Paper Review] 객체 인식 정확도 개선을 위한 이미지 초해상도 기술 (한국정보통신학회논문지_2021)"
categories: [Paper_review]
---




#### Reference

+ paper: <https://www.koreascience.or.kr/article/JAKO202120164147479.pdf>





#### 1. Motivation  



객체 인식 과정에서 학습된 이미지 데이터와 테스트 이미지 테이터간 해상도 차이로 인해 객체인식 정확도가 감소하는 문제가 종종 발생한다. 

따라서 객체 인식 정확도 향상을 위한 객체 인식 및 초해상도 통합 프레임위크를 설계 및 개발하고자 함






#### 2. Unique methology  

객체 인식 정확도 개선을 위한 이미지 초해상도 기술의 key idea는 크게 두 가지이다. 

+ DBPN 기반의 SR framework

  ![sr_frame](https://user-images.githubusercontent.com/76807432/137300933-72f1a11c-9f40-4e80-a482-3c706703e0b9.PNG)

  + DBPN 방법을 기반으로 하며, 반복적인 upblock과 downblock을 거친다.
  + 회전, 원근변환, 크롭 등의 다양한 data augmentation 기법을 사용한다.
  

+ Flip loss 제안

  ![sr_loss](https://user-images.githubusercontent.com/76807432/137301602-2c3fc195-7988-429c-99bd-557b0906f368.PNG)

  + 좌우 반전시킨 LR 이미지를 입력으로 하여 flipped SR 이미지와 flip loss를 얻는다.
  + original SR 이미지를 통해 출력된 original loss와 flip loss를 합한 total loss를 제안. 



#### 3. Results  

![번호판_비교](https://user-images.githubusercontent.com/76807432/137303209-126c8c9b-cf59-4a62-9809-61b3c4e076e2.PNG)
![scale_4](https://user-images.githubusercontent.com/76807432/137303251-a38d7fe8-c776-424d-9a5b-bf70d1e0fd15.PNG)
![정량적 비교](https://user-images.githubusercontent.com/76807432/137303263-78e6e983-6874-4017-8fc0-d992fe722bbb.PNG)

Fig. 8: SR methods 별 SR 이미지 비교(scale factor = x4), 논문에서 제안한 모델의 SR 이미지가 보다 선명한 것을 볼 수 있다. 

Fig. 13: SR method 별 object detection 출력 이미지 비교, 논문에서 제안한 모델의 출력 이미지는 보다 객체 감지가 정확하게 이루어졌음을 확인 

Table. 3: SR method 별 PSNR 및 SSIM 성능지표 수치 비교, 논문에서 제안한 모델이 모든 scale에서 좋은 성능지표 수치를 보임 



SR 을 통하여 이미지의 품질을 향상시킬 경우 object detection task의 성능을 높히는데 유의미한 결과를 보임  

object detection 뿐만 아니라 다양한 task에서 활용 가능할 것으로 추측된다.
