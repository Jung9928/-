```C++
#include <iostream>
#include <algorithm>
#include <sstream>
#include <queue>
#include <map>
#include <set>
#include <cstdio>
#include <vector>

using namespace std;

int main()
{
    //string str = "Bank of Korea. Bank of America.";
    //vector<string> result;
    
    vector<string> dates = {
        "2023-05-01 12:38:00"
        , "2023-05-02 03:34:22"
        , "2023-05-03 04:44:44"
        , "2023-05-07 08:22:12"
        , "2023-05-11 11:55:44"
    };
    
    string buffer;
    vector<string> date, yyyymmdd, hhmmss;
    for(int i=0; i<dates.size(); i++)
    {
        stringstream ss(dates[i]);
        while(getline(ss, buffer, ' '))
        {
            date.push_back(buffer);
            if(buffer.find('-') != string::npos)
                yyyymmdd.push_back(buffer);
            
            else if(buffer.find(':') != string::npos)
                hhmmss.push_back(buffer);
        }
            
    }
    
    /**
        2023-05-01  12:38:00    2023-05-02  03:34:22    2023-05-03  04:44:44    2023-05-07  08:22:22    2023-05-11  11:55:44
     */
    for(auto s : date)
        cout<<s<<" ";
        
    cout<<"\n";
    

    // 2023-05-01  2023-05-02  2023-05-03  2023-05-07  2023-05-11
    for(auto s : yyyymmdd)      // '-'가 포함된 문자열만 저장된 vector 출력
        cout<<s<<" ";
    
    cout<<"\n";    
    

    // 12:38:00    03:34:22    04:44:44    08:22:22    11:55:44
    for(auto s : hhmmss)        // ':'가 포함된 문자열만 저장된 vector 출력
        cout<<s<<" ";
    
    vector<string> ymd;
    for(int i=0; i<yyyymmdd.size(); i++)
    {
        stringstream ss(yyyymmdd[i]);
        while(getline(ss, buffer, '-'))
            ymd.push_back(buffer);
    }
    cout<<"\n";
    
    // 2023 05 01 2023 05 02 2023 05 03 2023 05 07 2023 05 11
    for(auto s : ymd)           // '-'가 포함된 문자열들을 '-'를 기준으로 split
        cout<<s<<" ";
        
    cout<<"\n";
    
    vector<string> hms;
    for(int i=0; i<hhmmss.size(); i++)
    {
        stringstream ss(hhmmss[i]);
        while(getline(ss, buffer, ':'))
            hms.push_back(buffer);
    }

    // 12 38 00 03 34 22 04 44 44 08 22 12 11 55 44
    for(auto s : hms)           // ':'가 포함된 문자열들을 '-'를 기준으로 split
        cout<<s<<" ";
        
    cout<<"\n";

    return 0;
}
```
