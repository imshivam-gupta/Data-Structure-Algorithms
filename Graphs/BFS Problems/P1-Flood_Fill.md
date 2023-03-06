# Intuition
Code as you think that is Brute Force Approach

# Approach
Perform DFS on each and every node connected through the given node

# Complexity
- Time complexity:
O(N*M)

- Space complexity:
O(N*M)

# Code
```cpp
class Solution {
public:
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        int oldColor = image[sr][sc];
        if (oldColor == color) return image;
        floodFill_util(image, sr, sc, oldColor, color);
        return image;
    }

    void floodFill_util(vector<vector<int>>& image, int sr, int sc, int oldColor, int newColor){
        if (sr < 0 || sr >= image.size() || sc < 0 || sc >= image[0].size()) return;
        if (image[sr][sc] != oldColor) return;
        image[sr][sc] = newColor;
        floodFill_util(image, sr-1, sc, oldColor, newColor);
        floodFill_util(image, sr+1, sc, oldColor, newColor);
        floodFill_util(image, sr, sc-1, oldColor, newColor);
        floodFill_util(image, sr, sc+1, oldColor, newColor);
    }

};
```
