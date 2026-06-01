# Steepest-Ascent Hill Climbing (Manhattan Distance) - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
Steepest-Ascent Hill Climbing
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán Hill Climbing hoạt động dựa trên:

- Hàm heuristic h(n)
- Luôn chọn trạng thái tốt nhất trong các trạng thái lân cận

---

# Trạng thái đích

```text
1 2 3
4 5 6
7 8 0
```

Trong đó:

- 0 là ô trống.

---

# Ý tưởng thuật toán

Thuật toán Steepest-Ascent Hill Climbing là một thuật toán:

```text
Local Search
```

Thay vì xét toàn bộ cây tìm kiếm, thuật toán chỉ quan tâm đến:

```text
Trạng thái hiện tại
```

và

```text
Các trạng thái lân cận
```

Khác với Simple Hill Climbing:

```text
Simple Hill Climbing
→ chọn trạng thái tốt hơn đầu tiên tìm thấy

Steepest-Ascent Hill Climbing
→ xét toàn bộ hàng xóm
→ chọn trạng thái có heuristic tốt nhất
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

- Ô 5 lệch 1 ô
- Ô 8 lệch 1 ô

```text
h(n) = 2
```

---

# Quy trình hoạt động

1. Chọn trạng thái hiện tại.
2. Tính heuristic hiện tại.
3. Sinh toàn bộ trạng thái lân cận.
4. Tính heuristic cho từng trạng thái con.
5. Chọn trạng thái có heuristic nhỏ nhất.
6. Nếu heuristic mới tốt hơn:

   - Di chuyển tới trạng thái đó.

7. Nếu không có trạng thái nào tốt hơn:

   - Dừng tìm kiếm.

8. Lặp lại cho đến khi:

   - Tìm thấy Goal.
   - Hoặc mắc kẹt tại Local Optimum.

---

# Pseudocode

```text
function Steepest_Ascent_Hill_Climbing(Start, Goal):

    Current = Start

    while Current ≠ Goal:

        sinh toàn bộ trạng thái lân cận

        Best = trạng thái có heuristic nhỏ nhất

        nếu h(Best) < h(Current):
            Current = Best
        ngược lại:
            STOP

    return lời giải
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
  - Cost hiện tại

---

# Highlight đặc biệt

## Ô đúng vị trí

- Màu trắng.

## Ô sai vị trí

- Màu đỏ nhạt.

## Ô trống

- Hiển thị màu khác nhau tùy theo trọng số vị trí.

---

# Các thành phần chính

| Hàm | Chức năng |
|------|------|
| manhattan() | Tính heuristic Manhattan |
| get_neighbors() | Sinh trạng thái con |
| hill_climbing() | Thuật toán Steepest-Ascent Hill Climbing |
| draw() | Vẽ bàn cờ |
| animate() | Animation lời giải |
| shuffle() | Random board |
| solve() | Chạy thuật toán |

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

Steepest-Ascent Hill Climbing sẽ:

```text
Xét toàn bộ hàng xóm

Chọn trạng thái có Manhattan Distance nhỏ nhất
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

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python Steepest_Ascent_Hill_Climbing.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Steepest-Ascent Hill Climbing
```

Đặc điểm:

- Là thuật toán tìm kiếm cục bộ.
- Chỉ lưu một trạng thái hiện tại.
- Bộ nhớ sử dụng rất thấp.
- Nhanh hơn nhiều thuật toán tìm kiếm có lưu cây.
- Luôn chọn hàng xóm tốt nhất.
- Không đảm bảo tìm được lời giải.
- Có thể mắc kẹt tại Local Optimum.
- Manhattan Distance giúp đánh giá mức độ gần Goal.

---

# Hạn chế

Steepest-Ascent Hill Climbing có thể gặp:

## Local Optimum

```text
Không có hàng xóm nào tốt hơn
nhưng vẫn chưa tới Goal.
```

## Plateau

```text
Nhiều trạng thái có cùng heuristic.
```

## Ridge

```text
Muốn tới Goal phải đi qua
một trạng thái có heuristic lớn hơn.
```

Do thuật toán chỉ chấp nhận:

```text
h(new) < h(current)
```

nên sẽ dừng lại ngay khi gặp các trường hợp trên.

---

# So sánh với Simple Hill Climbing

| Simple HC | Steepest-Ascent HC |
|------------|------------|
| Chọn trạng thái tốt hơn đầu tiên tìm thấy | Xét toàn bộ hàng xóm |
| Ít tính toán hơn | Tính toán nhiều hơn |
| Dễ phụ thuộc thứ tự sinh node | Ổn định hơn |
| Dễ bỏ lỡ lựa chọn tốt nhất | Luôn chọn lựa chọn tốt nhất hiện tại |

---

# Tác giả

**24133077 - Phạm Quý Vỹ**