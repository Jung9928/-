```C++

#include <iostream>
#include <queue>
#include <vector>

using namespace std;

int vertex = 9;
int visited[9];
vector<int> node[10];

void bfs(int start) 
{
  queue<int> q;
  q.push(start);
  visited[start] = true;
  
  while(!q.empty()) 
  {
    // 큐에 값이 있을 경우 계속 반복 실행
    // 큐에 값이 있다. => 아직 방문하지 않은 노드가 존재한다.
    
    int x = q.front();
    q.pop();
    cout<<x<<" ";
    
    for(int i=0; i<node[x].size(); i++)
    {
      int y = node[x][i];
      if(!visited[y])
      {
        // 방문하지 않았다면
        q.push(y);
        visited[y] = true;
      }
    }
  }
}

int main()
{
  // 1과 2를 연결
  node[1].push_back(2);
  node[2].push_back(1);
  
  // 1과 3을 연결
  node[1].push_back(3);
  node[3].push_back(1);
  
  // 2와 4를 연결
  node[2].push_back(4);
  node[4].push_back(2);
  
  // 2와 5를 연결
  node[2].push_back(5);
  node[5].push_back(2);
  
  // 4와 8을 연결
  node[4].push_back(8);
  node[8].push_back(4);
  
  // 5과 9를 연결
  node[5].push_back(9);
  node[9].push_back(5);
  
  // 3과 6을 연결
  node[3].push_back(6);
  node[6].push_back(3);
  
  // 3과 7을 연결
  node[3].push_back(7);
  node[7].push_back(3);
  
  // 1번 노드부터 bfs 탐색 실행
  bfs(1);
  
  return 0;
}


----------------------------
// 결과 : 1 2 3 4 5 6 7 8 9
----------------------------
```

