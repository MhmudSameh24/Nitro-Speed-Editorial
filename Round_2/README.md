# Editorial Round 1

### A. Hamza and Sequences

<details>
    <summary>Solution</summary>
    <ul>
        <li> 
        If <code>k</code> is odd then clearly the answer is <code>1</code>
        </li>
        <li> 
            If <code>k</code> is even, consider dividing  <code>k</code> by <code>2</code> until it becomes odd, then the answer is the number of times you divided <code>k</code> by <code>2</code> + <code>1</code>, More formally, the answer is the  logarithm to the base 2 of the largest power of 2 which is a divisor of <code>k</code> + <code>1</code>
        </li> 
    </ul>

```cpp
#include <bits/stdc++.h>
using namespace std;
int main() {
    long long n,k;
    cin >> n >> k;

    long long ans = 1;

    while(k%2==0) k/=2,ans++;

    cout << ans << endl;
}

```

</details>

### Problem B. Drawings

<details>
    <summary>Solution</summary>
    <p>
        Consider sorting the array <code>a</code> in non-decreasing order, and keep a visited array for the indexes, then try to find for each i and an index j such that <code>a[j] > a[i]</code> and <code>!visited[j]</code>, then mark <code>visited[j]</code> as true, and increment the answer by 1, the answer is the number of times we found such a j. 
    </p>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n; cin >> n;
    vector<int> v(n);

    for(auto& i : v)
        cin >> i;

    sort(v.begin(), v.end());
    vector<bool> vis(n);

    int cnt = 0;
    for(int i = 0; i < n; i++){
        for(int j = i + 1; j < n; j++){
            if(v[j] > v[i] && !vis[j]){
                cnt++;
                vis[j] = true;
                break;
            }
        }
    }

    cout << cnt;

    return 0;
}
```

</details>

### Problem C. Gaming Consoles Problems

<details>
    <summary>Solution</summary>
    <br>
    <p>
        Try To simulate the process, let's try the following approach:
        let's always use the <code>b</code> as the smallest charging till now, 
        then while <code>a > 0 and b > 0</code> we should try to charge b and decrease a by 2, and increase b by 1, and increment the answer by 1, then the answer is the number of times we did this process.
    </p>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {

    int a, b; cin >> a >> b;

    int cnt = 0;
    while(a > 0 && b > 0){
        if(a < b)
            swap(a, b);

        if(a == 1)
            break;

        a -= 2;
        b++;
        cnt++;
    }

    cout << cnt;


    return 0;
}
```

</details>

### Problem D. New Administrative Capital

<details>
    <summary>Solution</summary>
    <br>
    <p>
      This is a simple Implementation problem see the code below:
    </p>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {

   int n;
    cin >> n;
    bool found = false;
    char Arr[n][5];
    for(int i = 0; i < n; i++)
    {
        for(int j = 0; j < 5; j++)
        {
            cin >> Arr[i][j];
        }
    }


    for(int i = 0; i < n; i++)
    {
        if(Arr[i][0] == 'O' && Arr[i][1] == 'O' && found == false)
        {
            Arr[i][0] = '+';
            Arr[i][1] = '+';
            found = true;
        }

        if(Arr[i][3] == 'O' && Arr[i][4] == 'O' && found == false)
        {
            Arr[i][3] = '+';
            Arr[i][4] = '+';
            found = true;
        }
    }


    if(found == true)
    {
        cout << "YES\n";
        for(int i = 0; i < n; i++)
        {
            for(int j = 0; j < 5; j++)
            {
                cout << Arr[i][j];
            }
            cout << endl;
        }
    }

    else cout << "NO\n";



    return 0;
}
```

</details>

### Problem E. The Path To The ICPC

<details>
    <summary>Solution</summary>
    <br>
    <p>
     Scene you can travel between any pair of airports, then it is always optimal to go from a to b, then the answer will be 0 if <code>s[a]  == s[b]</code> and 1 otherwise. 
    </p>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {

    int n, a, b; cin >> n >> a >> b;
    string s; cin >> s;

    if(s[a - 1] == s[b - 1])
        cout << 0;
    else
        cout << 1;


    return 0;
}
```

</details>

### Problem F. Grasshopper XS Max

<details>
    <summary>Solution</summary>
    <br>
    <p>
Programming technique problem: You need to determine the positions of the grasshopper and insect. If k does not divide the difference in position, the answer is NO. Otherwise, we have to check positions pos+k, pos+2k, and so on, where pos is the minimal position of the grasshopper and insect. If there is an obstacle at any of these positions, the answer is NO; otherwise, the answer is YES.
    </p>

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {

    int n,k;
    cin >> n >> k;
    vector<char> vec(n);
    int pofG=0,pofT=0;
    for(int i = 0; i < n; i++){
        cin >> vec[i];
        if (vec[i] == 'G') pofG = i+1;
        if (vec[i] == 'T') pofT = i+1;
    }
    if (pofG > pofT){
        swap(vec[pofG-1], vec[pofT-1]);
        swap(pofG, pofT);
    }
    bool eat=false;
    // cout(vec);
    for (int i=pofG; i<=n; i+=k){
        if (vec[i-1]=='#') break;
        if (vec[i-1]== 'T') {
            eat = true;
            break;
        }
    }
    cout << (eat ? "YES" : "NO");


    return 0;
}
```

</details>
