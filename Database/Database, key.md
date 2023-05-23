# 데이터 베이스 종류와 특징 

DB는 크게 RDB, NoSQL로 분류되고 RDB에는 mysql, oracle 등이있고
noSQL은 몽고디비, 카산드라 등이 있습니다
이외에도 더많이 존재합니다.

특징은 아래와 같습니다.

- DB는 실시간서비스 되므로 실시간으로 접근할수있다는 특성이있다.

- DB상태는 계속 변경되고 항상 최신의 데이터를 유지하는 특성이있다.

- 다수의 사용자가 동시에 같은 내용의 데이터를 이용할수있어야한다.

- 사용자가 요구하는 데이터 내용으로 데이터를 찾는 특성이있다. 


# 키 종류와 특징 

- 슈퍼키: 유일성을 만족하는키 (학번+이름, 주민번호+학번)

- 복합키 : 2개이상의 속성을 사용한키

- 후보키: 유일성 ,최소성을 만족하는 키

- 기본키 : NOT NULL, 유일해야한다.

- 대체 키 : 후보키중 기본키가 아닌키

- 외래키 : 테이블간 기본키를 참조하는 속성 , 테이블간 관계를 나타내기 위해 사용된다


### 데이터 구조가 자주변하는 데이터를 저장하기위해 RDB, NOSQL중 어떤것이 더 좋을까 

- RDBMS는 스키마를 미리정의하고 데이터타입도 정의하기때문에 구조화된 데이터를 저장하기에 좋고 NOSQL은 데이터 구조에 국한되지않고 데이터를 쉽게 분산저장할수있기때문에 NOSQL이 더 적절하다


### 슈퍼키, 후보키의 관계를 말해주세요

슈퍼키는 유일성을 만족하고, 후보키는 유일성, 최소성을 만족한다.
슈퍼키에서 최소성을 만족하면 후보키이다.

### Q) 외래키에 null이 들어갈수있나?
네 들어갈수있습니다. 그러나 일반적으로 허용하지않습니다. 
최대한 지양해야 참조무결성을 지키는데 좋습니다.



### Q) nosql에 데이터가 어떻게 저장되는지 설명해주세요

- Key-value 모델 : Object, JSON 자료형 형식으로 데이터를 쉽게쉽게 저장, 출력이 가능(가장 심플)

- json Document 모델 : 테이블 대신 Collection이라는 문서 기반으로 데이터 분류, 저장

- Graph 모델 : 데이터를 노드의 형태로 저장하고 노드간의 흐름 or 관계를 저장할 수 있음


### Q) 로그같은걸 남길때 NOSQL에서 어떤구조를 사용하는게 좋을까?
https://kciter.so/posts/about-mongodb
https://stackoverflow.com/questions/10525725/which-nosql-database-should-i-use-for-logging
https://www.quora.com/Which-NoSQL-database-is-best-for-machine-log-data

https://www.infoworld.com/article/3263773/how-to-choose-the-right-nosql-database.html

column model? document model? 

> #### Q) 유일성과 최소성의 의미?

유일성: 유니크한 키값으로 하나의 키값으로 투플을 유일하게 식별할수있는 성질

최소성: 키를 구성하는 속성중 필요한 속성들로만 최소로 구성하는 성질

> #### Q) 복합키는 최소성을 만족하나?

만족 할수도있고, 안할수도있다. 
관련자료는 찾기힘들었다. 


### Q) nosql과 RDB의 차이점 

- nosql은 트랜잭션을 지원하지않고 ACID성질도 가지고있지않다.
- nosql은 테이블구조에 제약을 받지않아서 쉽게 분산저장할수있다.
- RDB는 스키마로 인해 데이터 중복이 없기때문에 update가 많을때 유리할수있다.
- nosql은 대량의 데이터를 빠르게 입출력할때 적합할수있다.

> #### Q) CAP이론에 대해 설명해주세요

분산 DB의 세가지속성인 일관성(Consistency), 가용성(Availability), 분리 내구성(Partition tolerance) 을 나타낸다. 

- Consistency(일관성)
  - 모든 노드가 같은시간에 같은 데이터를 보여줘야한다는 의미
  - 쓰기동작이 완료된후 발생하는 읽기동작은 마지막으로 쓰여진 데이터를 리턴해야한다는걸 의미한다.
  
- Availabilty(가용성)
  - 특정 노드가 장애나도 서비스가 가능해야한다
  - read,write등은 항상 성공적으로 리턴되어야한다

- Partitions Tolerance(분리 내구성)
  - 노드간에 통신문제가 생겨 메시지를 주고받지 못하더라도 동작해야한다.
  - Availabilty는 특정 노드가 장애가 발생한상황이라면 해당특성은 노드의 상태는 정상이지만 네트워크 등의 문제로 연결이 끊어진 상황에대한 이야기다. 


> #### Q) DBMS가 무엇인가?

- DB를 관리하는 시스템
- 데이터를 계층또는 탐색 형식으로 저장한다
- 파일시스템을 사용해 저장한다. 
- 테이블간 관계가 없다
- 데이터에대한 보안을 제공하지않고, 정규화를 수행할수없어 데이터의 높은 중복성을 가질수있다.