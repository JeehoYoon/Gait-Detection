# Gait-Based re-identification
걸음걸이로 사람을 Re-identifiate 하는 프로젝트

# 목차
### 1. 프로젝트 소개 
### 2. GEI 생성
### 3. re-id network  
### 4. 정확도 분석
<br/>
<br/>
<br/><br/>

# 1. 프로젝트 소개    
두명의 얼굴이 잡힌 사진에서 각 얼굴을 인식하여, 감정분석 프로그램에서 두명의 감정수치를 추출한다.
두 명의 감정 수치와 그 사진에서의 관계를 바탕으로 직접 제작한 호감도 도출 함수에서 나온 호감도 수치를 DNN을 사용하여 학습시킨다. 
학습이 완료된 뒤에는 두명의 얼굴이 있는 영상 혹은 사진을 입력으로 받고, 각각의 감정 수치와 그에 따른 호감도를 도출해내는 프로그램이다.
<br/>
<br/>
          

# 2. GEI 생성
## GEI
-GEI(Gait Energy Image)는 기존에 소개했던 대로 Gait Recognition 분야에서 가장 일찍부터 사용되었고, 여전히 애용되는 기술. 최근에는 여러 variation도 등장
-연속된 실루엣 영상의 평균값으로 만든 이미지
-장점 : noise의 영향을 잘 받지 않아 데이터 전처리가 쉽고 학습 시 정확도가 높음        
<br/>
## Background-matting을 이용한 silhouette 생성
‘Background Matting: The World is Your Green Screen’논문 이용
자동으로 사람을 떼어내어 배경을 바꿔주는 시스템
이 논문을 이용하여 우리 실루엣을 생성하는데 응용
<br/>
<div> <center><img src="https://user-images.githubusercontent.com/48399897/80967601-99ad7b80-8e51-11ea-8b3c-1417f8fca4bd.jpg" width="50%" height="40%" title="BackMatting " alt="실행1"> </img></div>
<br/>
<br/>
## Mask R-CNN 이용
Mask R-CNN, Kaiming He, Georgia Gkioxari, Piotr Dollár, Ross Girshick, arXiv:1703.06870 [cs.CV]
널리 이용되고 있는 Object Detection 소스 중 하나
MS COCO 데이터셋으로 학습되었고, 81개 Class에 대해 Detection 가능.
기존 학습된 모델에 Detect 하고싶은 물체를 100여장정도 작은 데이터만 추가적으로 학습시키는 방식으로 원하는 대로 customizing 가능
<br/>
<div> <center><img src="https://user-images.githubusercontent.com/48399897/80967601-99ad7b80-8e51-11ea-8b3c-1417f8fca4bd.jpg" width="50%" height="40%" title="Maskrcnn " alt="실행1"> </img></div>
<br/>
<br/>

# 3. re-id network  
<div> <center><img src="https://user-images.githubusercontent.com/48399897/80967601-99ad7b80-8e51-11ea-8b3c-1417f8fca4bd.jpg" width="50%" height="40%" title="reidNet " alt="실행1"> </img></div>
<br/>
<br/>

# 4. 정확도 분석   

***1. 각도별 정확성***    
<div>
<img src="https://user-images.githubusercontent.com/48399897/80968716-679d1900-8e53-11ea-8c14-a6a6363f0988.png" width="60%" height="40%" title="matrix" alt="실행1">     </img>  
</div>    
</br>
</br>
***2. 실제 정확성***    
<div>
<img src="https://user-images.githubusercontent.com/48399897/80968716-679d1900-8e53-11ea-8c14-a6a6363f0988.png" width="60%" height="40%" title="" alt="실행1">     </img>  
</div>    
</br>
</br>


