## BFS (C++)
```C++
#include <iostream>
#include <vector>

using namespace std;

int vertex = 9;
int visited[9];
vector<int> node[10];

void dfs(int start)
{
  if(visited[start])
    return;         // 방문한 경우 바로 빠져나옴
    
  visited[start] = true;    // 방문
  cout<<start<<" ";
  
  for(int i=0; i<node[start].size(); i++)
  {
    int x = node[start][i];
    dfs(x);
  }
}

int main()
{
  // 1과 2를 연결
  node[1].push_back(2);
  node[2].push_back(1);
  
  // 1과 3를 연결
  node[1].push_back(3);
  node[3].push_back(1);
 
  
  // 2와 3을 연결
  node[2].push_back(3);
  node[3].push_back(2);
  
  
  // 2와 4를 연결
  node[2].push_back(4);
  node[4].push_back(2);
  
  
  // 2와 5를 연결
  node[2].push_back(5);
  node[5].push_back(2);
  
  
  // 4와 8을 연결
  node[4].push_back(8);
  node[8].push_back(4);
  
  
  // 5와 9를 연결
  node[5].push_back(9);
  node[9].push_back(5);
  
  
  // 3과 6을 연결
  node[3].push_back(6);
  node[6].push_back(3);
  
  
  // 3과 7을 연결
  node[3].push_back(7);
  node[7].push_back(3);
  
  // 1번 노드부터 dfs 탐색 실행
  dfs(1);
  
  return 0;
}
```

// 결과 : 1 2 3 6 7 4 8 5 9 
