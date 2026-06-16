# CSP + Forward Checking - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng kỹ thuật:

```text
Constraint Satisfaction Problem (CSP)
```

kết hợp với:

```text
Forward Checking
```

và giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán được sử dụng để tìm chuỗi hành động đưa trạng thái hiện tại về trạng thái đích đồng thời loại bỏ sớm các nhánh không khả thi thông qua kỹ thuật Forward Checking.

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

Bài toán được mô hình hóa dưới dạng:

```text
Constraint Satisfaction Problem (CSP)
```

Trong đó:

### Variables

```text
Move₁, Move₂, Move₃, ...
```

Mỗi biến đại diện cho một hành động tại một bước tìm kiếm.

---

### Domain

```text
{UP, DOWN, LEFT, RIGHT}
```

Mỗi biến có thể nhận một trong bốn hướng di chuyển.

---

### Constraints

```text
1. Hành động phải hợp lệ.
2. Không được tạo chu trình.
3. Không được quay lại trạng thái đã thăm.
4. Goal State kết thúc tìm kiếm.
```

---

# Forward Checking

Sau khi gán giá trị cho:

```text
Move_i
```

thuật toán sẽ kiểm tra trước miền giá trị của:

```text
Move_(i+1)
```

Nếu:

```text
Domain(Move_(i+1)) = ∅
```

thì nhánh hiện tại bị loại bỏ ngay lập tức.

---

# Hàm heuristic

Project sử dụng:

```text
Misplaced Tiles
```

---

## Công thức

Đếm số ô sai vị trí:

```text
h(n) =
Số ô khác Goal
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

# Quy trình hoạt động

1. Bắt đầu từ trạng thái Start.
2. Tạo biến Move₁.
3. Thử các giá trị trong Domain.
4. Kiểm tra tính hợp lệ.
5. Kiểm tra chu trình.
6. Thực hiện Forward Checking.
7. Nếu Domain kế tiếp rỗng → Prune.
8. Nếu còn giá trị → tiếp tục đệ quy.
9. Kiểm tra Goal State.
10. Trả về lời giải.

---

# Minh họa CSP

```text
Move₁
 │
 ├── UP
 ├── DOWN
 ├── LEFT
 └── RIGHT
```

Sau khi gán:

```text
Move₁ = DOWN
```

Forward Checking tính:

```text
Domain(Move₂)
```

Nếu:

```text
Domain(Move₂) = {}
```

thì:

```text
FC_PRUNE
```

---

# Pseudocode

```text
BACKTRACK(state)

    if GOAL(state)
        return SUCCESS

    for action in ACTIONS

        next_state = APPLY(action)

        if invalid
            continue

        if cycle
            continue

        domain_next =
            FORWARD_CHECKING(next_state)

        if domain_next = ∅
            prune

        BACKTRACK(next_state)

    return FAILURE
```

---

# Các loại sự kiện

## INVALID

```text
Hành động vượt ra ngoài bàn cờ.
```

Ví dụ:

```text
UP tại hàng đầu.
```

---

## CYCLE

```text
Trạng thái đã tồn tại trong visited.
```

Vi phạm ràng buộc:

```text
No-repeat Constraint
```

---

## FC_PRUNE

```text
Domain(Move_(i+1)) = ∅
```

Forward Checking cắt bỏ nhánh.

---

## OK

```text
Hành động hợp lệ.
```

Tiếp tục tìm kiếm.

---

## GOAL

```text
Đạt trạng thái đích.
```

Thuật toán dừng.

---

# Cấu trúc tìm kiếm

```text
Move₁
 │
 ├── Move₂
 │     │
 │     ├── Move₃
 │     └── FC_PRUNE
 │
 ├── Move₂
 │     └── GOAL
 │
 └── CYCLE
```

---

# Chức năng giao diện

## Bao gồm

* Random trạng thái đầu.
* Solve tự động.
* Step-by-step.
* Animation quá trình tìm kiếm.
* Hiển thị:

  * Nodes
  * Moves
  * Time
  * Current Variable
  * Path
  * h(n)
  * Forward Checking Domain

---

# Thông tin hiển thị

## Nodes

```text
Số node đã mở rộng
```

---

## Moves

```text
Số bước lời giải
```

---

## Time

```text
Thời gian thực thi
```

---

## Variable

```text
Biến CSP hiện tại
```

Ví dụ:

```text
Move_5
```

---

## Path

```text
Chuỗi hành động đã thực hiện
```

Ví dụ:

```text
[DOWN, LEFT, UP]
```

---

## h(n)

```text
Số ô sai vị trí
```

---

# Các thành phần chính

| Hàm                     | Chức năng                  |
| ----------------------- | -------------------------- |
| `apply_move()`          | Thực hiện hành động        |
| `misplaced()`           | Tính heuristic             |
| `random_board()`        | Sinh trạng thái ngẫu nhiên |
| `fc_csp_search()`       | CSP + Forward Checking     |
| `forward_checking()`    | Tính miền kế tiếp          |
| `bt()`                  | Backtracking Search        |
| `_draw_board()`         | Vẽ bàn cờ                  |
| `_update_domain_grid()` | Hiển thị Domain            |
| `animate()`             | Chạy Animation             |
| `solve()`               | Giải bài toán              |

---

# Công nghệ sử dụng

* Python 3
* Tkinter
* Constraint Satisfaction Problem (CSP)
* Backtracking Search
* Forward Checking

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python FC.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Constraint Satisfaction Problem
```

và

```text
Forward Checking
```

Đặc điểm:

* Biểu diễn bài toán dưới dạng CSP.
* Gán giá trị cho các biến Moveᵢ.
* Kiểm tra ràng buộc ngay khi gán.
* Loại bỏ sớm các miền không khả thi.
* Giảm số node phải duyệt.
* Tăng hiệu quả Backtracking Search.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**
