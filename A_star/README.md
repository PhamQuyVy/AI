# A* Search - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
A* Search
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán A* hoạt động dựa trên:

* Chi phí thực tế `g(n)`
* Hàm heuristic `h(n)`

và luôn ưu tiên node có:

```text
f(n) = g(n) + h(n)
```

nhỏ nhất.

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

# Ý tưởng thuật toán

Thuật toán A* sử dụng:

```text
Priority Queue (Min Heap)
```

để luôn lấy trạng thái có:

```text
f(n) nhỏ nhất
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

# Hàm chi phí

Ngoài heuristic, project còn sử dụng:

```text
Weighted Step Cost
```

Chi phí phụ thuộc vào vị trí ô trống.

---

## Position Cost

```python
POSITION_COST = {
    0: 4, 1: 2, 2: 4,
    3: 2, 4: 1, 5: 2,
    6: 4, 7: 2, 8: 4
}
```

---

## Ý nghĩa

* Ô giữa:
  cost thấp nhất

* Ô cạnh:
  cost trung bình

* Ô góc:
  cost cao nhất

---

# Hàm đánh giá A*

Thuật toán sử dụng:

```text
f(n) = g(n) + h(n)
```

Trong đó:

* `g(n)`:
  tổng chi phí từ start đến node hiện tại

* `h(n)`:
  Manhattan Distance

* `f(n)`:
  chi phí ước lượng tổng

---

# Ví dụ Manhattan Distance

## Trạng thái hiện tại

```text
1 2 3
4 0 6
7 5 8
```

## Tính heuristic

* Ô `5` lệch 1 ô
* Ô `8` lệch 1 ô

```text
h(n) = 2
```

---

# Quy trình hoạt động

1. Đưa trạng thái đầu vào heap.
2. Tính `h(start)`.
3. Pop node có `f(n)` nhỏ nhất.
4. Kiểm tra goal.
5. Sinh trạng thái con.
6. Tính:

```text
g(n), h(n), f(n)
```

7. Push lại vào heap.
8. Lặp đến khi tìm thấy goal.

---

# Pseudocode

```text
function A_Star(Start, Goal):

    frontier = priority queue
    reached = {}

    push Start với:
        f = g + h

    while frontier không rỗng:

        lấy node có f nhỏ nhất

        nếu node là Goal:
            trả về lời giải

        sinh các node con

        với mỗi node con:

            child_g = g + cost

            child_f = child_g + h(child)

            nếu tốt hơn:
                push vào frontier
```

---

# Chức năng giao diện

## Gồm

* Bàn cờ 8 Puzzle 3x3.
* Animation lời giải.
* Shuffle random board.
* Solve tự động.
* Step-by-step.
* Hiển thị:

  * Expanded Nodes
  * Steps
  * Time
  * Step Cost
  * `g(n)`
  * `h(n)`
  * `f(n)`

---

# Highlight đặc biệt

## Ô đúng vị trí

* Màu trắng.

## Ô sai vị trí

* Màu đỏ nhạt.

## Ô trống

Màu thay đổi theo cost:

| Cost | Màu       |
| ---- | --------- |
| 1    | Xanh nhạt |
| 2    | Vàng nhạt |
| 4    | Hồng nhạt |

---

# Các thành phần chính

| Hàm               | Chức năng                |
| ----------------- | ------------------------ |
| `manhattan()`     | Tính heuristic Manhattan |
| `step_cost()`     | Tính cost vị trí         |
| `get_neighbors()` | Sinh trạng thái con      |
| `astar()`         | Thuật toán A*            |
| `draw()`          | Vẽ bàn cờ                |
| `animate()`       | Animation lời giải       |
| `shuffle()`       | Random board             |
| `solve()`         | Chạy thuật toán          |

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

A* sẽ ưu tiên:

```text
node có f(n) nhỏ nhất
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

# Ví dụ log thuật toán

```text
1. DOWN  g=2(+2) h=1 f=3
2. RIGHT g=4(+2) h=0 f=4
```

Trong đó:

* `(+2)`:
  step cost hiện tại

* `g`:
  tổng chi phí

* `h`:
  heuristic

* `f`:
  giá trị A*

---

# Công nghệ sử dụng

* Python 3
* Tkinter
* Heap Queue (`heapq`)

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python A_star.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
A* Search Algorithm
```

Đặc điểm:

* Sử dụng heuristic để tối ưu tìm kiếm.
* Đảm bảo tối ưu nếu heuristic admissible.
* Hiệu quả hơn BFS.
* Tìm lời giải tốt hơn Greedy Search.
* Manhattan Distance giúp đánh giá độ gần goal.

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

Do A* cần lưu frontier.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**
