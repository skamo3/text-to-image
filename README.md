# text-to-image
 - gan 모델 도전기
 ## 목표 
 - User가 Input으로 특정 Text를 넣었을 때 그에 맞는 QuickDraw Image를 그려주는 Model
 ## 사용 Dataset
 [QuickDraw-Dataset](https://github.com/googlecreativelab/quickdraw-dataset)
 ![image](https://user-images.githubusercontent.com/54701846/69910685-ecbe7500-1452-11ea-855f-9e83a8edd4d8.png)
 
## 1차 
- Generator 에 341(기존 class+False) + 100(Noise) 를 넣어주고 Discriminator에 Labeling 된 Dataset을 넣어 분류하게 해 QuickDraw Image를 그려내도록 하기  
![image](https://user-images.githubusercontent.com/54701846/69911937-f4d3e000-1465-11ea-9420-741b6f1543c6.png)

-그림을 그리지 못하고 noise image만 생성

## 2차 
- Generator에 넣어주는 341의 데이터를 빼고 Discriminator에서만 분류하도록 설정
![image](https://user-images.githubusercontent.com/54701846/69912704-58630b00-1470-11ea-8b88-b969250aa351.png)

- 결과물이 비슷함
![image](https://user-images.githubusercontent.com/54701846/69912799-94e33680-1471-11ea-9270-b22fe4468a9f.png)

## 문제찾기
 1. Class의 갯수가 너무 많아서 학습을 못할 수 있음
 2. Loss Function의 문제
### 해결
 1. 전체가 아닌 단일 Class에 대한 Model로 해보기
 2. 다른 Loss Function 찾아보기
 
## 3차 
 - 단일 Class로 학습시킨 결과 
 ![image](https://user-images.githubusercontent.com/54701846/69912789-7ed57600-1471-11ea-82b7-f4d1ffc36be4.png)

 - 전보단 나은 양상을 보이지만 여전히 그리는데에 한계가 있음
 
### 추후 모델 변경 계획
 - Loss Function 바꿔보기 : 조사 중 Gan모델은 Loss Function에 따라 수많은 불안정성이 발생함을 알게 됨
 - 참고 Gan => WGAN, [SAGAN](https://towardsdatascience.com/not-just-another-gan-paper-sagan-96e649f01a6b)
