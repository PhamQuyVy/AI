# Pure Backtracking Search - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
Pure Backtracking Search
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán Backtracking thực hiện tìm kiếm theo chiều sâu (Depth First Search) và sử dụng cơ chế quay lui (Backtrack) để khám phá không gian trạng thái của bài toán.

---

# Trạng thái đích

```text
1 2 3
4 5 6
7 8 0
```

Trong đó:

* `0` là ô trống.
* Các số còn lại là các quân cờ cần được sắp xếp đúng vị trí.

---

# Ý tưởng thuật toán

Thuật toán Backtracking hoạt động theo nguyên tắc:

1. Bắt đầu từ trạng thái hiện tại.
2. Sinh các trạng thái kế tiếp.
3. Chọn một trạng thái con để tiếp tục tìm kiếm.
4. Nếu gặp trạng thái đích thì kết thúc.
5. Nếu nhánh hiện tại không dẫn tới lời giải:

   * Quay lui về trạng thái cha.
6. Tiếp tục thử các nhánh còn lại.

Để tránh lặp vô hạn, chương trình sử dụng:

```text
ancestor_set
```

để lưu các trạng thái tổ tiên trên nhánh hiện tại.

---

# Hàm đánh giá

Chương trình hiển thị giá trị heuristic:

```text
Misplaced Tiles
```

Heuristic này chỉ dùng để quan sát trạng thái hiện tại trên giao diện, không ảnh hưởng đến quá trình Backtracking.

---

## Công thức

```text
h(n) =
Số ô sai vị trí
(không tính ô trống)
```

---

# Ví dụ

## Trạng thái hiện tại

```text
1 2 3
4 0 6
7 5 8
```

Các ô sai vị trí:

```text
5
8
```

Do đó:

```text
h(n) = 2
```

---

# Cấu trúc thuật toán

Mỗi khi mở rộng một node:

```text
ancestor_set.add(node)
```

Khi quay lui:

```text
ancestor_set.remove(node)
```

Mục đích:

* Tránh chu trình.
* Tránh quay lại trạng thái tổ tiên.
* Giảm số lượng trạng thái lặp.

---

# Quy trình hoạt động

```text
State hiện tại
      |
      v
Sinh trạng thái con
      |
      v
Chọn một trạng thái
      |
      v
Đệ quy xuống sâu hơn
      |
      +---- Goal ? ---- Yes ---> Kết thúc
      |
      No
      |
      v
Backtrack
      |
      v
Thử nhánh khác
```

---

# Pseudocode

```text
BACKTRACK(state)

    if state == GOAL:
        return SUCCESS

    if depth == 0:
        return FAILURE

    for action in ACTIONS:

        next_state = apply_action(state)

        if next_state không thuộc ancestor_set:

            ancestor_set.add(next_state)

            BACKTRACK(next_state)

            if SUCCESS:
                return SUCCESS

            ancestor_set.remove(next_state)

    return FAILURE
```

---

# Các hành động

Ô trống có thể thực hiện 4 hành động:

```text
UP
DOWN
LEFT
RIGHT
```

Ví dụ:

```text
1 2 3
4 0 6
7 5 8
```

Các nước đi hợp lệ:

```text
UP
DOWN
LEFT
RIGHT
```

---

# Thành phần chính

| Hàm                     | Chức năng                  |
| ----------------------- | -------------------------- |
| `misplaced()`           | Tính số ô sai vị trí       |
| `apply_action()`        | Sinh trạng thái mới        |
| `backtracking_search()` | Thuật toán Backtracking    |
| `draw()`                | Hiển thị bàn cờ            |
| `animate()`             | Animation lời giải         |
| `shuffle()`             | Sinh trạng thái ngẫu nhiên |
| `solve()`               | Thực thi thuật toán        |

---

# Chức năng giao diện

## Bao gồm

* Bàn cờ 8 Puzzle 3x3.
* Animation quá trình tìm kiếm.
* Shuffle trạng thái ngẫu nhiên.
* Solve tự động.
* Step-by-Step.
* Hiển thị:

  * Nodes Expanded
  * Execution Time
  * Solution Depth
  * Heuristic h(n)
  * Search Path
  * Trạng thái tìm kiếm hiện tại

---

# Hiển thị quá trình tìm kiếm

## Khởi đầu

```text
START
```

---

## Mở rộng node

```text
Mở rộng → ancestor_set
```

---

## Hoàn thành

```text
✓ SOLVED
```

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

```text
S
|
v
A
|
v
B
|
v
Goal
```

---

## Output

```text
1 2 3
4 0 6
7 5 8
```

↓

RIGHT

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
* Recursion
* Backtracking Search

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python Backtracking.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Pure Backtracking Search
```

Đặc điểm:

* Tìm kiếm theo chiều sâu.
* Sử dụng đệ quy.
* Có cơ chế quay lui.
* Tránh chu trình bằng ancestor_set.
* Không sử dụng heuristic để lựa chọn node.
* Có thể tìm được lời giải nếu độ sâu đủ lớn.
* Bộ nhớ sử dụng thấp.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**
