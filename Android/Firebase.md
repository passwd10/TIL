## RealTime Database vs Cloud Firestore

1. 데이터 모델
- RealTime database에서는 데이터를 하나의 큰 JSON트리로 저장하기때문에 복잡한 계층적 데이터를 정규화 시켜서 정리하기가 쉽지 않음. 중복데이터가 많이 발생
- Cloud Firestore는 문서와 컬렉션으로 이루어져있음. 문서에는 키-값 쌍이 들어있고, 작은 문서가 많이 모인 컬렉션을 저장하는데 최적화되어 있음. 그래서 NOSQL이지만 SQL처럼 테이블 관리에 용이함. path를 지정하고 데이터를 할당하기만 하면 됨.

2. 쿼리(데이터베이스에 정보를 요청하는 것)
- RealTime database는 쿼리할때 정렬 및 필터링을 할수는 있지만 동시에 조건문을 걸수는 없음. 데이터 정규화가 제대로 이루어지지 않은 데이터베이스라면 불필요하게 큰 데이터까지 매전 가져와야해서 성능저하가 발생.
- Cloud FireStore는 쿼리할때 정렬 및 필터링 조건문을 동시에 사용가능. 쿼리가 얕아서 특정 컬렉션이나 컬렉션이 가지고 있는 문서만 반환하여 불필요한 하위 데이터까지 반환하는 성능문제가 발생하지 않음.

3. 확장성
- Realtime Database의 단일 데이터베이스는 동시 연결이 약 100,000개, 초당 쓰기 약 1,000회 까지 확장됨. 추가로 확장하려면 데이터를 여러 데이터베이스로 샤딩(같은 테이블 스키마를 가진 데이터를 다수의 데이터베이스에 분산하여 저장하는 방법)해야함.
- Cloud Firestore는 샤딩이 필요없이 자동으로 확장이됨. 현재 확장 한도는 동시 연결수 약 1,000,000개, 초당 쓰기 10,000회

4. 가격
- Realtime Database는 용량, 대역폭(다운로드크기)에 대해 주로 과금을 함. 가벼운 데이터이지만 문서에 대한 CRUD작업이 자주 발생하는 앱일 때 유리
- FireStore는 용량, document CRUD 연산 횟수에 따라 과금을 주로 함. 큰단위에 유리