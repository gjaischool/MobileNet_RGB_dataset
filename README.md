# MobileNet_RGB_dataset

### [데이터셋 출처](https://www.kaggle.com/datasets/selfishgene/youtube-faces-with-facial-keypoints)

### 데이터셋 구성
이미지 & 68개의 keypoint 약 26만장

### RGB_dataset_분석.ipynb
: 828명의 인물 / 각 인물당 최대 240 프레임으로 최대 6개의 영상으로 구성 / 총 2194개의 .npz파일이 있으며 이는 영상 이미지와 68개의 keypoint로 구성

## 폴더내 파일 설명
[각 파일의 best model](https://drive.google.com/drive/folders/1K-WdH8WnHdSLzUm-ucGt8p5QEYICQ-pm)  
### 1. y_v2_adam_lr001_eye.ipynb
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / lr 1e-3, 1e-4 / 100 epochs  
Epoch 97: val_loss improved from 0.00001 to 0.00001, saving model to y_eye_v2_adam.h5   
358s 141ms/step - loss: 1.4649e-05 - mae: 0.0031 - val_loss: 1.3701e-05 - val_mae: 0.0030 - lr: 1.0000e-0
![image](https://github.com/user-attachments/assets/308539ab-cbef-4d57-b835-8addc8afd0f5)  

### 2. y_v2_adam_all_5만.ipynb
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / lr 1e-4 / 100 epochs  
Epoch 84: val_loss improved from 0.00004 to 0.00004, saving model to y_all_v2_adam.h5   
544s 334ms/step - loss: 3.9693e-05 - mae: 0.0048 - val_loss: 4.2830e-05 - val_mae: 0.0050
![image](https://github.com/user-attachments/assets/d8c014cd-0f52-4b1c-9008-a3bd94bf3b32)  

### 3. y_v2_adam_all_10만.ipynb
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / lr 1e-4 / 100 epochs  
Epoch 60: val_loss improved from 0.00010 to 0.00010, saving model to y_all_v2_adam_10.h5  
244s 146ms/step - loss: 3.1613e-05 - mae: 0.0044 - val_loss: 9.8058e-05 - val_mae: 0.0074
![image](https://github.com/user-attachments/assets/35248f3c-ee54-4252-ab87-8f5b7ffdecdf)  

### 4. y_v2_adam_lr001_mouth.ipynb  
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / lr 1e-4 / 100 epochs    
Epoch 75: val_loss improved from 0.00002 to 0.00002, saving model to y_mouth_v2_adam_lr0001.h5  
294s 117ms/step - loss: 2.0858e-05 - mae: 0.0035 - val_loss: 1.8806e-05 - val_mae: 0.0034
![image](https://github.com/user-attachments/assets/4e9d73f6-698c-46d0-b27c-1df6dd5befb5)  

### 5. y_v2_adam_lr001_all_mouth.ipynb  
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / lr 1e-4 / 100 epochs  
Epoch 93: val_loss improved from 0.00002 to 0.00002, saving model to y_all_mouth_v2_adam_lr0001.h5  
332s 133ms/step - loss: 2.0894e-05 - mae: 0.0036 - val_loss: 2.0056e-05 - val_mae: 0.0035
![image](https://github.com/user-attachments/assets/a42506e3-cce1-4a9f-94ae-8ead84d60586)  

### 6. y_v2_adam_all_10만_version2.ipynb  
: MobileNetV2 / scale img size 224 / batchsize 16 / Adam / reduce_lr / 200 epochs  
Epoch 89: val_loss improved from 0.00009 to 0.00009, saving model to y_all_v2_adam.h5  
271s 163ms/step - loss: 2.2144e-05 - mae: 0.0037 - val_loss: 9.3622e-05 - val_mae: 0.0068 - lr: 2.0000e-04
![image](https://github.com/user-attachments/assets/f5d550c5-f55b-4a90-ab09-24dedb90d8f5)

### 모델 총 정리  
![image](https://github.com/user-attachments/assets/9bb9e957-3e6f-4ad1-9f37-014cc7462ef3)

## 진행하면서 배운점
1. IR dataset과 RGB dataset 차이에 의한 실시간 스트리밍 성능 지표 확인이 됐다.
2. 68개의 keypoint로 진행시 입, 코, 눈과 같은 서로간 연간성을 보임. 그래서 입을 가리게 되면 눈을 잡지 못하는 걸 확인.
3. 눈만 keypoint 학습시 눈을 매우 잘잡는 걸 확인.
4. 이번엔 입의 내곽 8 keypoint만 이용시보다 외곽까지 총 20개 keypoint 이용시 더 잘잡는 걸 확인. 
