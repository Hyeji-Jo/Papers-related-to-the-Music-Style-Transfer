## Title  
- Music Style Transfer with Vocals Based on CycleGAN  
  

## Problem Definition  
- 최근에 뉴럴 스타일 변환은 이미지 응용 분야에서 주요한 역할을 하지만 음악 스타일 변환 분야에서는 약함  
- 대부분의 연구가 이미지 스타일 변환 알고리즘을 음악 스타일 변환에 적용하였으며, 보컬이 있는 대중음악에서의 결과는 만족스럽지 못함  
- CycleGAN을 통한 음색을 변환해 장르 변환하여 WaveNet을 통한 소리 출력 등의 과거 연구를 볼 수 있지만 보컬과 배경음악이 변환되는 것은 없음  


## Motivation  
- 음악은 시간을 기반으로 하며 많은 구성 요소로 이루어져 있기에 특징 추출이 복잡  
- 음성의 CQT 특징과 Mel spectrogram을 추출하고 CycleGAN을 활용해 스타일 변환 수행  
  - CQT(Constant Q Transform) : 서로 다른 주파수 대역들 사이의 기하학적 분해를 고려하며, 인간 귀의 특성을 반영  
- 그 후 WaveNet 디코더를 통해 고품질의 보컬이 있는 음악으로 구현할 계획  
   

## Method  
**1. CycleGAN**   
  - 2개의 생성기와 2개의 판별기를 포함하고 있는 비지도 생성형 네트워크  
  - 페어링 된 데이터 없이 두 도메인 간 매핑을 학습할 수 있음  
  - 생성기는 노이즈를 입력으로 받지 않고 도메인 샘플을 입력받음  
  - Zhu et al.이 제안한 동일성 손실 함수와 cycle consistency loss 사용  
  - 본 논문에서는 비선형 attenuation 모델을 사용하여 견고한 모델 생성
  - Deconvolution 대신 이웃 보간법과 일반 컨볼루션 사용
  
**2. CQT**  
  - 낮은 주파수 영역에서는 좁은 대역폭을 가지고, 높은 주파수의 영역에서는 넓은 대역폭을 가짐  
  - 인간은 낮은 주파수 영역의 소리에 더 민감하기에 낮은 주파수 대역폭을 고해상도로 분석하는 것이 인간의 청각 시스템 반영
  
**3. Mel-Spectrogram**  
  - Spectrogram이 Mel-Spectrogram으로 변환되면 인간의 귀의 주파수에 대한 인식이 선형적으로 변경됨  
  - 이러면 특징 추출과 처리가 쉬워짐
  
**4. WaveNet**  
  - 오디오의 파형을 생성하는 생성형 모델  
  - causal convolution과 dilated convolution의 아이디어를 채택  
  

## Experiment setup  
**- Dataset**  
  - 미디엄 버전의 무료 음악(길이가 30초이며 샘플링 속도가 22050인 25000개의 클립)  
  - 팝, 블루스, 포크, 재즈, 컨트리, 클래식 6가지의 카테고리  
**- Baseline**  
  - 오디오의 Mel-Spectrogram과 CQT 특징 추출  
  - 추출된 Mel-Spectrogram과 CQT 특징을 두 개의 레이어로 병합하여 입력  
  - 이 두 개의 레이어를 사전훈련된 WaveNet 디코더에 입력하여 오디오 생성  
  

## Result  
- 음악 생성 시스템의 성능을 평가하는 것은 주관적인 척도  
- 스타일 및 도메인 변환을 평가하는 것은 분류기를 통해 진행하기에 조금 더 간단  
- 변환된 음악 영역의 각 샘플에서 무작위로 30개의 음악 클립을 선택해 오디오 품질률과 스타일 변환율을 평가 지표로서 사용  
- 선형 attenuation 모델을 사용하였을 때 보다 비선형 attenuation 모델을 사용했을 때, 스타일 변환율이 더 좋음  
- 또한 오디오 품질률이 82.86%로서 보컬이 있는 음악 처리에서도 좋은 결과를 보여줬다고 할 수 있음  
  

## Conclusion  
- 본 논문에서는 CycleGAN과 WaveNet 디코더를 활용하여 사람의 목소리가 포함된 음악의 스타일 변환 수행  
- 음악의 평균 스타일 변환율은 94.07%를 달성  
  

## Author Information  
- Hongliang Ye and Wanning Zhu  


