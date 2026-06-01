# Simple Hill Climbing (Manhattan Distance) - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
Simple Hill Climbing
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán Hill Climbing hoạt động dựa trên:

* Hàm heuristic `h(n)`
* Luôn tìm trạng thái tốt hơn trạng thái hiện tại

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

Thuật toán Simple Hill Climbing là một thuật toán:

```text
Local Search
```

Thay vì lưu toàn bộ cây tìm kiếm, thuật toán chỉ quan tâm đến:

```text
Trạng thái hiện tại
```

và

```text
Các trạng thái lân cận
```

Thuật toán sẽ:

* Sinh các trạng thái kề.
* Duyệt lần lượt các trạng thái đó.
* Nếu gặp trạng thái có heuristic tốt hơn thì di chuyển ngay.
* Nếu không tìm được trạng thái tốt hơn thì dừng.

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

* Ô `5` lệch 1 ô
* Ô `8` lệch 1 ô

```text
h(n) = 2
```

---

# Quy trình hoạt động

1. Chọn trạng thái hiện tại.
2. Tính heuristic hiện tại.
3. Sinh các trạng thái lân cận.
4. Duyệt từng trạng thái con.
5. Nếu tìm thấy trạng thái có heuristic nhỏ hơn:

   * Di chuyển tới trạng thái đó.
6. Nếu không tìm thấy trạng thái tốt hơn:

   * Dừng tìm kiếm.
7. Lặp lại cho đến khi:

   * Tìm thấy Goal.
   * Hoặc mắc kẹt tại Local Optimum.

---

# Pseudocode

```text
function Hill_Climbing(Start, Goal):

    Current = Start

    while Current ≠ Goal:

        sinh các trạng thái lân cận

        tìm trạng thái đầu tiên
        có heuristic tốt hơn

        nếu tìm thấy:
            Current = trạng thái mới
        ngược lại:
            STOP

    return lời giải
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
  * Heuristic hiện tại `h(n)`
  * Cost hiện tại

---

# Highlight đặc biệt

## Ô đúng vị trí

* Màu trắng.

## Ô sai vị trí

* Màu đỏ nhạt.

## Ô trống

* Hiển thị màu khác nhau tùy theo trọng số vị trí.

---

# Các thành phần chính

| Hàm               | Chức năng                |
| ----------------- | ------------------------ |
| `manhattan()`     | Tính heuristic Manhattan |
| `get_neighbors()` | Sinh trạng thái con      |
| `hill_climbing()` | Thuật toán Hill Climbing |
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

Hill Climbing sẽ chọn:

```text
Trạng thái đầu tiên có Manhattan Distance nhỏ hơn
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

* Python 3
* Tkinter

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python Hill_Climbing.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Simple Hill Climbing
```

Đặc điểm:

* Là thuật toán tìm kiếm cục bộ.
* Bộ nhớ sử dụng rất thấp.
* Tốc độ thực thi nhanh.
* Không đảm bảo tìm được lời giải.
* Có thể mắc kẹt tại Local Optimum.
* Có thể dừng trước khi đạt Goal.
* Manhattan Distance giúp đánh giá mức độ gần trạng thái đích.

---

# Hạn chế

Hill Climbing có thể gặp:

## Local Optimum

```text
Trạng thái hiện tại tốt hơn tất cả trạng thái lân cận
nhưng chưa phải Goal.
```

## Plateau

```text
Nhiều trạng thái có cùng heuristic.
```

## Ridge

```text
Cần đi qua trạng thái xấu hơn
mới có thể tới Goal.
```

Do đó chương trình không đảm bảo luôn tìm được lời giải.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**
