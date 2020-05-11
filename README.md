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
Re-id (사람 재식별) 기술은 cctv 영상을 이용해 보행자의 통행량이나 이동경로를 분석할 수 있고 위험지역에 진입하는 보행자에게 경고를 주는 등 한 대의 카메라에서 검출된 특정 보행자가 같은 카메라의 다른 시간대에 다시 나타났는지, 또는 주변 다른 카메라에서 어느 시간에 포착되었는지를 찾는 기술이다. 여기에 걸음걸이 인식을 사용하여 재식별을 한다면 사람의 얼굴이 잘 파악이 되지 않는 상태에서도 범인 추적, 재식별, 인식 등의 성능을 높일 수 있을 것으로 기대한다. 따라서 이 프로젝트에서는 걸음걸이 정보를 이용하여 사람을 재식별하는 것을 목표로 한다.
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


