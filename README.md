# Logic-Design
Here is my logic design report

---

- Lab1 基本邏輯閘與使用

- Lab2 互斥或閘與應用

- Lab3 NAND 與 NOR 閘與應用

- Lab4 簡單應用與電路布林代數

- Lab5 卡諾圖

- Lab6 七段顯示器與解碼電路

- Lab7 加減法器

- Lab8 比較器與多工器

- Lab9 組合應用電路

- Lab10 閂鎖器與正反器

- Lab11 移位暫存器與應用:wq

- Lab12 非同步計數器

- Lab13 同步計數器

- Lab14 有限狀態機

```cpp=
#include<bits/stdc++.h>
using namespace std;

#define int long long
#define all(aa) aa.begin(),aa.end()
const int MAXN = 1e7+10;
//vector<vector<int>> mp; // val group
unordered_map<int, vector<int>> mp;
//vector<int> mp[MAXN];
deque<int> arr;

bool group(int a, int b){
    for(auto i: mp[b]){
        for(auto k : mp[a]){
            if(i == k){
                return 1;
            }
        }
    }
    return 0;
}

void solve(){
    string ss;
    int now, ind = 0;
    while(cin >> ss){
        
        if(ss == "STOP"){
            break;
        }
        
        else if(ss == "ENQUEUE"){
            int ind = (int)(arr.end()-arr.begin());
            cin >> now;
            for(int i=0;i<arr.size();i++){
                if(group(arr[i], now)){
                    ind = i + 1;
                }
            }

            arr.insert(arr.begin()+ind, now);    
        }    
        
        else{
            if(!arr.empty()){
                cout << arr.front() << "\n";
                arr.pop_front();    
            }
        }
    }
    
    return;
}


signed main(){
    ios_base::sync_with_stdio(false); cin.tie(0);
    int n, Case = 1;
    while(cin >> n){
        mp.clear();
        arr.clear();
        cout << "Line #" << Case++ << "\n";
        int m, val;
        
        //unordered_set<int> tmp;
        
        for(int i=0;i<n;i++){
            cin >> m;
            for(int i=0;i<m;i++){
                cin >> val;
          //      tmp.insert(val);
                mp[val].push_back(m);
            }
        }
        
        //for(auto i:tmp){
          //  sort(mp[i].begin(), mp[i].end());
        //}
        
        solve();
    }
    
    return 0;
}
```
