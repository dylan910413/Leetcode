Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

輸出二進制的 1~n 中有分別有幾個 1
利用二進制是不斷除以2求餘數的特性
答案原本用dp建表格做查詢
但因為從小排到大，實際上依序查詢 [x/2] 再加 x%2 就可以了

```c++=
class Solution {
public:
    int bit[100005] = {0};
    int count(int x){
        if(bit[x]) return bit[x];
        if(x == 0) return bit[x] = 0;
        else if(x == 1) return bit[x] = 1;
        else return bit[x] = x%2 + count(x/2);
    }
    vector<int> countBits(int n) {
        vector<int> ans;
        for(int i = 0;i <= n;i++){
            ans.push_back(count(i));
        }
        return ans;
    }
};
```

