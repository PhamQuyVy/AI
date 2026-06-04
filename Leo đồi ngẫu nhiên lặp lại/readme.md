# Random Restart Hill Climbing (Manhattan Distance) - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
Random Restart Hill Climbing
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán hoạt động dựa trên:

* Hàm heuristic `h(n)`
* Chỉ chọn các trạng thái tốt hơn trạng thái hiện tại
* Khi bị kẹt tại Local Optimum sẽ khởi động lại từ trạng thái ngẫu nhiên khác

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

Hill Climbing là thuật toán tìm kiếm cục bộ.

Tại mỗi bước:

```text
Chỉ di chuyển đến trạng thái có heuristic tốt hơn
```

Nếu không tồn tại trạng thái tốt hơn:

```text
Local Optimum
```

thuật toán sẽ:

```text
Random Restart
```

từ một trạng thái hợp lệ ngẫu nhiên khác.

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

* Ô `5` lệch 1 ô
* Ô `8` lệch 1 ô

```text
h(n) = 2
```

---

# Random Restart Hill Climbing

## Hill Climbing thông thường

```text
Current State
      ↓
Best Neighbor
      ↓
Best Neighbor
      ↓
Local Optimum
      ↓
STOP
```

---

## Random Restart Hill Climbing

```text
Current State
      ↓
Best Neighbor
      ↓
Local Optimum
      ↓
Random Restart
      ↓
New State
      ↓
Continue Search
```

---

# Quy trình hoạt động

1. Sinh trạng thái bắt đầu.
2. Tính heuristic hiện tại.
3. Sinh các trạng thái lân cận.
4. Chọn các trạng thái có:

```text
h(new) < h(current)
```

5. Chọn ngẫu nhiên một trạng thái tốt hơn.
6. Nếu không có trạng thái tốt hơn:

```text
Restart
```

7. Lặp lại cho tới khi:

   * Tìm thấy Goal
   * Hoặc vượt quá số lần Restart cho phép

---

# Pseudocode

```text
function Random_Hill_Climbing(start):

    current = start

    while not goal:

        neighbors = get_neighbors(current)

        better_neighbors =
            neighbor có h nhỏ hơn

        if better_neighbors tồn tại:

            current =
                random(better_neighbors)

        else:

            restart từ trạng thái ngẫu nhiên
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
  * Heuristic hiện tại
  * Số lần Restart

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

| Hàm                      | Chức năng                               |
| ------------------------ | --------------------------------------- |
| `manhattan()`            | Tính Manhattan Distance                 |
| `get_neighbors()`        | Sinh trạng thái con                     |
| `random_hill_climbing()` | Thuật toán Random Restart Hill Climbing |
| `random_board()`         | Sinh trạng thái ngẫu nhiên              |
| `draw()`                 | Vẽ bàn cờ                               |
| `animate()`              | Animation lời giải                      |
| `shuffle()`              | Trộn puzzle                             |
| `solve()`                | Chạy thuật toán                         |

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

Thuật toán ưu tiên:

```text
Neighbor có Manhattan Distance nhỏ hơn
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

# Trường hợp mắc kẹt

Ví dụ:

```text
Current h(n)=4
```

Tất cả neighbor:

```text
h(n)=5
h(n)=6
h(n)=5
```

Không có trạng thái tốt hơn.

Thuật toán sẽ:

```text
Random Restart
```

và tiếp tục tìm kiếm từ trạng thái mới.

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
python Leo đồi ngẫu nhiên lặp lại.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Random Restart Hill Climbing
```

Đặc điểm:

* Tìm kiếm cục bộ.
* Sử dụng heuristic Manhattan Distance.
* Tiêu tốn ít bộ nhớ.
* Có thể bị mắc kẹt tại Local Optimum.
* Random Restart giúp tăng khả năng tìm được Goal.
* Không đảm bảo tìm được lời giải tối ưu.

---

# Ưu điểm

* Cài đặt đơn giản.
* Tốc độ nhanh.
* Tiết kiệm bộ nhớ.
* Giảm nguy cơ kẹt Local Optimum nhờ Restart.

---

# Nhược điểm

* Không đảm bảo tối ưu.
* Có thể cần nhiều lần Restart.
* Không luôn tìm được Goal trong giới hạn thời gian.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**
