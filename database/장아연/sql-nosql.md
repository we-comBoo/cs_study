## RDBMS

### 정의
관게형 데이터 베이스 관리 시스템

### 특징
1. 정해진 스키마에 따라 테이블이 구성됨
2. 테이블끼리 관계를 가짐
3. transcation을 사용함
4. 인덱스 사용
5. 다중 작업 지원
6. 데이터 백업
7. 데이터 복구

<br/>
* 스키마 : 데이터베이스에 사용되는 전체 데이터 구조 정의하는 개체 <br/>
* 테이블 : 데이터를 구성하는 가장 기본적인 단위

## SQL

### 정의
RDBMS에서 사용되는 표준 질의언어

### 분류
1. DDL : Data Definition Language
* 생성 - create
* 수정 - alter
* 초기화 - truncate
* 삭제 - drop

2. DML : Data Manipulation Language
* 생성 - insert
* 조회 - select
* 갱신 - update
* 삭제 - delete

3. DCL : Data Control Language
* 권한 부여 - grant
* 권한 회수 - revoke

4. TCL : Transcation Control Language
* 커밋 - commit
* 롤백 - rollback


## NoSQL

### 등장 배경
1. RDBMS 확장의 한계


### 특징
1. 유연한 데이터 모델 
* 고정된 스키마를 갖지 않음
* 데이터 모델 변화에 대한 용이한 대응
* 어플리케이션 단에서 데이터 구조에 맞게 매핑할 필요 없음
* 다양한 데이터 모델 - column, graph, key:value, document, 
2. 저렴한 비용
* 오픈소스 제품 많음
* 노드 추가를 통한 데이터 가용성을 보장하기 때문에 HW 비용이 상대적으로 낮음
3. 분산 시스템

### BASE
1. 기본적 가용성 - Basically Available
* 일부 노드에서 실패하더라도 적절한 replication과 분산 시스템을 통한 전체적인 시스템 가용성 유지
2. Soft State
* 데이터 베이스가 능동적으로 상태를 조정해 데이터 일관성 유지
* 분산 시스템에서 발생하는 네트워크 지연, 노드 간 통신 문제로 데이터 베이스 상태는 시간에 따라 가변적임
4. Eventually Consistent
* 데이터 일관성이 모든 노드에서 즉시 유지되지 않을 수 있지만, 일정 시간 내 결국 데이터 일관성이 유지됨


