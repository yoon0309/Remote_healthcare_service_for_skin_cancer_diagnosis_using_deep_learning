# Cp1: 딥러닝을 이용한 피부암 진단 원격 의료 서비스(데이터 분석 관점)


## **1. 데이터 셋 설명**

- 애플 스토어의  메디팡팡, 모비닥, 엠디톡, 굿닥, 올라케어, 나만의 닥터, 닥터온, 똑닥의 리뷰 데이터 셋(2020년 3월 31일~2023년 9월 18일)
  
- 통계청
    - KOSIS 고령인구비율 , 행정구역별 위경도
- 보건의료빅데이터개방시스템
    - 피부암 환자수 추이, 성별 연령구간별 내원일수
- 공공데이터포털
    - 전국의료기관표준데이터

## **2. 프로젝트에서 풀고자 하는 문제 (문제인식, 문제 정의, 가설)**

피부암은 
- UV-C(파장: 200~280nm)와 같은 유해 자외선은 대부분 지표에 도달하지 않지만, 환경문제로 오존층에 구멍(오존홀)이 생기는 경우 지상에 도달하게 되는데, 이때 사람들의 세포조직을 손상시켜 피부암을 초래합니다.
- 피부암 방치 시에는 피하조직과 근육, 심지어 뼈에 전이되어 피부와 장기에 있는 정상세포의 활동을 방해합니다.

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

전국 병원 분포 낮은 순위
1. 전라남도 
2. 경상북도 
3. 전라북도 

따라서 전라남도, 경상북도, 전라북도 지역의 지방의료 감소로 고령인구가 많은 지방이 상대적으로 의료 혜택을 보기 어려운 상황에 처해있음을 확인 할 수 있었습니다. 

DA 분석으로는 긍정 평가와 사용자 반응, 부정평가와 사용자 반응을 확인하고, 2023년 9월 23일 이후 진행한 데이터 분석에서는 비대면 진료 서비스를 제공하고 있는 어플리케이션 리뷰분석을 통하여 사용자 의견을 이해하고 주제에 대한 트렌드를 발견하기 위하여 토픽분석을 진행하였습니다. 

그에 따른 가설은 

가설 1. 2020년에 앱 사용 리뷰가 많았을 것이다.

가설 2. 12월에 앱 사용 리뷰가 많았을 것이다. 

가설 3. 불만 리뷰를 남기는 사람들은 리뷰를 길게 쓸 것이다. 

로 진행하였습니다. 


## **3. 프로젝트 진행과정**
<img width="500" src="https://github.com/yoon0309/Remote_healthcare_service_for_skin_cancer_diagnosis_using_deep_learning/assets/102473586/72b58902-25bc-4110-b0d8-fce907dd416f"> 

위와 같이 업무 분담을 하였습니다. 

- 2023년 05월 이전으로 개명 전 이름 박윤아로 참여했습니다.  

## **4. 문제상황 해결과정(분석기법, 모델 등)**

현재 시중에 사용되고 있는 애플 스토어의 메디팡팡, 모비닥, 엠디톡, 굿닥, 올라케어, 나만의 닥터, 닥터온, 똑닥의 리뷰 데이터 셋(2020년 3월 31일~2023년 9월 18일)의 후기의 동향을 살펴보았을 때, 

### **기존 분석을 통한 알게된 결과**

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

### **업그레이드**




## **5. 결과정리** 
- DA

이번 분석을 통해서 피부암 환자는 꾸준히 증가 추세를 보이고 있으며 남/여를 구분해서 확인하였을 때, 여자, 50세 이상의 고령 환자의 비율이 높았음을 시각적으로 확인할 수 있었습니다.
또한, 고령인구와 전국 병원분포 낮은 순위로 확인해 보았을 때, 경상북도, 전라북도, 전라남도를 꼽을 수 있었습니다.
현재 시중에 사용되고 있는 비대면 앱 서비스 중 긍정 평가와 부정 평가로 나뉘어 확인할 수 있었는데 지방의 경우에는 연결된 병원이 없으며, 비대면 진료를 신청했음에도 불구하고 병원에서는 내원하길 원하여 거주지역 외의 타지역 병원과 연결되어 내원이 불편한 경험을 공유받았습니다.


## **6. 한계점 및 해결방안**

기획에 집중해서 이전에 진행한 프로젝트처럼 모델의 성능, 기능을 다루지 못해서 아쉬웠으며 데이터분석의 부족함이 느껴졌던 프로젝트였습니다. 
프로젝트를 발전시 리뷰 크롤링을 다시 하여 NLP분석 위주의 데이터분석을 재진행할 예정입니다.   
