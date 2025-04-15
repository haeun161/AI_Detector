# AI_Detector
최신 생성형 모델이 생성한 AI 이미지를 탐지하는 모델 개발

## 선행 연구 조사
- [선행 연구 정리 자료](https://github.com/user-attachments/files/19746428/Task1_.pptx)

### 요점 정리
- 최근 상용화된 AI 생성 이미지 판별기 특징
  - AI or Not, Hive Moderation 두 사이트가 현재 다양한 분야의 이미지에 대해 높은 성능을 보인다
  - AI가 생성한 풍경화 이미지에 대해 정확도가 떨어진다는 취약점을 보인다
- 탐지가 어려움 이미지 유형
  - 복잡하고 추상적인 스타일
  - 하이브리드 이미지: AI가 생성한 이미지를 인간이 수정한 경우
  - 업스케일된 이미지(인간이 생성한 사진을 AI로 해상도를 높인 경우)
- 전문가 또한 특정 AI 생성모델(Midjourney v6, Dalle3)에 대해 이미지 판별의 어려움을 겪음
- 관련 연구
  - Stable Diffusion과 StyleCLIP 딥페이크에 대한 최근 8가지 탐지기
    - UnivCLIP, DE-FAKE, DCT (Discrete Cosine Transform), Patch-Forensics, Gram-Net, Resynthesis, CNN-F, MesoNet
  - FakeShield: 이미지 진위 평가, 조작 영역 마스크 생성, 판단 근거까지 제공하는 멀티모달 프레임워
 
## 목표
- 상용화된 AI 생성 이미지 판별기보다 적은 데이터셋으로 좋은 성능을 보이는 것

## Method
- EfficientNetB6를 FineTuning 하여 AI가 생성형 이미지인지 분류 태스크 수행

## 데이터셋 구축
- Flamel, Midjourney, DALLE, Stable Diffusion 상용화 모델을 사용하여 생성형 데이터셋 이미지를 구축
- 다양한 카테고리를 포함시키기 위해 얼굴, 동물, 음식, 자연풍경, 실내 가구, 건축물, 흑백사진 등 다양하게 포함
- 이외에 오픈된 데이터셋을 선별하여 사용
  - 지속적인 이슈인 Deep Fake 대응을 위해 [Fake Face](https://www.kaggle.com/datasets/xhlulu/140k-real-and-fake-faces) 사용
  - 상용화된 AI 생성 이미지 판별기인 Hive, AI or Not, Maybe, Illuminarty에서 취약하다고 들어난 Fake 풍경화 이미지 판별 타겟으로 [Artistic Works](https://www.kaggle.com/datasets/superpotato9/dalle-recognition-dataset0) 사용
  - 다양한 생성형 모델과 카테고리를 포함하고 있는 [GenImage](https://github.com/GenImage-Dataset/GenImage)와[MiT 구축 이미지](https://www.kaggle.com/datasets/tristanzhang32/ai-generated-images-vs-real-images/data) 데이터셋 사용

## 현재 최고 성능: 데이터 구조와 하이퍼파라미터
- ![image](https://github.com/user-attachments/assets/803545f6-7151-4fb3-8b10-637078ad28fa)
- HyperParameter
  - Learning Rate: 0.0005
  - Batch: 8 (16부터는 GPU 부족)
  - Epoch: 20
  - D/O: 0.3
  - Regulatization Rate: 0.005
- Fine-Tuning할 Layer 수: 30

## 사이트 주소
https://aidetector-k6fwtyk6gyqodyvadhzxfj.streamlit.app/
