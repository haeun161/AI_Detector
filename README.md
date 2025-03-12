# AI_Detector
최신 생성형 모델이 생성한 AI 이미지를 탐지하는 모델 개발

### 데이터셋 구축
- Flamel, Midjourney, DALLE, Stable Diffusion 상용화 모델을 사용하여 생성형 데이터셋 이미지를 구축
- 다양한 카테고리를 포함시키기 위해 얼굴, 동물, 음식, 자연풍경, 실내 가구, 건축물, 흑백사진 등 다양하게 포함
- 이외에 오픈된 데이터셋을 선별하여 사용
  - 지속적인 이슈인 Deep Fake 대응을 위해 [Fake Face](https://www.kaggle.com/datasets/xhlulu/140k-real-and-fake-faces) 사용
  - 상용화된 AI 생성 이미지 판별기인 Hive, AI or Not, Maybe, Illuminarty에서 취약하다고 들어난 Fake 풍경화 이미지 판별 타겟으로 [Artistic Works](https://www.kaggle.com/datasets/superpotato9/dalle-recognition-dataset0) 사용
  - 다양한 생성형 모델과 카테고리를 포함하고 있는 [GenImage](https://github.com/GenImage-Dataset/GenImage),[MiT 구축 이미지](https://www.kaggle.com/datasets/tristanzhang32/ai-generated-images-vs-real-images/data) 데이터셋 사용
 
### Method
EfficientNetB6를 FineTuning 하여 AI가 생성형 이미지인지 분류
