## Title  
- Can Machines Generate Personalized Music? A Hybrid Favorite-aware Method for User Preference Music Transfer    
  
<br/>

## Problem Definition  
- 대부분의 음악 스타일 변환은 데이터 기반 방법에 의존하여 사용자가 좋아하는 노래를 충분히 제공할 수 없음  
- 해당 문제를 해결하기 위해 사용자가 가장 좋아하는 음악 중 한 곡에 대한 사전 지식만 사용하는 사용자 선호도 트랜스포머(UP-Transformer) 방법 제안  
- 사용자가 가장 좋아하는 음악에서 추출된 음악 패턴을 기반으로 사용자 선호 음악 변환(UPMT)을 달성  
- 사용자 선호도에 맞게 치료 음악을 제공하면 증상을 완화하는데 더 효과적인 치료로 이러질 수 있음    

  
<br/>

## Motivation  
- VAE 및 GAN 기반 모델은 학습을 위해 많은 수의 데이터 샘플을 필요로 하기에 본 학습에 적절하지 않음  
- MIDI에 비해 REMI는 순서에 따라 다른 이벤트를 명시적으로 정의  
  - 템포 변경 및 코드 정보와 같은 더 많은 정보를 포함     
  
<br/>

## Method  
- 사전 학습된 Transformer-XL 모델을 베이스로 채택하여 선호도 인식 손실 함수 사용  
  
<br/>

## Experiment setup  
- **Dataset**  
  - 가장 좋아하는 음악 샘플은 피험자가 오픈소스에서 다운로드하여 제공  
  - 악기 연주 훈련을 받고 기초 음악 이론에 익숙한 23명의 피험자 모집하였으며, 음악 간의 중복으로 인해 19개의 가장 좋아하는 음악 포함  
  - 7개 장르(클래식, 재즈, 팝, 록, 포크, 뉴에이지, 라이트 음악)  
  - 음악 한 곡을 128개의 토큰 길이로 나눔  
  - 손실 함수의 경우 α = 0.01로 설정  
  
- **Evaluation Metrics**  
  - 다양한 논문에서 많은 평가 지표가 제안되었지만 음악 스타일 변환에서 여전히 미해결 문제로 남아 있음  
  - 해당 연구에서는 네 가지 지표를 활용한 모델 평가 제안  
    - 피치 클래스  
    - 주 분포  
    - Duration : 32개의 클래스로 양자화하고 클래스의 분포를 계산  
    - IOI(Inter-Onset Interval) : 두 노트 온셋 사이의 간격을 측정  
    - 네 가지 요소 분포의 평균 중첩 면적(OA)을 계산하여 두 음악 작품 간의 유사성을 측정  
    - 멜로디 정보가 아닌 음악 이벤트 정보만을 통해 유사성 평가  
- **청취 테스트**   
  - 원래 입력된 음악 한 곡과 그들이 가장 좋아하는 음악 한 곡 제공  
  - PopMT, PopMAG, CycleGAN, TTM 및 UP-Transformer에 의해 변환된 다섯 곡의 음악 제공하여 5점 척도를 통한 비교 평가 진행  
    - 음악성  
    - 유사성 : 좋아하는 음악과 얼마나 유사한지  
    - 선호도 : 얼마나 좋은지  

  
<br/>

## Result  
- 음악의 시퀀스 길이가 너무 길면 수렴 속도가 낮고, 너무 짧으면 모델 성능이 별로 좋지 않음  
  - 시퀀스 길이가 64 또는 128인 모델만 좋은 결과 보여줌   

<br/>

## Conclusion  
- 음악의 다양성을 높이고 사용자의 선호도에 맞게 더 많은 음악 변환 가능성을 탐색하기 위해 가사와 연주와 같은 다른 음악 특징을 고려할 예정  
- 모델 성능을 향상시키기 위해 두 단계(멜로디 간격, 고조파 간격)에 걸쳐 다른 음악 이론 적용 가능  
- 모델 효율성을 높이기 위해 모든 사용자의 선호도에 맞는 모델 도입하여 미세 조정 시간을 줄일 수 있음  
- 위와 같은 연구 방향에 초점을 맞춰 앞으로 연구 진행할 것  

<br/>

## Author Information  
- Zhejing Hu, Yan Liu, Gong Chen, Yongxu Liu  

<br/>

## [Github Implementation](https://github.com/hu-music/UPMT)  
