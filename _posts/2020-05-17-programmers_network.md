---
layout: post
title: "프로그래머스 Network"
date: 2020-05-17
excerpt: ""
algorithm: true
comments: true
tag: [코딩테스트, 알고리즘]
---
문제 설명
네트워크란 컴퓨터 상호 간에 정보를 교환할 수 있도록 연결된 형태를 의미합니다. 예를 들어, 컴퓨터 A와 컴퓨터 B가 직접적으로 연결되어있고, 컴퓨터 B와 컴퓨터 C가 직접적으로 연결되어 있을 때 컴퓨터 A와 컴퓨터 C도 간접적으로 연결되어 정보를 교환할 수 있습니다. 따라서 컴퓨터 A, B, C는 모두 같은 네트워크 상에 있다고 할 수 있습니다.

컴퓨터의 개수 n, 연결에 대한 정보가 담긴 2차원 배열 computers가 매개변수로 주어질 때, 네트워크의 개수를 return 하도록 solution 함수를 작성하시오.

제한사항
컴퓨터의 개수 n은 1 이상 200 이하인 자연수입니다.
각 컴퓨터는 0부터 n-1인 정수로 표현합니다.
i번 컴퓨터와 j번 컴퓨터가 연결되어 있으면 computers[i][j]를 1로 표현합니다.
computer[i][i]는 항상 1입니다.
입출력 예
n	computers	return
3	[[1, 1, 0], [1, 1, 0], [0, 0, 1]]	2
3	[[1, 1, 0], [1, 1, 1], [0, 1, 1]]	1

간단히 설명해 나누어져 있는 트리의 개수를 새는 것이다.

인트라넷을 생각했을때 따로 구성된 인트라넷끼리는 서로 연결되어 있지 않은 별도의 네트워크라는 점을 생각해보면 된다.

DFS를 진행하되 트리가 여러개로 나누어져 있기때문에 DFS가 완료되어도 모든 컴퓨터에 대해서 탐색을 완료할 때 까지 탐색을 해야한다.

코드는 다음과 같다.

    #include <string>
    #include <vector>
    #include <algorithm>
    #include <iostream>
    using namespace std;

    vector<int> finish;
    int answer = 0;

    void dfs(int n,vector<vector<int>> computers,int startpoint){
        int i = startpoint;
        for(int j=0;j<n;j++){
            if(i==j)
                continue;
            else{
                if(computers[i][j]==1&&find(finish.begin(),finish.end(),j)==finish.end()){
                    finish.push_back(j);
                    dfs(n,computers,j);
                }
            }
            if(finish.size()==n){
                break;
            }
        }
    }

    int solution(int n, vector<vector<int>> computers) {
        for(int i=0;i<n;i++){
            if(find(finish.begin(),finish.end(),i)==finish.end()){
                finish.push_back(i);
                answer++;
            }
            for(int j=0;j<n;j++){
                //cout<<(find(finish.begin(),finish.end(),j)!=finish.end())<<endl;
                if(i==j)
                    continue;
                else{
                    if(computers[i][j]==1&&find(finish.begin(),finish.end(),j)==finish.end()){
                        finish.push_back(j);
                        dfs(n,computers,j);
                    }
                }
                if(finish.size()==n){
                    break;
                }
            }
        }
        return answer;
    }

<hr>

## References

https://programmers.co.kr/learn/courses/30/parts/12421