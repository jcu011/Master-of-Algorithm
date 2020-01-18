# **< Master-of-Algorithm >**
- 마크다운 문법 참고

[MD Grammer](https://simhyejin.github.io/2016/06/30/Markdown-syntax/#blockquotes "마크다운 문법");

- 알고리즘PS의 시작

[알고리즘 길라잡이](https://ryute.tistory.com/m/33 "류트님 블로그")

[알고리즘 공부순서](https://baactree.tistory.com/14 "박트리님 블로그")


- # <div id="0">목차</div>
1.  [VS Code 단축키, 사용법](#1)
2.  [C++ default main code](#2)
3.  [C++ References](#3)
4.  [cmath 헤더](#4)
5.  [string 헤더](#5)
6.  [vector 헤더](#6)
7.  [Linked List 사용예시](#7)
8.  [STL의 함수들](#8)
9.  [오류대처](#9)
10. [알고리즘 & 자료구조 코드](#10)
*********************************************************************************************************

# <div id="1">VS Code 단축키, 사용법</div>
~~~
코드러너 실행 : ctrl + alt + N
검색 : F1 또는 ctrl + shift + p
설정 : ctrl + ,
git소스제어 : ctrl + shift + g
코드정렬 : shift + alt + f
o -> x로 바뀌면 저장 된거.

한줄삭제 :  shift + Delete
모든 항목 이름변경 : Ctrl + F2
~~~

*********************************************************************************************************


# <div id="2">C++ default main code</div>
~~~cpp
#include <bits/stdc++.h>
#define rep(i,x,n) for(int i=x; i<n; i++)
using namespace std;

int main() {
	ios_base::sync_with_stdio(false); cin.tie(nullptr);
	int N, M;
	cin>>N>>M;
	vector<int> arr(N+1);
    rep(i, 0, N) cin>>arr[i]; // i=0부터 N-1까지 (idex)
}
~~~
*********************************************************************************************************


# <div id="3">C++ References</div>
~~~
C++이 제공하는 헤더에서 함수들에 대한 상세한 정보 확인가능
http://www.cplusplus.com/reference/algorithm/

~~~
*********************************************************************************************************

# <div id="4">cmath 헤더</div>
~~~cpp
abs(val); // 절대값
pow(val,n); // val의 n제곱
ceil(val);  // 올림
floor(val); // 내림
round(val); // 반올림
//round함수 오버라이딩 (pos이용하여 반올림 자릿수 설정)
double round(double value, int pos )
{
	double temp = 0;

	temp = value * pow( 10.0, pos );
	temp = floor( temp + 0.5 );
	temp = temp * pow( 10.0, -pos );

	return temp;
} 

~~~
*********************************************************************************************************

# <div id="5">String 헤더</div>
~~~
< string 클래스 정리 (append, length, at, insert, replace, finde, compare) >
  1. String 변수 초기화방법
    * string str1 = "Hello "; // 초기화방법
    * string copys(str1); // 이렇게 복사가능 (깊은복사)
    * cin>>str1>>str2; cin만 사용시 공백 구분하여 입력받음
    * str1 = str2 + str3; // 연산자로 문자열 붙이기 가능
    * getline(cin, str1); 
        - 공백문자 포함 한번에받기. c언어의 gets(str1)와 같은함수
        - 정확히는 -> getline(입력방식, 입력버퍼시작주소, 딜리미터)   //딜리미터 : 구분문자,
        - 버퍼는 여기공부 : https://kks227.blog.me/60204963264

  2. 문자열 확장  : str1.append("World"); // c의 strcat()과 비슷, str1 += "World"; // 위와 같은 코드
  3. 문자열길이   : str1.length(); // 문자열 길이출력
  4. 문자열인덱싱 : str1.at(3) == str1[3]
  5. 문자열삽입   : str1.insert(6, "Happy "); //str1이 "Hello World"라면, "Hello Happy World" 가 str1에 저장됨
  6. 문자열대체   : str1.replace(0, 5, "Bye"); // 0~5인덱스까지 삭제후 Bye로 대체.
  7. 문자열검색   : str1.find("World"); // 탐색문자열이 있으면 그 시작 인덱스를 반환. 없으면 -1반환
  8. 문자열비교   : str1.compare(str2); // 같으면 0 str1이 더 작으면(우선순위높으면) -1, 크면 1반환
~~~
*********************************************************************************************************


# <div id="6">Vector 헤더</div>
~~~
  https://blockdmask.tistory.com/70
  * capacity는 capacity의 크기 이상의 데이터가 들어오면 capacity의 기존메모리 x 2로 capacity가 증가함.
    
  1. vector<타입> v(n, initnum); 또는 ()안에 벡터를 넣어서 복사가능
  2. v.at(idx) 와 v[idx] 의 차이점 -> []가 더 빠르지만, at()은 인덱스 범위(range)점검하여 벗어나면 예외날림(안전).
  3. v.assign(5, 2); -> 2의 값으로 5개 원소 할당
  4. v.front(); -> 첫번째 원소 참조(반환)
  5. v.clear(); -> 모든원소 제거
  6. v.push_back(7); -> 마지막 원소뒤에 7삽입
  7. v.pop_back(); -> 마지막 원소 제거
  8. v.begin(); -> 첫번째 원소 가리킴(참조아님) : iterator와 사용 , *첫번째 원소의 iterator 반환해줌
  9. v.end(); -> 마지막원소의 다음 가리킴(참조아님) : iterator와 사용, *마지막 원소가아닌 그다음항의 iterator 반환
  10. v.rbegin(); v.rend(); -> 역방향 이터레이터용 주소 반환 함수
  11. v.reserve(n); -> n개원소를 저장할 위치를 예약함 (미리 동적할당)
  12. v.resize(n); -> size를 n으로 변경. size가 더 커졌을경우는 default값인 0으로 변경 (size는 원소의 개수이므로)
  13. v.resize(n,m); -> size를 n으로 변경하고 더 커졌을경우 m으로 변경
  14. v.size(); -> 원소의 개수 리턴, 2차원으로 생성해도 행개수 출력가능함
  15. v.capacity(); -> 할당된 공간 리턴
  16. v2.swap(v1); -> v1과 v2를 완전 스왑. (즉, capacity를 바꿈)
  17. v.insert(2, 3, 4); -> 2번째 위치에 3개의 4값을 삽입 (뒤의 값들은 뒤로밀림)
  18. v.insert(2, 3); -> 2번째 위치에 3삽입, 삽입한 곳의 iterator를 반환
  19. v.erase(iter); -> iter가 가리키는 원소제거. 범위제거시 인자를 2개넣기. https://blockdmask.tistory.com/75 참고
  20. v.empty(); -> vector가 비었으면 리턴 true (size가 0. capacity와는 상관없는것)
~~~
*********************************************************************************************************


# <div id="7">Linked List With Vector and Class</div>
~~~cpp
// foreach도 포함 !
#include <iostream>
#include <vector>
using namespace std;

class Node {
   private:
    int num;
    int sum;
    int fac;

   public:
    Node(int n) : num(n) {
        sum = sumFunc(n);
        fac = facFunc(n);
    }
    // Function Prototype
    int sumFunc(int);
    int facFunc(int);
    int getNum();
    int getSum();
    int getFac();
};

int main() {
    ios_base::sync_with_stdio(false); cin.tie(nullptr);
    vector<Node*> n;
    int N;
    cin >> N;

    // Node초기화. 1~N까지 인덱스에따라 num, sum, fac를 생성자를 이용하여 초기화
    for (int i = 1; i <= N; i++) {
        n.push_back(new Node(i));
    }

    vector<Node*>::iterator iter = n.begin();
    iter++;  // 0 -> 1번 노드로 이동
    cout << "<Testing of iterator>" << endl;
    cout << "print : " << (*(iter - 1))->getNum() << endl;  // 1출력
    cout << "print : " << (*iter)->getNum() << endl;        // 2출력
    cout << "print : " << iter[1]->getNum() << endl;        // 3출력
    cout << "print : " << (*iter++)->getNum() << endl;      // 2출력
    cout << "print : " << (*++iter)->getNum() << endl;      // 4출력
    cout << endl;

    int M;
    cin >> M;
    // M만큼 수를 받고 그 수가 node에 있으면 삭제
    while (M--) {
        if (n.empty()) break;
        int searchIdx;
        cin >> searchIdx;
        for (vector<Node*>::iterator it = n.begin(); it != n.end(); it++) { // iterator 변수 생성방법, 종료조건
            if (searchIdx == (*it)->getNum()) {
                n.erase(it);
                break;
            }
        }
    }

    // iterator이용하여 Node 모두 출력
    cout << "<Information of Nodes>" << endl;
    for (auto it = n.begin(); it != n.end(); it++) { // auto 자료형으로 컴파일러가 알아서 iterator형으로 변수 생성해줌.
        cout << "Num : " << (*it)->getNum() << ", Sum : " << (*it)->getSum() << ", Fac : " << (*it)->getFac() << endl;
    }
    cout<<"\n";

    // foreach문 이용하여 Node 모두 출력
    cout << "<Information of Nodes by foreach>" << endl;
    for(Node* it : n){
        cout << "Num : " << it->getNum() << ", Sum : " << it->getSum() << ", Fac : " << it->getFac() << endl;
    }

}

// Function Definition
int Node::facFunc(int n) {
    int result = 1;
    for (int i = n; i > 0; i--) {
        result *= i;
    }
    return result;
}
int Node::sumFunc(int n) {
    int result = 0;
    for (int i = 1; i <= n; i++) {
        result += i;
    }
    return result;
}
int Node::getNum() {
    return num;
}
int Node::getSum() {
    return sum;
}
int Node::getFac() {
    return fac;
}

~~~
*********************************************************************************************************


# <div id="8">STL의 함수들 사용예시</div>

* **<div id="8.0">목록</div>**
> 1. [find()](#8.1)
> 2. [binary_search()](#8.2)
> 3. [lower_bound(), upper_bound()](#8.3)
> 4. [sort()](#8.4)
> 5. [includes()](#8.5)
> 6. [unique()](#8.6)

1. **<div id="8.1">find() 함수</div>**
~~~cpp
auto it = find(arr.begin(), arr.end(), val);
// iterator 로 반환

/*
 <Algo find 속도>
Binary Tree 기반 자료구조에서는 O(logn)
Hashing 으로 관리한다면 O(1)
Array 기반 자료구조는 O(n)
*/
~~~

2. **<div id="8.2">binary_search() 함수</div>**
~~~cpp
sort(arr.begin(), arr.end());
// 이진탐색전 정렬필수
auto result = binary_search(arr.begin(), arr.end(), val);
// bool형 반환

~~~

3. **<div id="8.3">lower_bound(), upper_bound() 함수</div>**
~~~cpp
vector<int> v = { 1,2,4,4,4,5,7,7,7,9,10 };

// lower_bound : value보다 작지 않은 값 중 첫번째 iterator를 반환
auto l = lower_bound(v.begin(), v.end(), 4);
cout << "4의 처음 위치 : " << (l - v.begin()) << endl;
// 2 출력 (index)


// upper_bound : value보다 큰 값 중 첫번째 iterator를 반환
auto u = upper_bound(v.begin(), v.end(), 4);
cout << "4보다 큰 값 중 처음 위치 : " << (u - v.begin()) << endl;
// 5 출력 (index)

/* 
lower_bound값과 upper_bound값의 차이를 통해 value의 갯수를 구할 수 있다.
위의 결과에서 u - l = 3
4의 개수는 3개.
*/

~~~

4. **<div id="8.4">sort() 함수</div>**
~~~cpp
//예시 1) 시작주소 ~ (끝주소 + 1) 로 지정하여 sort
sort(str.begin(), str.end());

//예시 2) 일반 자료형
sort(v.begin(),v.end(),greater<int>());
sort(v.begin(),v.end(),less<int>());

//예시 3) stable_sort() : 구조체 or 클래스
bool cmp(const Point&, const Point&); // 프로토타입
sort(v.begin(),v.end(),cmp); // 함수는 포인터로 받음
bool cmp(const Point &p1, const Point &p2){ // 오름차순정렬 되도록 설계한것.
    if(p1.x < p2.x)
        return true;
    else if(p1.x == p2.x)
        return p1.y < p2.y;
    else
        return false;
}

~~~

5. **<div id="8.5">includes() 함수, (less,greater) 클래스</div>**

사실 less는 따로 설정 안해주어도됨. 기본으로 오름차순으로 비교하기때문.
~~~cpp
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main(void)
{
    int N; cin>>N;
    vector<int> v1;
    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);
    
    vector<int> v2;
    v2.push_back(10);
    v2.push_back(40);
    v2.push_back(20);
   
    vector<int> v3;
    v3.push_back(10);
    v3.push_back(20);
    v3.push_back(60);

    vector<int> v4;
    v4.push_back(40);
    v4.push_back(20);
    v4.push_back(10);
    
    // 정렬을 하고 난 후 includes로 비교해야함. 따라서 아래 코드는 not으로 뜸.
    // bool형 반환
    if(includes(v1.begin(), v1.end(), v2.begin(), v2.end()))
        cout << "v2 is part of v1" << endl;
    else
        cout << "v2 is not part of v1" << endl;
    // v3가 v1에 포함되지 않음 (60은 v1에 없음)
    if(includes(v1.begin(), v1.end(), v3.begin(), v3.end()))
        cout << "v3 is part of v1" << endl;
    else
        cout << "v3 is not part of v1" << endl;
    

    //정렬 기준을 greater<int> 설정 ( 내림차순정렬 )
    sort(v1.begin(), v1.end(), greater<int>());
    sort(v2.begin(), v2.end(), greater<int>());
    for(int num: v1){
        cout<<num<<" ";
    } cout<<"\n";
    for(int num: v2){
        cout<<num<<" ";
    } cout<<"\n";
    //비교 기준을 greater<int> 설정 ( 내림차순으로 포함관계확인 )
    if(includes(v1.begin(), v1.end(), v2.begin(), v2.end(), greater<int>()))
        cout << "Using greater class : v2 is part of v1" << endl;


    //정렬 기준을 less<int> 설정 ( 오름차순정렬 )
    sort(v1.begin(), v1.end(), less<int>());
    sort(v4.begin(), v4.end(), less<int>());
    for(int num: v4){
        cout<<num<<" ";
    } cout<<"\n";
    for(int num: v1){
        cout<<num<<" ";
    } cout<<"\n";
    //비교 기준을 less<int> 설정 ( 오름차순으로 포함관계확인 )
    if(includes(v1.begin(), v1.end(), v4.begin(), v4.end(), less<int>()))
        cout << "Using less class : v4 is part of v1" << endl;

    return 0;
}

~~~

6. **<div id="8.6">unique() 함수</div>**

~~~cpp
#include<iostream>
#include<algorithm>
#include<vector>
using namespace std;

int main()
{
    ios_base::sync_with_stdio(false); cin.tie(nullptr);
    int N; cin>>N;
    vector<int> v = { 1,2,4,4,4,5,7,7,7,9,10 };
    auto n = unique(v.begin(),v.end());
    // uniqe함수는 중복제거후 마지막항 다음의 원소(필요없는...)의 iterator(주소)를 반환해줌.
    // 따라서 아래코드로 바로 삭제가능.
    v.erase(n,v.end());
    
    //결과 확인
    for(int num: v){
        cout<<num<<" ";
    }
}

~~~


*********************************************************************************************************


# <div id="9">오류대처</div>

- **오류 미리대처하기**

 1. c++ 입출력함수 속도
 
ios_base::sync_with_stdio(false); cin.tie(nullptr);

[참고블로그](https://blog.naver.com/acelhj/221316329745)
~~~
  * sync_with_stdio(false)는 c++ iostream 버퍼와 c의 stdio 버퍼의 동기화에 대한 함수
    - false설정시 동기화, iostream만의 버퍼를 만듬
  * cin.tie(nullptr); : 없으면 무조건 cin이랑 cout 들어올 때 버퍼 비움.
~~~
 2. 문자열 함수인자로 받을때는 &을 꼭 이용 ( call by reference )
 3. int값을 함수인자로 받을때는 그냥 ( call by value )가 좋음
 4. endl 은 사용하지말자 !! (느림)
~~~
endl은 '\n'을 출력하고 강제로 버퍼를 비움.

출력을 하던 도중에 입력을 받을 경우 버퍼를 비워야 하는게 맞지만,
예를들어 11725문제 경우는 최대 10만개의 라인을 출력만 하므로 (입력을 저장한 후 bfs계산하는 코드 작성함)
endl을 쓰면 불필요하게 버퍼를 비우므로 매우 느려짐.

따라서 endl 대신 \n을 출력하여 해결함.
~~~
5. 함수안에서 배열을 정의하지 말것 ! -> 스택공간을 차지하기때문
6. 재귀함수는 1만번이상 호출하지 않는것이 좋음 ( 스택계산이 어렵기때문 , 느림 )
7. 테스트케이스 입력하는 방법
~~~
 최소,최대 입력 -> 끝?값들 (메모리 사이즈 초과확인) -> 0, 음수, 최솟값, 최댓값...
 모두같은값 입력 -> 중복값, 중복값중 끝 값...
 1,2,3,4... 같은 연속수(규칙성있는 수) 입력
 랜덤함수써서 입력받기
 
 등등 꼬아서 입력해보기
~~~

- **오류 대처방안**
1. 시간초과
~~~
* 무한루프검사
* 입력 덜 받았는지 확인
* 알고리즘개선
~~~

2. 런타임오류
~~~
* 버퍼 오버플로우 -> 배열크기 작게잡음 or 인풋과 배열크기 불일치
* 스택 오버플로우 -> 재귀함수 많이호출 or 함수에 큰변수를 선언함
~~~

3. 틀렸습니다
~~~
* 검사도중 오류난경우 : 일부케이스만 정답이므로 <예외> 케이스 생각하기
* 배열 최대범위초과 : long long을 쓰기
~~~

4. 디버깅

디버깅은 최후의 수단 !!!
*********************************************************************************************************

# <div id="10">알고리즘 & 자료구조 코드</div>
1. DFS & BFS
~~~
~~~
2. 탐색
~~~
~~~
3. 최단경로
~~~
~~~
4. 세그먼트 트리
~~~
~~~

*********************************************************************************************************


- [목차로 이동](#0)