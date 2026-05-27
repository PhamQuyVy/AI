# IDA* Search - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
IDA* (Iterative Deepening A*)
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
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

# Ý tưởng thuật toán IDA*

IDA* là sự kết hợp giữa:

```text
IDS + A*
```

```text
f(n)=g(n)+h(n) 
```

để giới hạn độ sâu tìm kiếm.

---

# Hàm heuristic

Project sử dụng:

```text
g(n) = số ô sai vị trí
```

Ví dụ:

```text
1 2 3
4 0 6
7 5 8
```

Sai vị trí:

- 5
- 8

=>:

```text
g(n)=2
```

---

# Hàm g(n)

Project sử dụng:

```text
h(n) = Manhattan Distance
```

Mỗi bước:

```text
h(n) = tổng khoảng cách Manhattan của các ô
```

---

# Manhattan Distance

Công thức:

```text
|x1-x2| + |y1-y2|
```

Ví dụ:

```text
1 2 3
4 0 6
7 5 8
```

- Ô `5` cách vị trí đúng 1 bước
- Ô `8` cách vị trí đúng 1 bước

=>:

```text
h(n)=2
```

---

# Hàm đánh giá

```text
f(n)=g(n)+h(n)
```

Trong đó:

- `h(n)` = Manhattan Distance
- `g(n)` = số ô sai vị trí

---

# Cơ chế hoạt động

IDA* hoạt động theo:

```text
threshold
```

Ban đầu:

```text
threshold = f(start)
```

---

# Quy trình hoạt động

1. Bắt đầu DFS từ node gốc.
2. Tính:

```text
f(n)=g(n)+h(n)
```

3. Nếu:

```text
f(n) > threshold
```

→ cắt nhánh.

4. Nếu không tìm thấy goal:

```text
threshold = giá trị f nhỏ nhất bị prune
```

5. Lặp lại cho đến khi tìm thấy lời giải.

---

# Ví dụ

## Input

```text
1 2 3
4 0 6
7 5 8
```

---

## Start

```text
h(n)=2
g(n)=2
f(n)=4
```

---

## Sau DOWN

```text
1 2 3
4 5 6
7 0 8
```

```text
h(n)=1
g(n)=1
f(n)=2
```

---

## Sau RIGHT

```text
1 2 3
4 5 6
7 8 0
```

```text
h(n)=0
g(n)=0
f(n)=0
```

---

# Đường đi

```text
START
↓
DOWN
↓
RIGHT
↓
GOAL
```

---

# Các thành phần chính

| Hàm | Chức năng |
|---|---|
| `h_misplaced()` | Tính số ô sai |
| `manhattan()` | Tính Manhattan Distance |
| `get_neighbors()` | Sinh trạng thái con |
| `ida_star()` | Thuật toán IDA* |
| `draw()` | Vẽ bàn cờ |
| `animate()` | Animation |
| `solve()` | Chạy IDA* |

---

# Giao diện chương trình

## Bao gồm

- Bàn cờ 8 Puzzle.
- Animation từng bước.
- Shuffle random board.
- Solve tự động.
- Step-by-step.
- Hiển thị:

  - Nodes expanded
  - Steps
  - Time
  - g(n)
  - h(n)
  - f(n)

---

# Highlight giao diện

## Ô đúng vị trí

- Màu đen.

## Ô sai vị trí

- Màu đỏ.

## Ô trống

- Màu xám nhạt.

---

# Thuật toán IDA* trong code

## IDS có giới hạn

```python
if f > threshold:
    return f
```

---

## Goal test

```python
if current == GOAL:
    return "FOUND"
```

---

## Tăng threshold

```python
threshold = result
```

---

# Công nghệ sử dụng

- Python 3
- Tkinter
- Recursive DFS

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
jupyter IDA.ipynb
```

---

# Đặc điểm của IDA*

| Đặc điểm | IDA* |
|---|---|
| Complete | Có |
| Optimal | Có |
| Bộ nhớ | Thấp |
| Tốc độ | Nhanh |
| Heuristic | Có |

---

# So sánh nhanh

| Thuật toán | Có heuristic | Dùng RAM |
|---|---|---|
| DFS | Không | Thấp |
| BFS | Không | Rất cao |
| A* | Có | Cao |
| IDA* | Có | Thấp |

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Heuristic Search
```

và:

```text
Iterative Deepening A*
```

để giải bài toán tìm đường trong không gian trạng thái.

---

# Tác giả

```text
24133077 - Phạm Quý Vỹ
```