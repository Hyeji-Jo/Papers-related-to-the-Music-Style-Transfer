# Music style transfer 관련 논문 리뷰  
<br/>

## 📌 Index
[0. Paper list up](#📃-Paper-list-up)  
[1. Music Style Transfer_A Position Paper](#1️⃣-Music-Style-Transfer_A-Position-Paper)  
[2. Symbolic Music Genre Transfer with CycleGAN](#2️⃣-Symbolic-Music-Genre-Transfer-with-CycleGAN)  
[3. Music Style Transfer with Vocals Based on CycleGAN](#3️⃣-Music-Style-Transfer-with-Vocals-Based-on-CycleGAN)  
[4. Timbre-enhanced Multi-modal Music Style Transfer](#4️⃣-Timbre-enhanced-Multi-modal-Music-Style-Transfer)  
[5. Self-Supervised VQ-VAE for One-Shot Music Style Transfer](#5️⃣-Self-Supervised-VQ-VAE-for-One-Shot-Music-Style-Transfer)  
[6. Actions Speak Louder than Listening: Evaluating Music Style Transfer based on Editing Experience](#6️⃣-Evaluating-Music-Style-Transfer-based-on-Editing-Experience)  
[7. Full-Song and Fine-Grained Piano Music Style Transfer with One Transformer VAE](#7️⃣-Full-Song-and-Fine-Grained-Piano-Music-Style-Transfer-with-One-Transformer-VAE)  
[8. Can Machines Generate Personalized Music? A Hybrid Favorite-aware Method for User Preference Music Transfer](#8️⃣-Can-Machines-Generate-Personalized-Music?-A-Hybrid-Favorite-aware-Method-for-User-Preference-Music-Transfer)  
  
<br/><br/>
  
  
## 📃 Paper list up
|Paper|Published in|Year|Note:|
|------|---|:--:|---|
|[Music Style Transfer: A Position Paper](https://arxiv.org/pdf/1803.06841.pdf)|arXiv: Sound|2018|[Github Implementation](https://github.com/ChienYuLu/Play-As-You-Like-Timbre-Enhanced-Multi-modal-Music-Style-Transfer)|
|[Symbolic Music Genre Transfer with CycleGAN](https://arxiv.org/pdf/1809.07575.pdf)|ICTAI(International Conference on Tools with Artificial Intelligence)|2018||
|[Music Style Transfer with Vocals Based on CycleGAN](https://iopscience.iop.org/article/10.1088/1742-6596/1631/1/012039)|ICAICS(2nd International Conference on Artificial Intelligence and Computer Science)|2020||
|[Timbre-enhanced Multi-modal Music Style Transfer](https://arxiv.org/pdf/1811.12214.pdf)|TAAI(International Conference on Technologies and Applications of Artificial Intelligence)|2020||
|[Self-Supervised VQ-VAE for One-Shot Music Style Transfer](https://arxiv.org/pdf/2102.05749)|ICASSP(IEEE International Conference on Acoustics, Speech and Signal Processing)|2021|[Github Implementation](https://github.com/cifkao/ss-vq-vae)|
|[Actions Speak Louder than Listening: Evaluating Music Style Transfer based on Editing Experience](https://arxiv.org/pdf/2110.12855)|29th ACM International Conference on Multimedia|2021|[Github Implementation](https://github.com/s603122001/Bidirectional-Music-Style-Transformer)|
|[MuseMorphose: Full-Song and Fine-Grained Piano Music Style Transfer with One Transformer VAE](https://arxiv.org/pdf/2105.04090)|TASLP(IEEE/ACM Transactions on Audio, Speech, and Language Processing)|2022|[Github Implementation](https://github.com/YatingMusic/MuseMorphose)|
|[Can Machines Generate Personalized Music? A Hybrid Favorite-aware Method for User Preference Music Transfer](https://arxiv.org/pdf/2201.08526)|arXiv: Sound|2022|[Github Implementation](https://github.com/hu-music/UPMT)|


<br/><br/>
  
  
## 1️⃣ Music Style Transfer_A Position Paper  
> 음악 스타일 변환은 음색 변환, 연주 스타일 변환, 작곡 스타일 변환 3가지로 구성되어 있으며, 각각에 대한 정보 존재  

[Music Style Transfer: A Position Paper 요약 페이지🔎](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/blob/d57a25cfe7b6e00b6e90725ed08f14ccb54fe108/Music%20Style%20Transfer%3A%20A%20Position%20Paper_Summary.md)
  
<br/>

## 2️⃣ Symbolic Music Genre Transfer with CycleGAN  
> 이미지 스타일 변환으로 가장 성공한 GAN의 음악 장르 변환 실현 가능성 연구  
> 음악 음성이 아닌 재즈, 클래식, 팝의 MIDI 데이터를 활용하여 음악 장르 A에서 B로의 양방향 장르 변환 모델 구축  

[Symbolic Music Genre Transfer with CycleGAN 요약 페이지🔎](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/blob/d57a25cfe7b6e00b6e90725ed08f14ccb54fe108/Symbolic%20Music%20Genre%20Transfer%20with%20CycleGAN_Summary.md)  

<br/>

## 3️⃣ Music Style Transfer with Vocals Based on CycleGAN  
> 음악 오디오의 Mel-Spectrogram과 CQT 특징 추출하여 CycleGAN 모델로 도메인 변환을 수행하고 사전훈련된 WaveNet 디코더에 입력하여 오디오 생성  
> 기존의 보컬이 없는 음악들을 활용한 연구들과 달리 보컬이 존재하는 음악을 활용하였으며, 비선형 attenuation 모델을 사용하여 견고한 모델 생성  

[Music Style Transfer with Vocals Based on CycleGAN 요약 페이지🔎](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/blob/f731efab8428b3ad09808a4a92f457e66b8b471d/Music%20Style%20Transfer%20with%20Vocals%20Based%20on%20CycleGAN_Summary.md)   

<br/>
  
## 4️⃣ Timbre-enhanced Multi-modal Music Style Transfer  
> 비지도 이미지 변환 프레임워크인 MUNIT과 상대론적 평균 GAN인 RaGAN을 활용하여 서로 다른 장르 간 양방향 스타일 변화 작업에 대한 실험 수행  

[Timbre-enhanced Multi-modal Music Style Transfer 요약 페이지🔎](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/blob/d57a25cfe7b6e00b6e90725ed08f14ccb54fe108/Play%20as%20You%20Like%3A%20Timbre-Enhanced%20Multi-Modal%20Music%20Style%20Transfer_%20Summary.md)  

<br/>
  
## 5️⃣ Self-Supervised VQ-VAE for One-Shot Music Style Transfer  
> VQ-VAE 모델을 활용한 음악 스타일 변화 작업을 수행했지만 출력물의 음질이 완벽하지 않음  
> WaveNet과 같은 표현력 있는 디코더 사용 시 다양한 악기들의 성능 향상 및 작곡 스타일 변환과 같은 더 어려운 스타일 변화도 가능할 것으로 생각  

[Self-Supervised VQ-VAE for One-Shot Music Style Transfer 요약 페이지🔎](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/blob/main/Self-Supervised%20VQ-VAE%20for%20One-Shot%20Music%20Style%20Transfer_Summary.md)  

<br/>
  
## 6️⃣ Evaluating Music Style Transfer based on Editing Experience  
> 설문지 기반 청취 테스트를 통해 결과를 도출한 기존 연구들과 달리 작곡가, 편곡자, 음악 제작자의 관점에서 연구 평가  
> BMST 기본 모델과 거기에 attention 메커니즘, 상대 위치 임베딩, CVAR의 절대 피치 학습을 더해 만든 모델의 비교 실험 수행  

[Evaluating Music Style Transfer based on Editing Experience 요약 페이지🔎](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/blob/main/Actions%20Speak%20Louder%20than%20Listening:%20Evaluating%20Music%20Style%20Transfer%20based%20on%20Editing%20Experience_Summary.md)  

<br/>
  
## 7️⃣ Full-Song and Fine-Grained Piano Music Style Transfer with One Transformer VAE  
> VAE 모델에 Transformer의 Attention 메커니즘을 추가하여 모델링  
> 3가지의 Attention 메커니즘을 비교해 본 결과 in-attention의 경우 결과가 가장 좋음  

[Full-Song and Fine-Grained Piano Music Style Transfer with One Transformer VAE 요약 페이지🔎](https://github.com/Hyeji-Jo/Papers-related-to-the-Music-Style-Transfer/blob/main/Full-Song%20and%20Fine-Grained%20Piano%20Music%20Style%20Transfer%20with%20One%20Transformer%20VAE_Summary.md)  

<br/>
  
## 8️⃣ Can Machines Generate Personalized Music? A Hybrid Favorite-aware Method for User Preference Music Transfer  


[Can Machines Generate Personalized Music? A Hybrid Favorite-aware Method for User Preference Music Transfer 요약 페이지🔎]()  

<br/>
