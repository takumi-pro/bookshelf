## 問題

### 1.1 重複のない文字列

バケットの考え方で、文字の種類（ここではASCII）の要素を持った配列を用意して文字コードをインデックスとして対応させる。対応した要素はtrueを代入する。
```cpp
#include <bits/stdc++.h>
using namespace std;

bool isUniqueChars(string S) {
    if (S.size() > 128) return false;

    vector<bool> ans(128, false);
    for (int i = 0; i < S.size(); i++) {
        int char_i = 0 + S[i];
        if (ans[char_i]) return false;
        ans[char_i] = true;
    }
    return true;
}

int main(void){
    string S; cin >> S;
    if (isUniqueChars(S)) cout << "Unique!!" << endl;
    else cout << "Not Unique!!" << endl;
}

```