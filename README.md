# counting-islands
given an mxn 2D binary grid which represents a map of '1 s (land) and '0'is '(water) return the number of islands'''
'''an island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. you may assume all four edges
of the grid are all surrouned by the water.'''
def numslands(grid: list[list[str]]):
    if not grid:
        return 0
    rows = len(grid)
    col = len(grid[0])
    count = 0  
    def bfs(r, c):
        queue = [(r, c)]
        grid[r][c] = '0'
        while queue:
            x, y = queue.pop(0)
            for dx, dy in [(-1, 0), (1, 0), (0, -1), (0, 1)]:
                nx, ny = x + dx, y + dy
                if 0 <= nx < rows and 0 <= ny < col and grid[nx][ny] == '1':
                    grid[nx][ny] = '0'  
                    queue.append((nx, ny))
    for r in range(rows):
        for c in range(col):
            if grid[r][c] == '1':
                bfs(r, c)  
                count += 1  
    return count
arr = [
    ["1", "1", "1", "1", "0"],
    ["1", "1", "0", "1", "0"],
    ["1", "1", "0", "0", "0"],
    ["0", "0", "0", "0", "0"]
]
print(numslands(arr))
