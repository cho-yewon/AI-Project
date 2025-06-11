# AI-Project
https://www.kaggle.com/datasets/utkarshsaxenadn/fruits-classification

## 문제 정의  
문제 유형 : 영상 데이터 분류  
입력 변수 : 32x32 RGB 픽셀 이미지  
출력 변수 : 0-4 범위의 정수 클래스  


## 데이터 설명  
총 이미지 수 : 250장 (클래스당 50장)  
클래스 수 : 5개 (사과, 바나나, 포도, 망고, 딸기)  
입력 속성 : 이미지  
전처리 : 모든 이미지를 32x32로 resize, 픽셀 값 정규화(0-1 스케일)  
데이터 분할 :   
- Training : 76.9% (250장)  
- Validation : 15.4 (50장)  
- Test : 7.7% (25장)  


## 전처리 과정  
이미지 resize : cv2.resize(img, (32,32))  
정규화 : x = x / 255.0  
numpy array로 변환 : x = np.array(x).reshape(-1,32,32,3)  


## 하이퍼 파라미터 최적화 결과  
Conv2D 필터 구조  
|항목|test1|test2|test3|
|----|-----|-----|-----|
|Conv2D 필터 구조|64 --> 64 --> 128|32 --> 64 --> 64|64 --> 128 --> 128|
|Dense 노드 수|128|128|256|
Test 정확도|13/25=52%|16/25=64%|17/25=68%|


## 최종 하이퍼 파라미터
Conv 구조 : 64 --> 128 --> 128  
Dense 노드 수 : 256  
Dropout : 0.3 (두 번)  
Activation : ReLU  
Optimizer : Adam  
Batch size : 10  
Epochs : 50  
Validation split = 0.2  


# 최종 성능
훈련 정확도 : 약 90% 이상  
Validtaion 정확도 : 최고 78%  
##### Test 성능 : 17/25=68% 정확도
