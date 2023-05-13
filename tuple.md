```C++
#include <iostream>
#include <algorithm>
#include <tuple>
#include <vector>

using namespace std;

bool compare(tuple<int, int, int> &a, tuple<int, int, int> &b)
{
  if(get<1>(a) < get<1>(b))
    return get<0>(a);
  return get<0>(a);
}

int main()
{
  int n;
  cin>>n;

  vector<tuple<int, int, int>> team_score;
  for(int i=0; i<n; i++)
  {
    int a, b, c;
    cin>>a>>b>>c;
    
    team_score.push_back(make_tuple(a, b, c));
  }
  
  sort(team_score.begin(), team_score.end(), compare);
  
  for(int i=0; i<team_score.size(); i++)
    cout<<get<0>(team_score[i])<<" / "<<get<1>(team_score[i])<<" / "<<get<2>(team_score[i])<<"\n";
    
  return 0;
}

#### 입력 ####
3
1 2 3
4 5 6
7 9 8
##############

#### 결과 ####
7 / 9 / 8
4 / 5 / 6
1 / 2 / 3
##############
```

