# Uniform Cost Search (UCS) - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán **8-Puzzle** sử dụng thuật toán:

```text
Uniform Cost Search (UCS)
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán UCS hoạt động dựa trên:

- Chi phí đường đi nhỏ nhất.
- Mỗi trạng thái có một `path cost`.
- Node có tổng chi phí nhỏ nhất sẽ được mở rộng trước.

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

Thuật toán UCS sử dụng:

```text
Priority Queue (Min Heap)
```

để luôn lấy trạng thái có:

```text
path cost nhỏ nhất
```

---

# Hàm chi phí

Project sử dụng:

```text
Position Cost
```

Chi phí phụ thuộc vào vị trí của ô trống (`0`).

---

## Bảng cost

| Vị trí | Cost |
|---|---|
| Góc | 4 |
| Cạnh | 2 |
| Trung tâm | 1 |

---

## Cost Map

```text
4 2 4
2 1 2
4 2 4
```

---

# Công thức tính

## Step Cost

```python
step_cost(board)
```

Lấy cost dựa theo vị trí hiện tại của ô trống.

---

## Path Cost

```text
g(child) = g(parent) + step_cost(child)
```

---

# Quy trình hoạt động

1. Đưa trạng thái đầu vào heap.
2. Pop node có cost nhỏ nhất.
3. Kiểm tra goal.
4. Sinh trạng thái con.
5. Tính cost mới.
6. Push lại vào heap.
7. Lặp đến khi tìm thấy goal.

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
  - Step Cost
  - Total Path Cost

---

# Highlight đặc biệt

## Ô sai vị trí

- Ô sai sẽ hiển thị màu đỏ.

## Ô trống

- Ô trống đổi màu theo cost:

| Cost | Màu |
|---|---|
| 1 | Xanh nhạt |
| 2 | Vàng nhạt |
| 4 | Hồng nhạt |

---

# Các thành phần chính

| Hàm | Chức năng |
|---|---|
| `get_neighbors()` | Sinh trạng thái con |
| `step_cost()` | Tính cost theo vị trí |
| `ucs()` | Thuật toán Uniform Cost Search |
| `draw()` | Vẽ bàn cờ |
| `animate()` | Animation lời giải |
| `shuffle()` | Random board |
| `solve()` | Chạy UCS |

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

UCS sẽ ưu tiên:

```text
node có total path cost nhỏ nhất
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
python ucs_8puzzle.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Uniform Cost Search (UCS)
```

Đặc điểm:

- Tìm đường đi có chi phí nhỏ nhất với vị trí trên bàn cờ khác nhau thì cost khác nhau.
- Hoàn chỉnh (Complete).
- Tối ưu  nếu cost dương.
- Tổng quát hơn BFS, DFS.
---

# Tác giả

**24133077- Phạm Quý Vỹ**