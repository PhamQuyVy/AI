# 8 Puzzle Solver using CSP + AC-3

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng phương pháp:

```text
Constraint Satisfaction Problem (CSP)
```

kết hợp:

```text
AC-3 (Arc Consistency Algorithm)
Backtracking Search
```

và giao diện đồ họa được xây dựng bằng:

```text
Tkinter
```

Mục tiêu của chương trình là tìm chuỗi hành động đưa trạng thái hiện tại về trạng thái đích thông qua việc mô hình hóa 8 Puzzle thành bài toán CSP.

---

# Trạng thái đích

```text
1 2 3
4 5 6
7 8 0
```

Trong đó:

```text
0
```

là ô trống.

---

# Mô hình hóa CSP

Thay vì xem 8 Puzzle là bài toán tìm kiếm trạng thái truyền thống, chương trình chuyển đổi thành CSP.

## Variables

```text
Move1
Move2
Move3
...
Movek
```

Mỗi biến đại diện cho một hành động tại một bước.

---

## Domains

Mỗi biến có miền giá trị:

```text
{UP, DOWN, LEFT, RIGHT}
```

---

## Constraints

### Constraint 1

Không được đi ra ngoài bàn cờ.

Ví dụ:

```text
Blank ở hàng đầu

Movei ≠ UP
```

---

### Constraint 2

Không được quay lại trạng thái đã thăm.

```text
next_state ∉ visited
```

---

### Constraint 3

Chuỗi hành động phải dẫn tới Goal State.

```text
Result(Start, Move1...Movek)
=
Goal
```

---

# Thuật toán AC-3

AC-3 (Arc Consistency Algorithm) được sử dụng để:

```text
Loại bỏ các giá trị không thỏa mãn ràng buộc khỏi domain.
```

Mục tiêu:

```text
Giảm không gian tìm kiếm
(Constraint Propagation)
```

AC-3 không trực tiếp tìm lời giải.

Nó chỉ giúp:

```text
Prune Domain
```

trước khi Backtracking Search được thực hiện.

---

# Quy trình hoạt động

```text
Start State
      │
      ▼
CSP Formulation
      │
      ▼
AC-3
(Arc Consistency)
      │
      ▼
Domain Reduction
      │
      ▼
Backtracking Search
      │
      ▼
Goal State
```

---

# Hàm heuristic

Chương trình sử dụng:

```text
Misplaced Tiles
```

---

## Công thức

```text
h(n) =
Số ô sai vị trí
(không tính ô trống)
```

---

## Ví dụ

```text
1 2 3
4 0 6
7 5 8
```

So với Goal:

```text
1 2 3
4 5 6
7 8 0
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

# Arc Consistency

Một cung:

```text
(Xi, Xj)
```

được gọi là Arc Consistent nếu:

```text
∀ value ∈ Domain(Xi)

tồn tại ít nhất một giá trị
trong Domain(Xj)

thỏa mãn Constraint(Xi, Xj)
```

Nếu không tồn tại:

```text
value
```

đó sẽ bị loại khỏi domain.

---

# Pseudocode AC-3

```text
AC3(csp)

    queue ← all arcs

    while queue not empty

        (Xi, Xj) ← pop(queue)

        if REVISE(Xi, Xj)

            if Domain(Xi) = ∅
                return FAILURE

            for each Xk neighbor Xi

                add(Xk, Xi)

    return SUCCESS
```

---

# Pseudocode Backtracking

```text
BACKTRACKING(assignment)

    if complete
        return assignment

    select variable

    for each value in domain

        if consistent

            assign value

            result ← BACKTRACKING()

            if success
                return result

    return FAILURE
```

---

# Chức năng giao diện

## Bao gồm

* Random trạng thái đầu.
* Solve tự động.
* Chạy từng bước.
* Animation quá trình tìm kiếm.
* Hiển thị Arc Consistency.
* Hiển thị Domain.
* Hiển thị Backtracking.
* Hiển thị Goal State.

---

# Thông tin hiển thị

## Nodes

```text
Số node đã mở rộng
```

---

## Steps

```text
Số bước lời giải
```

---

## Time

```text
Thời gian thực thi
```

---

## h(n)

```text
Số ô sai vị trí
```

---

# Các thành phần chính

| Hàm              | Chức năng               |
| ---------------- | ----------------------- |
| `apply_move()`   | Thực hiện hành động     |
| `misplaced()`    | Tính heuristic          |
| `is_solvable()`  | Kiểm tra khả năng giải  |
| `ac3()`          | Arc Consistency         |
| `revise()`       | Loại bỏ giá trị vi phạm |
| `backtracking()` | Tìm lời giải            |
| `draw_board()`   | Vẽ bàn cờ               |
| `animate()`      | Hiển thị quá trình giải |
| `solve()`        | Thực thi thuật toán     |

---

# Ví dụ

## Input

```text
1 2 3
4 0 6
7 5 8
```

---

## Output

```text
1 2 3
4 0 6
7 5 8
```

↓

```text
DOWN
```

↓

```text
1 2 3
4 5 6
7 0 8
```

↓

```text
RIGHT
```

↓

```text
1 2 3
4 5 6
7 8 0
```

---

# Công nghệ sử dụng

* Python 3
* Tkinter
* CSP
* AC-3
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
python AC_3.ipynb
```

---

# Kiến thức AI áp dụng

Project áp dụng:

```text
Constraint Satisfaction Problem (CSP)
```

và:

```text
AC-3 (Arc Consistency)
```

Đặc điểm:

* Biểu diễn bài toán dưới dạng CSP.
* Duy trì Arc Consistency.
* Loại bỏ giá trị không hợp lệ khỏi Domain.
* Giảm không gian tìm kiếm.
* Kết hợp Backtracking Search để tìm lời giải.

Lưu ý:

```text
AC-3 không phải thuật toán giải 8 Puzzle chuẩn.
Trong project này, 8 Puzzle được mô hình hóa thành CSP nhằm minh họa Constraint Propagation và Arc Consistency.
```

---

# Tác giả

**24133077 – Phạm Quý Vỹ**
