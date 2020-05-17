---
layout: post
title: "프로그래머스 target number"
date: 2020-05-17
excerpt: ""
algorithm: true
comments: true
tag: [코딩테스트, 알고리즘]
---
# DFS
프로그래머스의 DFS/BFS의 최하 문제인 target Number 문제이다.

사실 어려운 문제는 아니었으나 처음엔 이게 왜 DFS인지 이해를 못했다..

그러던 와중에 그래프를 그려봤더니 왜 인지 알아냈다.

첫 합계를 0으로 시작하여 각 숫자별로 +와 -로 나눠 트리를 그려보면 이진트리가 나타난다.

이 경우에는 트리의 끝 점까지 가야해서 DFS로 풀어야한다.

![장고 이미지](/assets/img/post_img/targetNum.png)

대략 위와 같은 이미지인데 대충..알아 보면 될것 같다..

저런식으로 가장 끝 노드까지 탐색을 해야하기 때문에 DFS로 구현해야 한다.

막상 코드를 보면 굉장히 간단하다. 재귀 함수를 이용하여 구현하면 된다.

    #include <string>
    #include <vector>
    #include <algorithm>
    #include <iostream>

    using namespace std;

    int answer = 0;

    void dfs(vector<int> numbers,int sum,int count,int targetNum){
        if(numbers.size()<=count&&(count!=-1)){
            //cout<<sum<<endl;
            if(targetNum==sum){
                answer++;
                return;
            }
            return;
        }
        dfs(numbers,sum+numbers[count],count+1,targetNum);
        dfs(numbers,sum-numbers[count],count+1,targetNum);
    }

    int solution(vector<int> numbers, int target) {
        dfs(numbers,0,0,target);
        return answer;
    }

