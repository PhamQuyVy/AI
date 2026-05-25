# Greedy Search (Manhattan Distance) - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
Greedy Best First Search
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán Greedy hoạt động dựa trên:

- Hàm heuristic `h(n)`
- Luôn ưu tiên node có:

```text
h(n) nhỏ nhất
```

---

# Trạng thái đích

```text
1 2 3
4 5 6
7 8 0
```

Trong đó:

- `0` là ô trống.

---

# Ý tưởng thuật toán

Thuật toán Greedy sử dụng:

```text
Priority Queue (Min Heap)
```

để luôn lấy trạng thái có:

```text
Manhattan Distance nhỏ nhất
```

---

# Hàm heuristic

Project sử dụng:

```text
Manhattan Distance
```

---

## Công thức Manhattan

```text
h(n) =
|x1 - x2| + |y1 - y2|
```

Tổng khoảng cách của tất cả ô số tới vị trí đích.

---

# Ví dụ Manhattan Distance

## Trạng thái hiện tại

```text
1 2 3
4 0 6
7 5 8
```

## Tính heuristic

- Ô `5` lệch 1 ô
- Ô `8` lệch 1 ô

```text
h(n) = 2
```

---

# Quy trình hoạt động

1. Đưa trạng thái đầu vào heap.
2. Tính `h(start)`.
3. Pop node có heuristic nhỏ nhất.
4. Kiểm tra goal.
5. Sinh trạng thái con.
6. Tính heuristic mới.
7. Push lại vào heap.
8. Lặp đến khi tìm thấy goal.

---

# Pseudocode

```text
function Greedy_Search(Start, Goal):

    frontier = priority queue
    reached = {}

    push Start vào frontier với h(Start)

    while frontier không rỗng:

        lấy node có h nhỏ nhất

        nếu node là Goal:
            trả về lời giải

        thêm node vào reached

        sinh các node con

        với mỗi node con:
            nếu chưa xuất hiện:
                tính h(node con)
                push vào frontier
```

---

# Chức năng giao diện

## Gồm

- Bàn cờ 8 Puzzle 3x3.
- Animation lời giải.
- Shuffle random board.
- Solve tự động.
- Step-by-step.
- Hiển thị:

  - Expanded Nodes
  - Steps
  - Time
  - Heuristic hiện tại `h(n)`

---

# Highlight đặc biệt

## Ô đúng vị trí

- Màu xanh nhạt.

## Ô gần đúng

- Màu vàng.

## Ô xa vị trí đích

- Màu cam hoặc đỏ nhạt.

## Ô trống

- Hiển thị màu xám.

---

# Các thành phần chính

| Hàm | Chức năng |
|---|---|
| `manhattan()` | Tính heuristic Manhattan |
| `get_neighbors()` | Sinh trạng thái con |
| `greedy()` | Thuật toán Greedy Search |
| `draw()` | Vẽ bàn cờ |
| `animate()` | Animation lời giải |
| `shuffle()` | Random board |
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

## Quá trình

Greedy sẽ ưu tiên:

```text
node có Manhattan Distance nhỏ nhất
```

---

## Output

```text
1 2 3
4 0 6
7 5 8
```

↓

DOWN

```text
1 2 3
4 5 6
7 0 8
```

↓

RIGHT

```text
1 2 3
4 5 6
7 8 0
```

---

# Công nghệ sử dụng

- Python 3
- Tkinter
- Heap Queue (`heapq`)

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python greedy_8puzzle.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Greedy Best First Search
```

Đặc điểm:

- Dùng heuristic để tìm đường đi nhanh hơn.
- Không đảm bảo tối ưu.
- Thường nhanh hơn BFS/DFS.
- Dễ bị mắc kẹt local optimum.
- Manhattan Distance giúp đánh giá độ gần goal.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**