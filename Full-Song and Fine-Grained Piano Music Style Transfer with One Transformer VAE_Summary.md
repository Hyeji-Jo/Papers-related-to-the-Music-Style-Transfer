## Title  
- MuseMorphose: Full-Song and Fine-Grained Piano Music Style Transfer with One Transformer VAE
  
<br/>

## Problem Definition  
- 트랜스포머와 변형 자동 인코더(VAE) 각각의 장점을 모두 가진 단일모델(=MuseMorphose) 구성을 목적으로 함

<br/>

## Motivation  
- 신경망의 발달로 인해 음악 작곡을 위한 딥러닝 기반 방법이 계속해서 발달하며 최신모델들은 트랜스포머, 변형 자동 인코더 중 하나의 아키텍처를 기반으로 함
**- 트랜스포머**  
  - 3~5분 길이의 일관된 음악 작곡 가능    
  - 긴 시퀀스 생성을 위한 최첨한 모델  

**- VAE**  
  - 인코더와 디코더 및 그 사이에 Kullback-Leibler(KL)로 구성되어 있는 심층 잠재 변수 모델  
  - 음악 생성 및 음악 스타일 변환 작업에 훌륭한 선택  
  - RNN 기반  

<br/>

## Method  
- MIDI 파일은 음악 작품의 템포(분당 비트 수 또는 bpm), 타임 시그니처(예: 3/4, 4/4, 6/8 등), 각 음의 시작 및 해제 타임스탬프 및 속도(예: 음량)를 저장  
- REMI(Revamed MIDI-derived events) : 음악의 고유한 시간 단위, 즉 막대와 비트를 통합  
- Pre-attention, In-attention, Post-attention 3가지 사용  
**- Pre-attention**  
  - 세그먼트 수준 조건은 모든 attention layer 이전에 한 번만 트랜스포머 디코더에 들어감  
  - BERT의 세그먼트 임베딩이 토큰 임베딩과 직접 합산되는 점을 제외하고는 방법론적으로 유사  
**- In-attention**  
  - 트랜스포머 디코더에게 셀프 attention layer 전체의 세그먼트 레벨 조건을 더 자주 알려줌  
  - 세그먼트 수준 조건을 복사하여 곳곳에 붙여넣음으로써 트랜스포머에 미치는 영향을 더욱 확대할 수 있을것으로 기대  
**- Post-attention**  
  - 위의 두 메커니즘과 달리 세크먼트 임베딩이 자체 attention layer와 상호 작용하지 않음  
  
- 12-layer Transformer-XL 채택
- Adam optimizer 활용
- K=32
- 처음 500개의 훈련 단계에서 학습 속도를 0에서 2x10-4까지 선형적으로 올려가며, 그 후 코사인 학습 속도 감소(600,000단계)를 사용
- 각 모델은 약 20개의 에포크 동안 배치 크기가 4개인 엔비디아 테슬라 V100 GPU(32GB 메모리 포함)에서 훈련되며, 이는 2일이 소요
   
<br/>

## Experiment setup  
- 긴 시퀀스 생성 동안 시간 변화 조건 벡터를 사용하여 트랜스포머 디코더를 조건화하는 매커니즘 고안  
- Attention이 장착된 트랜스포머 디코더와 높은 수준의 청사진을 독립적으로 추출하는 방법을 배우는 트랜스포머 인코더를 결합  
- 그로인해 세분화된 음악 스타일 변환이 가능한 MuseMorphose 모델 구축  
- 인코더와 디코더의 경우 VAE 목표로 훈련되며 속성 임베딩을 통해 음악 스타일 변환을 가능하게 함  
  
> RNN의 경우 2가지 문제 존재  
> 1. 하나의 고정된 크기의 벡터에 모든 정보를 압축하려고 하니까 정보 손실 발생  
> 2. 기울기 소실 문제 존재  
> -> 이를 대안으로 입력 시퀀스가 길어지면 출력 시퀀스의 정확도가 떨어지는 것을 **보정해주기 위해 등장한 기법 Attention**  

**- Dataset**  
  - 곡당 최대 17개의 기악 트랙(예: 피아노, 스트링 및 드럼)이 있는 >20,000곡을 포함하는 팝 음악 미디 데이터 세트인 LPD-17 클린 데이터 세트
  - 타임 시그니처가 4/4(즉, 마디당 4비트)인 10,626곡의 하위 집합을 취하며, 피아노가 최소 절반의 시간동안 재생되는 경우 채택
  - 데이터 세트에는 650시간의 음악이 포함
  - 객관적인 평가를 위한 검증 세트로 곡의 4%(즉, 425곡)를 추출

<br/>

## Result  & Conclusion  
- 검증 세트의 고유한 노래의 막대 수준 조건을 사용하여 각각 425개의 재창조에 대한 점수 계산  
- 비교를 위해 모델이 처음부터 400개의 32마디 조각을 무작위로 생성하도록 하고, 훈련 세트에서 추출한 400개의 무작위 조각 쌍에 대해 점수가 계산되는 무작위 기준선을 추가로 포함  
- In-attention이 세그먼트 수준의 시간 변화 조건을 가진 트랜스포머 디코더를 제어하는 데 결과가 가장 효과적  

<br/>

## Author Information  
- Shih-Lun Wu, and Yi-Hsuan Yang, Senior Member, IEEE  

<br/>

## [Github Implementation](https://github.com/YatingMusic/MuseMorphose)

