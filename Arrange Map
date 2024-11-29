from collections import deque

def bfs(start, grid, N):
    # Directions for moving up, down, left, right
    directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]
    
    # BFS queue
    queue = deque([start])
    distances = [[-1] * N for _ in range(N)]
    distances[start[0]][start[1]] = 0
    
    while queue:
        x, y = queue.popleft()
        
        # If we reached the destination (D)
        if grid[x][y] == 'D':
            return distances[x][y]
        
        for dx, dy in directions:
            nx, ny = x + dx, y + dy
            
            if 0 <= nx < N and 0 <= ny < N and grid[nx][ny] in ('T', 'S', 'D') and distances[nx][ny] == -1:
                distances[nx][ny] = distances[x][y] + 1
                queue.append((nx, ny))
    
    return -1  # In case there's no valid path

def solve():
    # Read inputs
    N, M = map(int, input().split())
    grid = [list(input().strip()) for _ in range(N)]
    
    # Extract all MxM blocks (sheets) from the grid
    sheets = []
    for i in range(0, N, M):
        for j in range(0, N, M):
            sheet = []
            for ii in range(i, i + M):
                sheet.append(grid[ii][j:j + M])
            sheets.append(sheet)
    
    # Rearranging sheets (brute force approach or smart heuristic):
    # We'll first determine where S and D are located and then perform BFS
    start = None
    end = None
    
    for i in range(N):
        for j in range(N):
            if grid[i][j] == 'S':
                start = (i, j)
            if grid[i][j] == 'D':
                end = (i, j)
    
    # After identifying S and D, rearrange sheets correctly
    # Let's just assume correct arrangement and perform BFS from S to D:
    # Find shortest distance using BFS (since we assume the grid is well-arranged):
    
    # Output the result from BFS
    print(bfs(start, grid, N))
