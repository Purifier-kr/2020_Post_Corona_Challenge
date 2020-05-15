# 2020_Post_Corona_Challenge
2020 포스트 코로나 챌린지 프로젝트

### 1. DATA 폴더: 프로젝트 관련 data   
- 주최측 제공 데이터( 기사, 로밍 데이터)는 저작권에 의해 업로드가 불가합니다.  
- 일일 입국자 데이터(항공정보포탈시스템: http://www.airportal.go.kr/)  
- 해외 코로나 확진자 발생 데이터 (질병관리본부 보도자료: http://www.cdc.go.kr/)  
- 국내 해외 유입 확진자 데이터(코로나바이러:스 http://ncov.mohw.go.kr/)

### 2. Src 폴더: 프로젝트 관련 src code  
#### <전처리>  
- A.뉴스 데이터
- B.해외 신규 확진자 데이터  
- C.해외 입국자 데이터 
- D.로밍 데이터  
- E.국내 해외유입  확진자 수 데이터  
- F. (B)-> 대륙별 신규 확진자(백만명 당)  
#### <NLP 모델링>  
- LDA를 통한 Topic 추출:  
0번째 Topic: 0.020*"death" + 0.012*"confirm" + 0.011*"ministry" + 0.010*"test" + 0.010*"minister" +...  
1번째 Topic: 0.019*"virus" + 0.012*"death" + 0.009*"world" + 0.008*"outbreak" + 0.008*"spread" +...  
2번째 Topic: 0.061*"VIRGINIA" + 0.031*"test" + 0.022*"trump" + 0.017*"NEWYORK" + 0.016*"death" + 0.016*"US" +...  
3번째 Topic: 0.077*"china" + 0.031*"chinese" + 0.023*"wuhan" + 0.019*"province" + 0.013*"patient" +...   
4번째 Topic: 0.020*"patient" + 0.012*"disease" + 0.010*"drug" + 0.010*"SARS" + 0.010*"study" + 0.009*"covV" +...  
5번째 Topic: 0.018*"test" + 0.014*"hospital" + 0.013*"care" + 0.013*"patient" + 0.012*"home" + 0.008*"positive" +...  
6번째 Topic: 0.014*"epidemic" + 0.011*"control" + 0.011*"medical" + 0.009*"prevention" + 0.008*"public" +...  
7번째 Topic: 0.011*"government" + 0.009*"pandemic" + 0.006*"lockdown" + 0.005*"business" + 0.005*"food" +...  
#### <Feature Engineering>  
  - 상관관계 확인  
  - lag 1~14 까지 주어서 모든 경우의 수를 피쳐화  
  - rolling을 사용하여 target값의 트렌드를 피쳐로 사용  
#### <모델링>  
  - Train:  
미주: america_train.pkl  
유럽: europe_train.pkl  
중국 외 아시아: asia_train.pkl  
- Test:  
미주: america_test.pkl  
유럽: europe_test.pkl  
중국 외 아시아: asia_test.pkl  

- 활용 모델:  
XGBoosting( x )  
GradientBoosting( x )  
RandomForest( o )  
