# Method 1 - DFS


## Intuition
Code as you think that is Brute Force Approach

## Approach
Perform DFS on each and every node connected through the given node

## Complexity
- Time complexity:
O(N*M)

- Space complexity:
O(N*M)

## Code
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


# Method 2 - BFS


## Intuition
Code BFS in matrix

## Approach
Perform BFS using queue approach

## Complexity
- Time complexity:
O(N*M)

- Space complexity:
O(N*M)

## Code
```cpp
class Solution {
public:


    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor){

        queue<pair<int,int>> q;
        q.push({sr,sc});

        int color = image[sr][sc];
        if (color == newColor) return image;
        image[sr][sc] = newColor;

        while(!q.empty()){

            int x = q.front().first;
            int y = q.front().second;
            q.pop();

            if (x>=1 && image[x-1][y] == color)               
                q.push({x-1,y}),image[x-1][y] = newColor;

            if (x<image.size()-1 && image[x+1][y] == color)    
                q.push({x+1,y}),image[x+1][y] = newColor;

            if (y>=1 && image[x][y-1] == color)                
                q.push({x,y-1}),image[x][y-1] = newColor;
                
            if (y<image[0].size()-1 && image[x][y+1] == color) 
                q.push({x,y+1}),image[x][y+1] = newColor;
            
            
        }
        
        return image;

    }

};
```
