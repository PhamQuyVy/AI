# 8-Puzzle — Min-Conflicts

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
Min-Conflicts
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán được cài đặt theo:

```text
MIN-CONFLICTS
```

thuộc nhóm:

```text
Constraint Satisfaction Problems (CSP)
```

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

Min-Conflicts là thuật toán:

```text
Local Search for CSP
```

Ý tưởng chính:

1. Tạo một nghiệm đầy đủ ngẫu nhiên.
2. Xác định biến đang vi phạm ràng buộc.
3. Chọn giá trị làm giảm số xung đột nhiều nhất.
4. Cập nhật nghiệm.
5. Lặp lại cho tới khi không còn xung đột.

---

# Mô hình CSP

Bàn cờ được mô hình hóa thành CSP.

## Variables

```text
X0, X1, X2, ..., X8
```

Mỗi biến đại diện cho:

```text
Một vị trí trên bàn cờ
```

---

## Domain

```text
D(Xi) = {0,1,2,3,4,5,6,7,8}
```

---

## Constraints

### AllDiff

```text
Xi ≠ Xj
```

với:

```text
i ≠ j
```

Tất cả vị trí phải chứa giá trị khác nhau.

---

### Goal Constraint

```text
Xi = GOAL[i]
```

Ví dụ:

```text
X0 = 1
X1 = 2
X2 = 3
...
X8 = 0
```

---

# Hàm xung đột (Conflict Function)

Đối với một biến:

```text
Xi
```

gán giá trị:

```text
v
```

Số xung đột được tính:

```text
Conflict(Xi,v)

=

AllDiff Violations

+

Goal Violations
```

---

## AllDiff Violation

Nếu tồn tại:

```text
Xj = v
```

với:

```text
j ≠ i
```

thì phát sinh xung đột.

---

## Goal Violation

Nếu:

```text
v ≠ GOAL[i]
```

thì phát sinh thêm:

```text
1 conflict
```

---

# Pseudocode

```text
MIN-CONFLICTS(CSP,max_steps)

    current ← random complete assignment

    for i = 1 → max_steps

        if solution(current)
            return current

        var ← random conflicted variable

        value ← value minimizing conflicts

        current[var] ← value

    return FAILURE
```

---

# Hàm heuristic

Project hiển thị:

```text
Misplaced Tiles
```

---

## Công thức

```text
h(n)

=

Số ô sai vị trí

(không tính ô trống)
```

---

## Ví dụ

Trạng thái:

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

```text
Random Assignment
        │
        ▼
   Min-Conflicts
        │
        ▼
    Goal State
        │
        ▼
        BFS
        │
        ▼
     Animation
```

---

# Vai trò của BFS

Sau khi Min-Conflicts tìm được:

```text
1 2 3
4 5 6
7 8 0
```

chương trình sử dụng:

```text
Breadth First Search (BFS)
```

để tìm chuỗi di chuyển:

```text
Start → Goal
```

nhằm:

- Hiển thị animation
- Trình diễn lời giải
- Mô phỏng đường đi

---

# Chức năng giao diện

## Bao gồm

- Random trạng thái đầu
- Reset
- Solve
- Step-by-Step
- Animation
- Hiển thị Min-Conflicts Iterations

---

# Thông tin hiển thị

## Steps

```text
Số vòng lặp của Min-Conflicts
```

---

## Moves

```text
Số bước BFS từ Start đến Goal
```

---

## Depth

```text
Độ sâu lời giải BFS
```

---

## Time

```text
Thời gian thực thi
```

---

## h(n)

```text
Misplaced Tiles
```

---

# Các thành phần chính

| Hàm | Chức năng |
|------|------|
| `count_conflicts()` | Tính số xung đột |
| `conflicted_variables()` | Tìm biến vi phạm |
| `min_conflicts()` | Thuật toán Min-Conflicts |
| `bfs_path()` | Tìm đường đi Start → Goal |
| `misplaced()` | Tính heuristic |
| `apply_action()` | Thực hiện di chuyển |
| `draw()` | Vẽ bàn cờ |
| `animate()` | Hiển thị lời giải |
| `solve()` | Chạy thuật toán |

---

# Ví dụ

## Input

```text
1 2 3
4 0 6
7 5 8
```

---

## CSP Solution

```text
1 2 3
4 5 6
7 8 0
```

---

## BFS Path

```text
RIGHT
DOWN
LEFT
...
```

---

# Công nghệ sử dụng

- Python 3
- Tkinter
- CSP
- Min-Conflicts
- BFS

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python Min_conflicts.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Constraint Satisfaction Problems (CSP)
```

và:

```text
Min-Conflicts
```

Đặc điểm:

- Local Search
- Complete Assignment
- Conflict Minimization
- Randomized Repair
- CSP Solving

---

# Hạn chế

Min-Conflicts không phải thuật toán chuẩn để giải 8-Puzzle.

Trong project này:

```text
Min-Conflicts
```

được dùng để minh họa CSP.

Đường đi thực tế từ trạng thái ban đầu tới Goal được tạo bởi:

```text
Breadth First Search (BFS)
```

Do đó đây là:

```text
Mô phỏng Min-Conflicts trên biểu diễn CSP của 8-Puzzle
```

không phải lời giải 8-Puzzle bằng Min-Conflicts theo nghĩa truyền thống.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**