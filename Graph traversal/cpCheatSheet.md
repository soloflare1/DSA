
# ⭐ 1️⃣ Fast I/O

```cpp
#define Naba ios_base::sync_with_stdio(false); cin.tie(0); cout.tie(0);
```

---

# ⭐ 2️⃣ Common Typedef

```cpp
typedef long long ll;
typedef vector<int> vi;
typedef pair<int,int> pii;
```

---

# ⭐ 3️⃣ Infinity Values

```cpp
const int INF = 1e9;
const ll LINF = 1e18;
```

---

## ✔ 1. **4 Directions (Up, Down, Left, Right)**

```cpp
vector<pair<int,int>> dir = {
    {-1, 0}, // up
    {1, 0},  // down
    {0, -1}, // left
    {0, 1}   // right
};
```

---

## ✔ 2. **8 Directions (Including Diagonals)**

```cpp
vector<pair<int,int>> dir = {
    {-1, 0},  // up
    {1, 0},   // down
    {0, -1},  // left
    {0, 1},   // right
    {-1, -1}, // up-left
    {-1, 1},  // up-right
    {1, -1},  // down-left
    {1, 1}    // down-right
};
```

---

## ✔ 3. **Knight Moves (Chess Knight — BFS Problems)**

```cpp
vector<pair<int,int>> knight = {
    {-2, -1}, {-2,  1},
    {-1, -2}, {-1,  2},
    { 1, -2}, { 1,  2},
    { 2, -1}, { 2,  1}
};
```
---

# ⭐ 

```cpp
for(auto [dx, dy] : dir)
{
    int ni = i + dx;
    int nj = j + dy;
}
```

---

# ⭐ 5️⃣ Check valid cell

```cpp
bool valid(int i, int j, int n, int m){
    return (i>=0 && i<n && j>=0 && j<m);
}
```

---

# ⭐ 6️⃣ BFS Template

```cpp
queue<pii> q;
q.push({si, sj});
vis[si][sj] = 1;
level[si][sj] = 0;

while(!q.empty()){
    auto [x,y] = q.front(); q.pop();
    for(int k=0;k<4;k++){
        int nx = x + dx[k];
        int ny = y + dy[k];
        if(valid(nx,ny,n,m) && !vis[nx][ny]){
            vis[nx][ny] = 1;
            level[nx][ny] = level[x][y] + 1;
            q.push({nx,ny});
        }
    }
}
```

---

# ⭐ 7️⃣ 0–1 BFS Template

```cpp
deque<int> dq;
dq.push_front(src);
dist[src] = 0;

while(!dq.empty()){
    int u = dq.front(); dq.pop_front();
    for(auto [v, w] : adj[u]){
        if(dist[v] > dist[u] + w){
            dist[v] = dist[u] + w;
            if(w == 0) dq.push_front(v);
            else dq.push_back(v);
        }
    }
}
```

---

# ⭐ 8️⃣ Dijkstra Template

```cpp
priority_queue<pii, vector<pii>, greater<pii>> pq;
pq.push({0, src});
dist[src] = 0;

while(!pq.empty()){
    auto [d,u] = pq.top(); pq.pop();
    if(d != dist[u]) continue;

    for(auto [v,w] : adj[u]){
        if(dist[v] > d + w){
            dist[v] = d + w;
            pq.push({dist[v], v});
        }
    }
}
```

---

# ⭐ 9️⃣ DFS Template

```cpp
void dfs(int u){
    vis[u] = 1;
    for(int v : adj[u]){
        if(!vis[v]) dfs(v);
    }
}
```

---

# ⭐ 🔟 Fast Power (Binary Exponentiation)

```cpp
ll binpow(ll a, ll b){
    ll res = 1;
    while(b){
        if(b&1) res *= a;
        a *= a;
        b >>= 1;
    }
    return res;
}
```

---

# ⭐ 11️⃣ GCD / LCM

```cpp
ll gcd(ll a, ll b){ return b ? gcd(b, a%b) : a; }
ll lcm(ll a, ll b){ return a/gcd(a,b)*b; }
```

---

# ⭐ 12️⃣ Prime Check

```cpp
bool isPrime(long long n){
    if(n < 2) return false;
    for(long long i=2; i*i <= n; i++)
        if(n % i == 0) return false;
    return true;
}
```

---

# ⭐ 13️⃣ Sieve of Eratosthenes

```cpp
vector<bool> prime(n+1, true);
prime[0] = prime[1] = false;
for(int i=2;i*i<=n;i++){
    if(prime[i]){
        for(int j=i*i;j<=n;j+=i)
            prime[j] = false;
    }
}
```

---

# ⭐ 14️⃣ Sorting Tricks

Sort pair by second:

```cpp
sort(v.begin(), v.end(), 
    [](auto &a, auto &b){ return a.second < b.second; });
```

---

# ⭐ 15️⃣ Frequency Map

```cpp
map<int,int> mp;
mp[x]++;
```

---

# ⭐ 16️⃣ Vector Input Shortcut

```cpp
vector<int> a(n);
for(int &x : a) cin >> x;
```

---

# ⭐ 17️⃣ Fast Max/Min Update

```cpp
mx = max(mx, x);
mn = min(mn, x);
```

---

# ⭐ 18️⃣ Debug Print

```cpp
#define debug(x) cout << #x << " = " << x << "\n";
```

---

# ⭐ 19️⃣ Modular Arithmetic

```cpp
const int MOD = 1e9+7;

ll add(ll a,ll b){ return (a+b)%MOD; }
ll mul(ll a,ll b){ return (a*b)%MOD; }
ll sub(ll a,ll b){ return (a-b+MOD)%MOD; }
```

---

# ⭐ 20️⃣ Graph Input

```cpp
for(int i=0;i<e;i++){
    int u,v;
    cin >> u >> v;
    adj[u].push_back(v);
    adj[v].push_back(u); // remove for directed
}
```

