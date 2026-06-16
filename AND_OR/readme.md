# AND-OR Graph Search - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
AND-OR Graph Search
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Thuật toán được sử dụng trong môi trường:

```text
Observable Environment
```

với mục tiêu tìm chuỗi hành động đưa trạng thái hiện tại về trạng thái đích.

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

AND-OR Graph Search là thuật toán tìm kiếm dùng cho:

```text
Problem Solving Agent
```

Trong đó:

- OR Node đại diện cho lựa chọn hành động của Agent.
- AND Node đại diện cho kết quả sau khi thực hiện hành động.

Thuật toán xây dựng cây tìm kiếm gồm:

```text
OR → AND → OR → AND ...
```

cho đến khi đạt trạng thái đích.

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
2. Tạo OR Node.
3. Chọn hành động khả thi.
4. Sinh trạng thái mới.
5. Tạo AND Node.
6. Tiếp tục mở rộng các trạng thái.
7. Kiểm tra Goal.
8. Trả về lời giải.

---

# Cấu trúc cây tìm kiếm

```text
          OR
         / | \
        /  |  \
      AND AND AND
       |    |    |
       OR   OR   OR
```

Trong đó:

```text
OR Node
```

đại diện cho:

```text
Lựa chọn hành động
```

và

```text
AND Node
```

đại diện cho:

```text
Kết quả của hành động
```

---

# Pseudocode

```text
AND_OR_GRAPH_SEARCH(problem)

    return OR_SEARCH(initial_state)

------------------------------------------------

OR_SEARCH(state)

    if Goal(state)
        return SUCCESS

    for each action in ACTIONS

        result = RESULT(state, action)

        plan = AND_SEARCH(result)

        if plan succeeds
            return plan

    return FAILURE

------------------------------------------------

AND_SEARCH(states)

    for each state in states

        plan = OR_SEARCH(state)

        if failure
            return FAILURE

    return SUCCESS
```

---

# Chức năng giao diện

## Bao gồm

- Random trạng thái đầu.
- Giải tự động.
- Chạy từng bước.
- Animation lời giải.
- Hiển thị:

  - Expanded Nodes
  - Search Depth
  - Steps
  - Time
  - Heuristic h(n)

---

# Thông tin hiển thị

## Nodes

```text
Số node đã mở rộng
```

---

## Depth

```text
Độ sâu lời giải tìm được
```

---

## Steps

```text
Số bước từ Start đến Goal
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

| Hàm | Chức năng |
|------|------|
| `misplaced()` | Tính heuristic |
| `apply_action()` | Thực hiện hành động |
| `and_or_graph_search()` | Thuật toán AND-OR |
| `OR_search()` | Mở rộng OR Node |
| `AND_search()` | Mở rộng AND Node |
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

- Python 3
- Tkinter
- Recursive Search

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python AND_OR_GRAPH_SEARCH.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
AND-OR Graph Search
```

Đặc điểm:

- Tìm kiếm theo cấu trúc AND-OR.
- Dùng cho Problem Solving Agent.
- Hỗ trợ biểu diễn cây quyết định.
- Kết hợp OR Node và AND Node.
- Có thể tìm kế hoạch dẫn tới Goal State.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**