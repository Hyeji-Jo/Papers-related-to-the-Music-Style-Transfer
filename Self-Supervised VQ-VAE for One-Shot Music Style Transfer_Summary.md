## Title  
- Self-Supervised VQ-VAE for One-Shot Music Style Transfer   
  
<br/>

## Problem Definition  
- 기존에 나온 음악 스타일 변환의 경우 각각의 개별 타깃 악기에 대한 트레이닝을 필요로 함  
- 시간이 많이 소요되며, 귀찮음 존재  
  
<br/>

## Motivation  
- 모델이 학습한 음정 및 음색 표현의 데이터 기반 분리가 필요함 -> VQ-VAE 활용  
  
<br/>

## Method  
- **VQ-VAE**  
  - 이산 잠재 표현을 가진 자동 인코더  
  - 인코딩할 수 있는 정보의 양에 제한 존재  
  - 입력과 디코더의 출력 사이 재구성 오류 Lae 최소화  

![VQ-VAE](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/assets/61963922/4fdec9a3-a465-4441-bc60-432e47007d82)
- 콘텐츠 입력 x와 스타일 입력 y 2개의 입력을 출력에 매핑하는 목표를 고려  
  - 두 개의 인코더(입력마다 하나씩)와 단일 디코더로 인코더-디코더 모델을 정의  
  
<br/>

## Experiment setup  
- **Dataset**  
  - 기본적인 가정은 x와 y가 같은 스타일(timbre)이지만 다른 내용을 가지고 있다는 것  
  - LMD(=Lakh MIDI Dataset)  
  - RT(=PG 뮤직의 오디오 트랙 세트) : 단일 악기의 반주 부분 또는 솔로를 단일 스타일로 연주하는 스튜디오 녹음 모음  
  - 두 가지 종류의 데이터 증강 수행  
  - 209k 개의 훈련 쌍(LMD8에서 119k, RT에서 90k)  
  
- **Model**  
  - 오디오 신호를 로그 스케일 크기 STFT 스펙트로그램으로 표현  
  - Adam 최적화 사용  
  - 32개의 epoch 동안 훈련하며 테슬라 V100 GPU에서 총 약 20시간이 소요  
  
<br/>

## Result  
- 콘텐츠 보존과 스타일 적합 두 가지 기준으로 평가  
  - 콘텐츠 보존  
    - 콘텐츠 입력의 음정이 출력물에 얼마나 유지되는지  
    - Pitch : MELLODIA 알고리즘을 활용하여 피치 윤곽을 추출하여 두 피치 세트 간의 불일치를 자카드 거리로 표현  
  - 스타일 적합  
    - 출력이 목표 음색에 얼마나 잘 맞는지  
    - Timbre : MFCC(Mel-frequency cepstral coefficients)를 활용하여 단일 비유사성 점수 출력

![result](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/assets/61963922/7e5ec4fe-7360-4815-a630-c687351b3dba)
- 그 결과 Ulyanov and Lebedev 알고리즘과 Musaicing 알고리즘 보다 결과가 좋음  


<br/>

## Conclusion  
- 출력물의 음질이 거의 완벽하지 않음  
  - 콘텐츠 입력 피치의 경우 일반적으로 출력에서 잘 보존되지만 빠른 음악에선 문제 존재  
  - 예를 들어 120 BPM의 템포에서 비트당 25.4비트의 정보만 인코딩 가능  
  - 이러한 것은 VQ-VAEs의 알려진 문제  
- 안정적인 사운드를 가진 피아노 음악의 경우 더 결과가 좋음  
- 해당 방법론에서의 가장 중요한 단점은 결정론적 디코더를 사용한 것  
  - WaveNet과 같은 표현력 있는 디코더를 사용하면 피아노뿐만 아니라 시간적 변동성이 큰 바이올린, 트럼펫 같은 악기의 성능도 향상될 것으로 생각  
  - 또한 작곡 스타일 변환과 같은 더 어려운 스타일 변환 작업도 가능할 것으로 생각   

<br/>

## Author Information  
- Ondřej Cífka, Alexey Ozerov, Umut Şimşekli, Gaël Richard  

<br/>

## [Github Implementation](https://github.com/cifkao/ss-vq-vae)  
