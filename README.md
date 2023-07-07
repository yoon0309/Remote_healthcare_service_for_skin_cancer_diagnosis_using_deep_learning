# Cp1: 딥러닝을 이용한 피부암 진단 원격 의료 서비스


## **1. 데이터 셋 설명**

- 흑색종 검출 데이터셋: [https://www.kaggle.com/datasets/wanderdust/skin-lesion-analysis-toward-melanoma-detection](https://www.kaggle.com/datasets/wanderdust/skin-lesion-analysis-toward-melanoma-detection)
- HAM10000 데이터셋: [https://www.kaggle.com/datasets/surajghuwalewala/ham1000-segmentation-and-](https://www.kaggle.com/datasets/surajghuwalewala/ham1000-segmentation-and-) classification?select=masks
- 흑색종 피부암 데이터셋: [https://www.kaggle.com/datasets/hasnainjaved/melanoma-skin-cancer-dataset-of-10000-images](https://www.kaggle.com/datasets/hasnainjaved/melanoma-skin-cancer-dataset-of-10000-images)

## **2. 프로젝트에서 풀고자 하는 문제 (문제인식, 문제 정의, 가설)**

프로젝트의 목적으로는 

  1. 100% 원격 진료 서비스로 수도권 병원의 서비스를 의료 취약 계층의 접근의 원활하게 하는 것
  2. 피부암과 같은 자가진단이 어려운 질병을 딥러닝 머신 구현을 통해 간단하고 정확히 진단 받도록 하는 것

왜 피부암인가? 
- UV-C(파장: 200~280nm)와 같은 유해 자외선은 대부분 지표에 도달하지 않지만, 환경문제로 오존층에 구멍(오존홀)이 생기는 경우 지상에 도달하게 되는데, 이때 사람들의 세포조직을 손상시켜 피부암을 초래합니다.
- 피부암 방치 시에는 피하조직과 근육, 심지어 뼈에 전이되어(퍼져) 피부와 장기에 있는 정상세포의 활동을 방해합니다.
- 피부암의 종류에는 기저세포암, 편평세포암, 흑색종이 있습니다. 
- 피부암 별 특성
    - 기저세포암, 편평세포암
        - 혈류나 림프절을 통한 전이확률과 사망률은 낮지만 재발 시 보기에 흉측해질 수 있음
    - 흑색종
        - 혈류나 림프절을 통해 신체의 다른 부위로 퍼지며, 방치 시 사망에 이를 수 있음
        - 일반 점(모반)과 형태가 비슷해 조기에 구분하지 못하는 경우가 많음
        - 흑색종을 잘 구별하는 것이 필요

## **3. 프로젝트 진행과정**
<img width="500" src="https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/72b58902-25bc-4110-b0d8-fce907dd416f"> 

위와 같이 업무 분담을 하였습니다. 

- 2023년 05월 이전으로 개명 전 이름 박윤아로 참여했습니다.  

## **4. 문제상황 해결과정(분석기법, 모델 등)**

국내 피부암 환자 현황으로는 

![Untitled (1)](https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/9d23a66e-d0ab-4a21-a045-2e05fd575b4a)

![Untitled](https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/2901c11e-e175-40bb-9388-50ed4fdb5f5f)

매년 증가 추세를 보이고 있으며 그 중 50세 이상의 고령 여자 환자의 비율이 높게 나타났습니다. 

![Untitled (2)](https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/a61b8558-e5be-424e-b7f7-88c3771dcdb4)
![Untitled (3)](https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/6c444484-7a27-4eca-96d9-bde9fe8521a1)


고령인구 비율이 높은 순위는 
1. 전라남도 
2. 경상북도 
3. 전라북도 

전국 병원 분포 낮은 분위
1. 전라남도 
2. 경상북도 
3. 전라북도 

-> 이 지역으로 인해 지방의료 감소로 인해 고령인구가 많은 지방이 상대적으로 의료 혜택을 보기 어려운 상황 

비대면 진료 앱(앱스토어의 굿닥, 나만의 닥터, 닥터온, 똑닥, 모비닥, 엠비닥 등)의 후기의 동향을 살펴보았을 때, 

**3점 이상 후기 가중치, 빈도**

![Untitled (4)](https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/2c9dcecf-9a9f-486c-9b85-f0a619a7a50d)


긍정 평가와 사용자 반응으로는 

- 비대면 진료가 편리하고
- 수도권의 경우 연결된 병원이 많아서 좋으며
- 지방의 경우에도 수도권 병원에서 비대면 진료를 볼 수 있어 편리
- 거동이 불편하신 분들이 원격 진료를 볼 수 있어 편리

**3점 이하 후기 가중치, 빈도**

![Untitled (5)](https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/1c97032e-84aa-4483-a40c-264b28af71cd)

부정평가와 사용자 반응으로는

- 지방의 경우 연결된 병원이 없어서 불편함
- 비대면 진료를 신청했는데 병원에서는 내원하라고 함
- 거주지역외에 타지역 병원과 연결되어 내원이 불편함

- 대시보드
[https://datastudio.google.com/reporting/f7b1d164-2672-4212-a229-db72227e66d1/page/p_o9k9aizkyc\](https://datastudio.google.com/reporting/f7b1d164-2672-4212-a229-db72227e66d1/page/p_o9k9aizkyc%5C) [https://datastudio.google.com/reporting/f7b1d164-2672-4212-a229-db72227e66d1/page/p_o9k9aizkyc\](https://datastudio.google.com/reporting/f7b1d164-2672-4212-a229-db72227e66d1/page/p_o9k9aizkyc%5C) [https://datastudio.google.com/reporting/8d139f58-d8f8-41bb-ab98-b23181b5bc97](https://datastudio.google.com/reporting/8d139f58-d8f8-41bb-ab98-b23181b5bc97)


딥러닝을 통한 이미지 분류 데이터 셋은

<img width="996" alt="198942981-445076c5-aa87-4fab-9330-741602d824a8" src="https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/d323c4aa-cd56-48d7-9497-00945f199943">

흩어진 이미지 데이터를 위와 같은 방법으로 합쳐서 진행하였습니다. 

## **5. 결과정리** 
    
<img width="1108" alt="198943176-81bd3dfc-d82c-4174-9740-976d5f413915" src="https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/f110ca1d-465e-44a3-9b1a-6628c83fcfbe">
<img width="865" alt="198946620-863855de-d1fa-4554-b235-4cf6962e3f2a" src="https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/db482678-5da1-4de3-a9a5-288d0225f25e">


- 시연 영상 [https://user-images.githubusercontent.com/102234250/198946771-dd125da1-af78-4294-bc15-9fb1d9ef8e9f.mp4](https://user-images.githubusercontent.com/102234250/198946771-dd125da1-af78-4294-bc15-9fb1d9ef8e9f.mp4)
- 발표영상 [https://youtu.be/rfUzJfn5rwQ](https://youtu.be/rfUzJfn5rwQ)

## **6. 한계점 및 해결방안**
기획에 집중해서 이전에 진행한 프로젝트처럼 모델의 성능, 기능을 다루지 못해서 아쉬웠습니다.
또한, 하드웨어 관련 문제로 딥러닝을 웹에 적응하지 못하였음이 아쉬웠던 프로젝트였습니다.  


## **7. 출처**
- 통계청
    - KOSIS 고령인구비율 , 행정구역별 위경도
- 보건의료빅데이터개방시스템
    - 피부암 환자수 추이, 성별 연령구간별 내원일수
- 공공데이터포털
    - 전국의료기관표준데이터
