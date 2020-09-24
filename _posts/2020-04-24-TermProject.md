---
title: Term Project
categories:
 - Algorithm
tags:
 - problem
 - c++
---

## 문제

[https://www.acmicpc.net/problem/9466
](https://www.acmicpc.net/problem/9466
)

이번 가을학기에 '문제 해결' 강의를 신청한 학생들은 텀 프로젝트를 수행해야 한다. 프로젝트 팀원 수에는 제한이 없다. 심지어 모든 학생들이 동일한 팀의 팀원인 경우와 같이 한 팀만 있을 수도 있다. 프로젝트 팀을 구성하기 위해, 모든 학생들은 프로젝트를 함께하고 싶은 학생을 선택해야 한다. (단, 단 한 명만 선택할 수 있다.) 혼자 하고 싶어하는 학생은 자기 자신을 선택하는 것도 가능하다.
학생들이(s1, s2, ..., sr)이라 할 때, r=1이고 s1이 s1을 선택하는 경우나, s1이 s2를 선택하고, s2가 s3를 선택하고,..., sr-1이 sr을 선택하고, sr이 s1을 선택하는 경우에만 한 팀이 될 수 있다.
예를 들어, 한 반에 7명의 학생이 있다고 하자. 학생들을 1번부터 7번으로 표현할 때, 선택의 결과는 다음과 같다.

| 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|--------|--------|--------|--------|--------|--------|--------|
| 3 | 1 | 3 | 7 | 3 | 4 | 6 |

위의 결과를 통해 (3)과 (4, 7, 6)이 팀을 이룰 수 있다. 1, 2, 5는 어느 팀에도 속하지 않는다.
주어진 선택의 결과를 보고 어느 프로젝트 팀에도 속하지 않는 학생들의 수를 계산하는 프로그램을 작성하라.

## 입력

첫째 줄에 테스트 케이스의 개수 T가 주어진다. 각 테스트 케이스의 첫 줄에는 학생의 수가 정수 n (2 ≤ n ≤ 100,000)으로 주어진다. 각 테스트 케이스의 둘째 줄에는 선택된 학생들의 번호가 주어진다. (모든 학생들은 1부터 n까지 번호가 부여된다.)
```
2
7
3 1 3 7 3 4 6
8
1 2 3 4 5 6 7 8
```

## 출력

각 테스트 케이스마다 한 줄에 출력하고, 각 줄에는 프로젝트 팀에 속하지 못한 학생들의 수를 나타내면 된다.
```
3
0
```

_ _ _


순열 사이클과 비슷하지만 다르다.
순열 사이클은 서로 다른 점이 같은 점을 가르킬 수 없지만 TermProject는 가능하다.

**핵심포인트**
반복 수열 풀이법을 응용한다.
DFS에 단계를 부여한다.

**풀이법**
1. DFS함수(노드,count,단계) 구현 : 반복 수열 풀이법을 이용하여 시작점에서 구할 수 있는 반복 수열을 계산한다. (주의점: 같은 단계=같은 시작점에서 시작한 수들만 짝이 될 수 있다. ->같은 단계에서 방문했던 점을 다시 방문할 경우에만 성공!)
2. 그래프 입력받기 node[i]=i점이 가르키는 점
3. 방문하지 않았으면 DFS함수 호출
4. 다음 테스트 케이스를 위해 변수 초기화

## 코드

```c++
#include <iostream>
#include <cstring>

using namespace std;

int team[100001];
int check[100001];
int stages[100001]; //dfs단계를 나타냄
int stage=0;
int success=0; //성공한 학생들 수

void dfs(int student, int count,int stage){
    if(check[student]>0 && stages[student]==stage){ //같은 단계에서 이미 방문한 친구일경우
        success+=count-check[student];
        return;
    }
    if(check[student]==0){ //한번도 방문하지 않은 친구
        check[student]=count;
        stages[student]=stage;

        dfs(team[student],count+1,stage);//짝하고싶은애를 찾아감

    }
    //다른 단계에서 이미 방문한 친구 일경우 패스한다.
}
int main()
{
    int t;
    cin>>t;

    while(t--){
        int num;//학생수
        cin>>num;
        for(int i=1;i<=num;i++){//가르키는 학생 넣음
            cin >> team[i];
            if(i==team[i]){//자기자신을 가르킬경우
                success++;
                check[i]=-1;

            }
        }
        for(int i=1;i<=num;i++){//체크되지않은 친구 dfs소환
            if(check[i]==0){
                dfs(i,1,stage++);

            }
        }
        cout<<num-success<<"\n";
        success=0;
        stage=0;
        for(int i=1;i<=num;i++){
            team[i]=0;
            check[i]=0;
            stages[i]=0;
        }
    }

    return 0;
}
```
