# 자료구조 & 알고리즘 TIL
## Hash
1. Hash의 원리
- 해쉬는 배열의 인덱싱하는 과정이 O(n)이기 때문에 이를 줄이고자 만든 자료구조이다. 기본적으로 Key : Value 형식으로 데이터가 저장된다. 따라서 내가 찾고 싶은 key를 알면 바로 해당하는 Value를 얻을 수 있다는 점에서 복잡도가 O(1)이다.
- 먼저, 특정 키마다 고유한 해쉬 키, 쉽게 말해 암호를 가지고 있다. 특정 키에 대해 해쉬 키를 만들어주는 함수가 해쉬 함수이고, 해쉬 키에 해당하는 배열에 값이 저장되어 있다.
- 해쉬맵(해쉬 테이블)은 기본적으로 자료를 담을 배열이 있어야 한다.
- 해쉬 키가 중복되는 경우를 해쉬 충돌(Collision)이라고 하는데 이때는 해당 키에 데이터를 연결 리스트로 저장을 하거나 해당 키 바로 밑에 비어있는 키에 데이터를 저장하는 방식이 있다. (이 때는 데이터를 Key,Value를 같이 저장한다.)
