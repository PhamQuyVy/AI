# Random Hill Climbing (Manhattan Distance) - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
Random Hill Climbing
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán hoạt động dựa trên:

* Hàm heuristic `h(n)`
* Chỉ chọn các trạng thái tốt hơn trạng thái hiện tại
* Nếu có nhiều lựa chọn tốt hơn, chọn ngẫu nhiên một trạng thái
* Không sử dụng Restart

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

Random Hill Climbing là biến thể của Hill Climbing.

Thay vì luôn chọn trạng thái tốt nhất, thuật toán:

```text
Chọn ngẫu nhiên một trạng thái có heuristic nhỏ hơn
```

Điều này giúp tạo ra các đường đi khác nhau mỗi lần chạy.

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

Tổng khoảng cách của tất cả các ô số tới vị trí đích.

---

# Ví dụ Manhattan Distance

## Trạng thái hiện tại

```text
1 2 3
4 0 6
7 5 8
```

## Tính heuristic

* Ô 5 lệch 1 ô
* Ô 8 lệch 1 ô

```text
h(n) = 2
```

---

# Quy trình hoạt động

1. Bắt đầu từ trạng thái đầu.
2. Tính heuristic hiện tại.
3. Sinh các trạng thái lân cận.
4. Chọn các trạng thái có:

```text
h(new) < h(current)
```

5. Chọn ngẫu nhiên một trạng thái trong danh sách đó.
6. Tiếp tục tìm kiếm.
7. Dừng khi:

   * Tìm thấy Goal.
   * Hoặc không còn trạng thái tốt hơn.

---

# Pseudocode

```text
function Random_Hill_Climbing(start):

    current = start

    while current != Goal:

        neighbors = get_neighbors(current)

        better = []

        for n in neighbors:

            if h(n) < h(current):
                better.add(n)

        if better rỗng:
            return Stuck

        current = random.choice(better)

    return Success
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

  * Steps
  * Time
  * Heuristic hiện tại `h(n)`

---

# Highlight đặc biệt

## Ô đúng vị trí

* Màu trắng.

## Ô sai vị trí

* Màu đỏ nhạt.

## Ô trống

* Màu xanh lá nhạt.
* Viền nét đứt.

---

# Các thành phần chính

| Hàm                      | Chức năng                       |
| ------------------------ | ------------------------------- |
| `manhattan()`            | Tính Manhattan Distance         |
| `get_neighbors()`        | Sinh trạng thái con             |
| `random_hill_climbing()` | Thuật toán Random Hill Climbing |
| `random_board()`         | Sinh trạng thái ngẫu nhiên      |
| `draw()`                 | Vẽ bàn cờ                       |
| `animate()`              | Animation lời giải              |
| `shuffle()`              | Trộn puzzle                     |
| `solve()`                | Chạy thuật toán                 |

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

Thuật toán chọn ngẫu nhiên một trạng thái có:

```text
h(n) nhỏ hơn trạng thái hiện tại
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

# Ví dụ Log

```text
1. DOWN  h(n)=1
2. RIGHT h(n)=0
```

---

# Trường hợp bị kẹt

Ví dụ:

```text
Current h(n)=4
```

Các trạng thái lân cận:

```text
h(n)=5
h(n)=6
h(n)=5
```

Không có trạng thái nào tốt hơn.

Thuật toán sẽ:

```text
STOP
```

và hiển thị:

```text
✗ Stuck (local optimum)
```

---

# Công nghệ sử dụng

* Python 3
* Tkinter
* Random Library
* Time Library

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python Leo đồi ngẫu nhiên.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Random Hill Climbing
```

Đặc điểm:

* Tìm kiếm cục bộ.
* Dùng Manhattan Distance làm heuristic.
* Chọn ngẫu nhiên một trạng thái tốt hơn.
* Tốn rất ít bộ nhớ.
* Không đảm bảo tối ưu.
* Dễ mắc kẹt tại Local Optimum.

---

# Ưu điểm

* Cài đặt đơn giản.
* Tốc độ nhanh.
* Bộ nhớ thấp.
* Dễ trực quan hóa.

---

# Nhược điểm

* Không đảm bảo tìm được Goal.
* Không đảm bảo tối ưu.
* Dễ mắc kẹt Local Optimum.
* Kết quả có thể khác nhau giữa các lần chạy.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**
