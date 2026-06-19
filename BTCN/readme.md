# AI Search Algorithms - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng nhiều thuật toán tìm kiếm trong Trí tuệ Nhân tạo (Artificial Intelligence)

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Project giúp trực quan hóa quá trình giải bài toán 8-Puzzle và so sánh hiệu năng giữa các thuật toán tìm kiếm khác nhau.

---

# Trạng thái đích

```text
1 2 3
4 5 6
7 8 0
```

Trong đó:

* `0` là ô trống.

---

# Bài toán 8 Puzzle

Cho một trạng thái ban đầu bất kỳ:

```text
2 8 3
1 6 4
7 0 5
```

Mục tiêu là đưa tất cả quân số về đúng vị trí bằng cách di chuyển ô trống.

---

# Các thuật toán được cài đặt

## Uninformed Search

```text
BFS (Breadth First Search)
DFS (Depth First Search)
IDS (Iterative Deepening Search)
UCS (Uniform Cost Search)
```

---

## Informed Search

```text
Greedy Best First Search
A* Search
```

---

## Local Search

```text
Hill Climbing
Steepest Ascent Hill Climbing
Random Hill Climbing
Random Restart Hill Climbing
Local Beam Search
Simulated Annealing
```

---

## CSP Search

```text
Backtracking Search
Forward Checking
```

---

## Other Search Methods

```text
AND-OR Graph Search
Sensorless Search
Belief State Search
```

---

# Heuristic sử dụng

Các thuật toán heuristic sử dụng:

```text
Manhattan Distance
Misplaced Tiles
```

---

## Manhattan Distance

```text
h(n) =
Σ(|x - x_goal| + |y - y_goal|)
```

Tính tổng khoảng cách Manhattan của tất cả quân số tới vị trí đích.

---

## Misplaced Tiles

```text
h(n) =
Số quân đang sai vị trí
```

---

# Ý tưởng thuật toán

Mỗi thuật toán sử dụng chiến lược tìm kiếm khác nhau:

### BFS

```text
Mở rộng theo từng mức
```

Đảm bảo tìm lời giải ngắn nhất.

---

### DFS

```text
Đi sâu nhất có thể
```

Tiết kiệm bộ nhớ nhưng không đảm bảo tối ưu.

---

### UCS

```text
Ưu tiên node có chi phí nhỏ nhất
```

---

### Greedy Search

```text
Ưu tiên node có h(n) nhỏ nhất
```

---

### A*

```text
f(n) = g(n) + h(n)
```

Kết hợp chi phí thực tế và heuristic.

---

### Hill Climbing

```text
Luôn chọn trạng thái tốt hơn hiện tại
```

---

### Simulated Annealing

```text
Cho phép đi lùi để tránh local optimum
```

---

### Local Beam Search

```text
Giữ lại k trạng thái tốt nhất
```

---

# Quy trình hoạt động

1. Sinh trạng thái ban đầu.
2. Chọn thuật toán.
3. Thực hiện tìm kiếm.
4. Sinh trạng thái con.
5. Đánh giá node.
6. Mở rộng node phù hợp.
7. Tìm đường đi đến goal.
8. Hiển thị animation lời giải.

---

# Pseudocode tổng quát

```text
function SEARCH(start):

    frontier ← {start}

    while frontier không rỗng:

        chọn node theo chiến lược

        nếu node là goal:
            return solution

        sinh trạng thái con

        thêm vào frontier

    return failure
```

---

# Chức năng giao diện

## Gồm

* Bàn cờ 8 Puzzle 3x3.
* Shuffle random board.
* Chọn thuật toán.
* Solve tự động.
* Animation lời giải.
* Reset board.
* Hiển thị thống kê.

---

# Thông tin hiển thị

```text
Expanded Nodes
Generated Nodes
Solution Depth
Execution Time
Path Cost
```

---

# Highlight đặc biệt

## Ô đúng vị trí

```text
Màu trắng
```

---

## Ô sai vị trí

```text
Màu đỏ nhạt
```

---

## Ô trống

```text
Màu xanh nhạt
```

---

# Các thành phần chính

| Hàm | Chức năng |
|------|------------|
| `manhattan()` | Tính Manhattan Distance |
| `misplaced_tiles()` | Tính số ô sai vị trí |
| `get_neighbors()` | Sinh trạng thái con |
| `bfs()` | Breadth First Search |
| `dfs()` | Depth First Search |
| `ids()` | Iterative Deepening Search |
| `ucs()` | Uniform Cost Search |
| `greedy()` | Greedy Best First Search |
| `astar()` | A* Search |
| `hill_climbing()` | Hill Climbing |
| `beam_search()` | Local Beam Search |
| `simulated_annealing()` | Simulated Annealing |
| `draw()` | Vẽ bàn cờ |
| `animate()` | Hiển thị lời giải |
| `shuffle()` | Sinh trạng thái ngẫu nhiên |
| `solve()` | Chạy thuật toán |

---

# Ví dụ

## Input

```text
1 2 3
4 0 6
7 5 8
```

---

## Output

```text
1 2 3
4 0 6
7 5 8
```

↓

```text
1 2 3
4 5 6
7 0 8
```

↓

```text
1 2 3
4 5 6
7 8 0
```

---

# Ví dụ kết quả

```text
Algorithm: A*

Expanded Nodes : 6
Steps          : 2
Path Cost      : 2
Time           : 0.0008 sec
```

---

# Công nghệ sử dụng

* Python 3
* Tkinter
* heapq
* collections.deque
* random
* math
* time

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy Notebook

```bash
jupyter notebook
```

Mở file:

```bash
BTCN.ipynb
```

và chạy từng cell.

---

# Kiến thức AI áp dụng

Project sử dụng các chủ đề:

```text
State Space Search
Heuristic Search
Local Search
Constraint Satisfaction Problem (CSP)
AND-OR Search
Belief State Search
Sensorless Search
```

---

# Độ phức tạp

## Time Complexity

```text
O(b^d)
```

Trong đó:

* `b` là branching factor
* `d` là độ sâu lời giải

---

## Space Complexity

```text
O(b^d)
```

Tùy thuộc vào thuật toán sử dụng.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**