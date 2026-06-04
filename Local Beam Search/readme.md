# Local Beam Search (Manhattan Distance) - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
Local Beam Search
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán Local Beam Search hoạt động bằng cách:

* Theo dõi đồng thời nhiều trạng thái triển vọng.
* Sinh tất cả trạng thái con từ các trạng thái hiện tại.
* Đánh giá bằng Manhattan Distance.
* Giữ lại `k` trạng thái tốt nhất để tiếp tục tìm kiếm.
* Lặp lại cho đến khi tìm thấy trạng thái đích hoặc không còn trạng thái mới.

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

Khác với Hill Climbing chỉ theo dõi một trạng thái duy nhất, Local Beam Search duy trì nhiều trạng thái cùng lúc.

Trong chương trình:

```text
BEAM_WIDTH = 4 ( có thể thay đổi theo ý muốn)
```

Nghĩa là sau mỗi lần mở rộng, thuật toán sẽ giữ lại:

```text
4 trạng thái có heuristic nhỏ nhất
```

để tiếp tục tìm kiếm.

Nhờ theo dõi nhiều hướng tìm kiếm đồng thời, thuật toán có khả năng thoát khỏi Local Optimum tốt hơn Hill Climbing.

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
Σ (|x - goal_x| + |y - goal_y|)
```

Trong đó:

* `(x, y)` là vị trí hiện tại của ô số.
* `(goal_x, goal_y)` là vị trí đích của ô số đó.

Tổng khoảng cách Manhattan của tất cả các ô chính là giá trị heuristic.

---

# Ví dụ Manhattan Distance

## Trạng thái hiện tại

```text
1 2 3
4 0 6
7 5 8
```

## Tính heuristic

* Ô 5 lệch 1 ô.
* Ô 8 lệch 1 ô.

```text
h(n) = 2
```

---

# Quy trình hoạt động

1. Khởi tạo Beam với trạng thái bắt đầu.
2. Kiểm tra Goal.
3. Sinh tất cả trạng thái con từ các trạng thái trong Beam.
4. Loại bỏ các trạng thái đã thăm.
5. Tính Manhattan Distance cho các trạng thái mới.
6. Sắp xếp theo heuristic tăng dần.
7. Giữ lại `k` trạng thái tốt nhất.
8. Lặp lại cho đến khi:

   * Tìm thấy Goal.
   * Hoặc không còn trạng thái mới để mở rộng.

---

# Pseudocode

```text
function LocalBeamSearch(start, k):

    beam ← {start}

    while beam ≠ ∅:

        if Goal ∈ beam:
            return Success

        successors ← ∅

        for state in beam:
            successors ← successors ∪ neighbors(state)

        loại bỏ trạng thái đã thăm

        sắp xếp successors theo h(n)

        beam ← k trạng thái có h(n) nhỏ nhất

    return Failure
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
  * Beam Width
  * Visited States

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

| Hàm                   | Chức năng                    |
| --------------------- | ---------------------------- |
| `manhattan()`         | Tính Manhattan Distance      |
| `get_neighbors()`     | Sinh trạng thái con          |
| `local_beam_search()` | Thuật toán Local Beam Search |
| `random_board()`      | Sinh trạng thái ngẫu nhiên   |
| `draw()`              | Vẽ bàn cờ                    |
| `animate()`           | Animation lời giải           |
| `shuffle()`           | Trộn puzzle                  |
| `solve()`             | Chạy thuật toán              |

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

Thuật toán sẽ:

```text
Giữ lại 4 trạng thái có Manhattan Distance nhỏ nhất
```

sau mỗi lần mở rộng và tiếp tục tìm kiếm từ các trạng thái đó.

---

## Output

```text
✓ SOLVED
```

hoặc

```text
✗ Stuck
```

nếu không còn trạng thái mới để mở rộng.

---

# Công nghệ sử dụng

* Python 3
* Tkinter
* Random
* Time

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python Local_Beam_Search.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Local Beam Search
```

Đặc điểm:

* Là thuật toán tìm kiếm cục bộ.
* Theo dõi nhiều trạng thái cùng lúc.
* Dùng Manhattan Distance làm heuristic.
* Giảm nguy cơ mắc kẹt tại Local Optimum so với Hill Climbing.
* Không đảm bảo tìm được lời giải tối ưu.
* Không đảm bảo luôn tìm được Goal.

---

# Ưu điểm

* Tìm kiếm theo nhiều hướng đồng thời.
* Hiệu quả hơn Hill Climbing đơn thuần.
* Dễ cài đặt.
* Dễ trực quan hóa.

---

# Nhược điểm

* Không đảm bảo tối ưu.
* Có thể bỏ lỡ lời giải tốt.
* Hiệu quả phụ thuộc Beam Width.
* Các Beam có thể hội tụ về cùng một vùng tìm kiếm.
* Vẫn có khả năng thất bại trong một số trường hợp.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**
