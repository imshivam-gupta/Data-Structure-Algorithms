## General Code
```cpp
int bfs(unordered_map<string, vector<ip>>& adj, vector<string>& query) {
    unordered_set<string> visited;
    string start = query[0];
    string end = query[1];
    queue<ip> q;
    q.push({start, 1});
    visited.insert(start);
    while (!q.empty()) {
        int sz = q.size();
        for (int i = 0; i < sz; i++) {
            auto [node, cost] = q.front(); q.pop();
            if (!adj.count(node)) continue;
            if (node == end) return cost;
            for (auto& a : adj[node]) {
                if (!visited.count(a.first)) {
                    q.push({a.first, cost * a.second});
                    visited.insert(node);
                }
            }
        }
    }
    return -1;
}
```

## Realted Problems 
- [Flood Fill](https://leetcode.com/problems/flood-fill/)
- [Number of Islands](https://leetcode.com/problems/number-of-islands/)
- [Word Ladder I](https://leetcode.com/problems/word-ladder/)
- [Word Ladder II](https://leetcode.com/problems/word-ladder-ii/)
- [Evaluate Division](https://leetcode.com/problems/evaluate-division/)
- [Get Watched Videos by Your Friends](https://leetcode.com/problems/get-watched-videos-by-your-friends/)
- [Cut Off Trees for Golf Event](https://leetcode.com/problems/cut-off-trees-for-golf-event/)
