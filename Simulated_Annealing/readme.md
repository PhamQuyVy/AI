# Simulated Annealing (Misplaced Tiles Heuristic) - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
Simulated Annealing
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán Simulated Annealing sử dụng cơ chế nhiệt độ (Temperature) để điều khiển quá trình tìm kiếm lời giải.

Trong quá trình thực hiện, thuật toán có thể chấp nhận một trạng thái kém hơn với một xác suất nhất định nhằm mở rộng không gian tìm kiếm.

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

Thuật toán bắt đầu từ trạng thái hiện tại.

Ở mỗi bước:

- Sinh các trạng thái lân cận.
- Chọn ngẫu nhiên một trạng thái.
- So sánh heuristic giữa trạng thái hiện tại và trạng thái mới.
- Nếu trạng thái mới tốt hơn sẽ được chấp nhận.
- Nếu trạng thái mới kém hơn vẫn có thể được chấp nhận theo xác suất.

Xác suất này phụ thuộc vào:

```text
Nhiệt độ hiện tại (T)
```

Nhiệt độ giảm dần theo thời gian cho đến khi đạt ngưỡng tối thiểu.

---

# Hàm heuristic

Project sử dụng:

```text
Misplaced Tiles
```

(Hàm đếm số ô sai vị trí)

---

## Công thức

```text
h(n) = số ô sai vị trí
```

Không tính ô trống `0`.

---

# Ví dụ Heuristic

## Trạng thái hiện tại

```text
1 2 3
4 0 6
7 5 8
```

## Goal

```text
1 2 3
4 5 6
7 8 0
```

Các ô sai vị trí:

- Ô 5
- Ô 8

```text
h(n) = 2
```

---

# Công thức xác suất

Khi trạng thái mới không tốt hơn:

```text
Δ = h(next) - h(current)
```

Xác suất chấp nhận:

```text
P = e^(-Δ/T)
```

Trong đó:

- Δ là độ thay đổi heuristic.
- T là nhiệt độ hiện tại.

---

# Quy trình hoạt động

1. Khởi tạo trạng thái đầu.
2. Đặt nhiệt độ ban đầu.
3. Sinh các trạng thái lân cận.
4. Chọn ngẫu nhiên một trạng thái.
5. Tính giá trị heuristic.
6. Quyết định chấp nhận hoặc từ chối trạng thái mới.
7. Giảm nhiệt độ.
8. Lặp lại cho đến khi:
   - Tìm thấy Goal.
   - Nhiệt độ nhỏ hơn ngưỡng tối thiểu.
   - Đạt số bước tối đa.

---

# Pseudocode

```text
function SimulatedAnnealing(start):

    current = start
    T = T0

    while T > Tmin:

        if current == Goal:
            return Success

        next = random neighbor

        Δ = h(next) - h(current)

        if Δ < 0:
            current = next

        else:
            P = e^(-Δ/T)

            if random() < P:
                current = next

        T = T × α

    return current
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
  - Heuristic hiện tại h(n)
  - Final Temperature
  - Visited States

---

# Highlight đặc biệt

## Ô đúng vị trí

- Màu trắng.

## Ô sai vị trí

- Màu đỏ nhạt.

## Ô trống

- Màu xanh lá nhạt.
- Viền nét đứt.

---

# Các thành phần chính

| Hàm | Chức năng |
|------|------------|
| `misplaced()` | Tính số ô sai vị trí |
| `get_neighbors()` | Sinh trạng thái con |
| `simulated_annealing()` | Thuật toán Simulated Annealing |
| `random_board()` | Sinh trạng thái ngẫu nhiên |
| `draw()` | Vẽ bàn cờ |
| `animate()` | Animation lời giải |
| `shuffle()` | Trộn puzzle |
| `solve()` | Chạy thuật toán |

---

# Ví dụ

## Input

```text
2 8 3
1 6 4
7 0 5
```

---

## Quá trình

Giả sử:

```text
h(current) = 4
h(next) = 5
```

Khi đó:

```text
Δ = 1
```

Xác suất chấp nhận:

```text
P = e^(-1/T)
```

Thuật toán sử dụng xác suất này để quyết định có chuyển sang trạng thái mới hay không.

---

## Output

```text
✓ SOLVED
```

hoặc

```text
✗ Stuck
```

---

# Công nghệ sử dụng

- Python 3
- Tkinter
- Random
- Math
- Time

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python Simulated_Annealing.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Simulated Annealing
```

Đặc điểm:

- Thuật toán tìm kiếm cục bộ.
- Sử dụng nhiệt độ để điều khiển tìm kiếm.
- Đánh giá trạng thái bằng heuristic.
- Chấp nhận trạng thái mới dựa trên xác suất.
- Nhiệt độ giảm dần trong quá trình thực hiện.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**