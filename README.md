# 얼굴인식 프로젝트

인증사진과 프로필사진을 통한 동일인물 여부 판단

# 프로젝트 상세 내용
### 배경
- 기존 모델에서 인증사진에 얼굴이 없음에도 인증이 되거나, 동일인물임에도 인증이 되지 않는 사례가 많아 개선할 필요가 있다.
### 목표
- 기존 기업에 있는 얼굴인식 모델의 성능 향상
### 진행 과정
1. 데이터 수집 ([데이터](https://aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=528))</br>
  - 총 1000가계(3000명)이상ㅇ을 대상으로 80,700장 이상의 얼굴 이미지 데이터셋 
2. 미디어 파이프를 활용한 데이터 전처리</br>
  - mediapipe라이브러리를 활용한 얼굴 검출 및 얼굴 정렬과 cv2를 활용한 그레이스캐일링과 리사이징
3. 아크페이스 활용 동일인물 인식 모델 개발</br>
  - 아크페이스를 활용하여 임베딩 벡터생성 및 코사인 유사도를 활용해 동일인물 여부 판단
4. 모델 테스트
- 결과: Accuracy기준 0.947, 서비스 속도는 대략 3~4초정도 소요된다.
# 기여한 내용
### 데이터 전처리
- mediapipe의 facedetection을 통해 사진의 얼굴부분만 검출
- mediapipe의 facemesh를 통해 양안의 랜드마크를 찾고 양안을 기준으로 얼굴 정렬
- cv2를 통해 이미지의 그레이 스케일링 및 리사이징
### 모델 구현 및 학습
- [모델](https://github.com/siriusdemon/Build-Your-Own-Face-Model/tree/master/recognition)을 통해 전처리를 완료한 데이터를 이용해 모델 학습
- 인증사진과 프로필사진의 URL을 통해 동일인물 여부 파악 시스템 구축(main.py)
# 회고
### 잘한 점
- 전처리 과정에서 얼굴 검출을 위한 미디어 파이프 관련 학습 내용
- 논문 구현함에 있어서 방법 이해
### 아쉬운 점
- 전처리 과정과 모델 구현 부분에서 너무 많은 시간을 낭비
- facenet 모델 학습과 그에 따른 비교결과가 없는 부분이 아쉬움
- 프로젝트 관련하여 효율적인 팀 역할분배 실패
### 앞으로의 계획
- 미디어파이프를 통한 얼굴 검출 부분의 개선(얼굴 검출의 민감도 조정을 통해 너무 많은 데이터가 검열되지 않도록 한다)
- 논문 구현을 해본 경험이 있기 때문에 이를 응용해볼 수 있다.


# 참고
[발표자료](https://docs.google.com/presentation/d/17219LG8eML33IYX20PDJRXY1isx_Td5Q/edit?usp=sharing&ouid=117033188443854497803&rtpof=true&sd=true)</br>
[성별파악](https://drive.google.com/file/d/1OXVYIP2mBSY7FhPhdPaNkwF0JDStxUxs/view?usp=sharing)(용량이 큰 관계로 checkpoints 안에 넣어서 사용)
