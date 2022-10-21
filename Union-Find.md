#### Union-Find (C++) ####
```C++
#include <cstdio>
#include <iostream>

using namespace std;

// 부모 노드 찾는 함수
int getParent(int parent[], int x)
{
  if(parent[x] == x)
    return x;
    
  return parent[x] = getParent(parent, parent[x]);
}

// 두 부모 노드를 합치는 함수
int unionParent(int parent[], int a, int b) 
{
  a = getParent(parent, a);
  b = getParent(parent, b);
  
  // 작은 값을 부모 노드로 선택
  if(a < b) 
  {
    parent[b] = a;
    return a;
  }
  else 
  {
    parent[a] = b;
    return b;
  }
}

// 같은 부모를 가지는지 확인
bool findParent(int parent[], int a, int b) 
{
  a = getParent(parent, a);
  b = getParent(parent, b);
  
  if(a == b)
    return true;
  return false;
}

int main()
{
  int parent[11];
  
  for(int i=1; i<=10; i++)
    parent[i] = i;
    
  unionParent(parent, 1, 2);
  unionParent(parent, 2, 3);
  unionParent(parent, 3, 4);
  unionParent(parent, 5, 6);
  unionParent(parent, 6, 7);
  unionParent(parent, 7, 8);
  unionParent(parent, 9, 10);
  
  // 결과 확인
  for(int i=1; i<=10; i++)
    cout<<"node : "<<i<<" || parent : "<<parent[i]<<"\n";
    
  cout<<"1과 5는 연결 되어있나? : "<<boolalpha<<findParent(parent, 1, 5)<<boolalpha<<"\n";
  cout<<"1과 3은 연결 되어있나? : "<<findParent(parent, 1, 3)<<"\n";
  cout<<"5와 10은 연결 되어있나? : "<<findParent(parent, 5, 10)<<"\n";
  
  return 0;
}
```

#### Union-Find (JAVA) ####
```JAVA
public class Main
{
	private static int n;
    private static int[] parents;

    public static int getParent(int[] parents, int x) {
        if (parents[x] == x) {
                return x;
        }
        int parent = getParent(parents, parents[x]);
        return parent;
    }

    public static void unionParent(int[] parents, int x, int y) {
        x = getParent(parents, x);
        y = getParent(parents, y);

        // 더 작은 값으로 부모 노드 설정
        if (x < y) {
            parents[y] = x;
        } else {
            parents[x] = y;
        }
    }

    public static boolean isSameParent(int[] parents, int x, int y) {
        boolean result = false;
        if (parents[x] == parents[y])
            result = true;
        return result;
    }

    public static void main(String[] args) {
        n = 10;
        parents = new int[n + 1];
        // 값 초기화 및 노드 연결 전
        System.out.println("< 연결 전 >");
        for (int i = 1; i <= n; i++) {
            parents[i] = i;
            System.out.print(parents[i] + " ");
        }
        System.out.println();System.out.println();

        // 노드 연결
        unionParent(parents, 1, 2);
        unionParent(parents, 2, 3);
        unionParent(parents, 3, 4);
        unionParent(parents, 5, 6);
        unionParent(parents, 6, 7);
        unionParent(parents, 7, 8);
        unionParent(parents, 9, 10);    

        // 연결 후
        System.out.println("< 연결 후 >");
        for (int i = 1; i <= n; i++) {
            System.out.print(parents[i] + " ");
        }
        System.out.println();

    }
}

```
