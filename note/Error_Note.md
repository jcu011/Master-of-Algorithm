## <Error 정리>

1. Wrong Answer
* 예외 케이스
* DP문제의 경우 기저값(basis) 초기화 오류
* 배열 개수 범위 설정 오류
* 자료형 오버플로우 ex) int범위 벗어남
* 테케가 많은경우 배열or벡터의 초기화가 안됨
* vector<int> v(10); 와 같이 초기화 해놓고 sort(v.begin(), v.end());
* MOD사용시 MOD가 1이 되는경우 -> 모든수%MOD = 0 이기때문에 WA
* 배열 참조 오류 ex) 세그먼트 트리에서 query함수 리턴값으로 (tree배열, arr배열) 둘중 잘못 참조하여 반환
* 연산 우선순위 오류 ex) Bitmask 계산중 오류
* 프로그래머스의 경우 런타임에러도 WA로 나옴.

*****************************************************************************************************************

2. 메모리 초과
* 배열의 잘못된 크기설정
* bfs 방문처리 안함
* 방문처리할 노드가 메모리 제한을 넘어가는 경우 -> Map에 방문한 노드를 저장하여 방문처리
* 스택이용시 스택에 중복 데이터로 인해 스택의 크기가 기하급수적(지수급)으로 늘어날 경우
* 세그먼트 트리에서 min 세그트리 사용할때 INF의 크기를 최대값과 같게 설정하여 메모리초과 (재귀 무한루프)

*****************************************************************************************************************

3. 런타임 에러
* 버퍼 오버플로우 -> 잘못된 배열크기 or 인덱싱 (Index Out Of Range)
* 스택 오버플로우 -> 재귀함수 많이호출 or 함수에 큰변수 선언
* return값이 있는 함수에서 특정 조건에 리턴값이 없는경우 (특히 재귀함수)
* stack 또는 queue에서 empty인데 pop 또는 top,front를 불러오는 경우

*****************************************************************************************************************

4. 시간초과
* 알고리즘개선
* 방문처리 누락 ex) dfs
* 무한루프검사 ex) bfs 큐이용시 (pop안함, pop하고나서 방문처리-> 중복방문)
* 입력 덜 받았는지 확인
* WA이지만 TLE인 경우도 있음 (백준)

*****************************************************************************************************************

