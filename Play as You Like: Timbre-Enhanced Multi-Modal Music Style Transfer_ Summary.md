## Title  
- Play as You Like: Timbre-Enhanced Multi-Modal Music Style Transfer 
  
<br/>

## Problem Definition  
- polyphonic music recordings(다성 음악 녹음)의 스타일 변환에 어려움 존재  
- 예전 연구에서는 서로 다른 도메인(피아노, 기타, 현악기 등) 간의 multi-modal 및 비결정론적 매핑을 거의 달성할 수 없음  
- 변환된 음악의 음색 경우 품질 저하의 문제가 존재  

<br/>

## Motivation  
- 일반적으로 음악은 불변의 콘텐츠와 변할 수 있는 스타일 두 가지 속성이 존재  
- 콘텐츠 속성을 요소별로 지정하고 스타일 변환이 수행되도록 도메인 간의 높은 수준의 매핑을 위해 GAN 접근 방식 사용 필요  

<br/>

## Method  
- 페어링 되지 않은 훈련 데이터로 고품질 및 다양성 음악 작품을 생성하기 위해 비지도 이미지 변환 프레임워크인 MUNIT 사용  
- 상대론적 평균 GAN인 RaGAN도 활용하여 빠른 수렴과 높은 안정성 달성  
- 훈련 단계에서 생성기가 원 데이터의 분포를 캡처할 뿐만 아니라 원 데이터와의 비슷할 확률을 낮춘다는 점에서 다른 GAN 아키텍처와 다름   
- 음색의 경우 서로 밀접한 형태의 관계를 가지고 있기 때문에 대상 도메인에서 채널별 일관성을 유지하기 위해 고유 일관성 손실이라는 새로운 손실 함수를 도입  
- 콘텐츠 보존 및 음질 측면에서 더 나은 성능을 달성함  

<br/>

## Experiment setup  
**- Dataset**  
 - 피아노 솔로, 기타 솔로 및 현악 4중주의 세 가지 다른 장르 간의 양방향 스타일 전송 작업에 대한 실험을 수행  
 
**- Baseline**  
 - MUNIT 프레임 워크, RaGAN
   ![모델](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/assets/61963922/1290be01-9421-4756-bc26-43966d35da89)
 
**- Evaluation Metric**  
 - 고유 일관성 손실이라는 새로운 손실 함수를 도입  

<br/>

## Result  
1. 클래식 피아노 독주와 클래식 현악 4중주 간의 쌍방향 스타일 전환  
2. 인기 피아노 솔로와 인기 기타 솔로 간의 쌍방향 스타일 전송(두 도메인의 데이터는 유튜브에서 피아니스트와 기타 연주자가 다루는 34개의 피아노 솔로(8,200초)와 56개의 기타 솔로(7,800초)로 구성되어 있습니다.)  
 간단히 말해서, 피아노 대 기타 (P2G), 기타 대 피아노 (G2P), 피아노 대 현악 4중주 (P2S), 현악 4중주 (S2P) 총 4개의 하위 작업 존재  

- 경쟁력 있는 비지도 스타일 전송 네트워크인 CycleGAN과 UNIT 과의 주관적인 테스트 수행  
- 실험의 참가자는 1(낮음)에서 5(높음)까지 세 가지 문제를 채점하도록 요청됨  
  1 - 스타일 전송 성공(ST): 전송된 버전의 스타일이 대상 도메인과 얼마나 잘 일치하는지  
  2 - CP(Content Preservation) : 전송된 버전의 내용이 원본과 얼마나 잘 일치하는지  
  3 - 음질(SQ): 음질이 얼마나 좋은지  

  2번 문항의 경우 CycleGAN이 가장 우수한 성능을 발휘하고 나머지 1,3번 문항의 경우 MUNIT이 다른 두 모델보다 성능이 뛰어남   

<br/>

## Conclusion  
- multi- modal framework가 이전의 접근 방식보다 더 적합하다  
- 쌍을 이루는 데이터와 사전 훈련된 모델이 필요하지 않지만 안정적이고 성능이 좋다  

<br/>

## Author Information  
- Chien-Yu Lu,Min-Xin Xue,Chia-Che Chang,Che-Rung Lee,Li Su  

<br/>

## [Github Implementation](https://github.com/ChienYuLu/Play-As-You-Like-Timbre-Enhanced-Multi-modal-Music-Style-Transfer)

