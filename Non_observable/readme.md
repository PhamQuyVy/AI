# Non-Observable Search - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng thuật toán:

```text
BFS
```

kết hợp giao diện đồ họa bằng:

```text
Tkinter
```

Trong môi trường không quan sát được (Non-Observable Environment), tác nhân không biết chính xác trạng thái hiện tại của mình.

Thay vì tìm kiếm trên một trạng thái duy nhất, thuật toán tìm kiếm trên:

```text
Belief State
```

là tập hợp các trạng thái có thể xảy ra.

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

# Môi trường không quan sát được

Ban đầu chương trình sinh ra:

```text
Board 1
Board 2
```

Agent không biết mình đang ở board nào.

Do đó trạng thái ban đầu là:

```text
Belief State = {Board1, Board2}
```

Mục tiêu:

```text
Belief State = {GOAL}
```

---

# Ý tưởng thuật toán

Thuật toán thực hiện tìm kiếm BFS trên:

```text
Belief States
```

Mỗi action:

```text
UP
DOWN
LEFT
RIGHT
```

được áp dụng đồng thời lên tất cả các trạng thái trong belief state.

Ví dụ:

```text
Belief = {S1, S2}
```

Sau action:

```text
UP
```

sẽ thu được:

```text
Belief' = {UP(S1), UP(S2)}
```

Nếu action không hợp lệ trên một board thì board đó giữ nguyên.

---

# Belief State

Belief State được lưu dưới dạng:

```python
frozenset(board)
```

Ví dụ:

```text
{
    Board A,
    Board B
}
```

Biểu diễn tất cả trạng thái mà agent có thể đang ở.

---

# Hàm heuristic

Chương trình sử dụng:

```text
Misplaced Tiles
```

để hiển thị mức độ gần Goal.

---

## Công thức

```text
h(n) = số ô sai vị trí
```

Không tính ô trống.

---

# Ví dụ Heuristic

## Trạng thái

```text
1 2 3
4 0 6
7 5 8
```

## Goal

```text
1 2 3
4 5 6
7 8 0
```

Các ô sai vị trí:

- 5
- 8

Do đó:

```text
h(n) = 2
```

---

# Quy trình hoạt động

1. Khởi tạo Belief State ban đầu.
2. Đưa Belief State vào Queue.
3. Lấy Belief State đầu tiên ra khỏi Queue.
4. Sinh các action:

```text
UP
DOWN
LEFT
RIGHT
```

5. Áp dụng action lên toàn bộ board trong Belief State.
6. Tạo Belief State mới.
7. Nếu chưa xuất hiện thì đưa vào Queue.
8. Lặp lại cho đến khi:

```text
Belief State = {GOAL}
```

---

# Pseudocode

```text
function Sensorless_BFS(start_belief):

    frontier ← Queue
    frontier.push(start_belief)

    visited ← {start_belief}

    while frontier not empty:

        belief ← frontier.pop()

        if belief = {GOAL}:
            return solution

        for action in Actions:

            new_belief ← Apply(action, belief)

            if new_belief not in visited:

                visited.add(new_belief)
                frontier.push(new_belief)
```

---

# Chức năng giao diện

## Gồm

- Hai bàn cờ 8 Puzzle.
- Animation lời giải.
- Shuffle random board.
- Solve tự động.
- Step-by-step.

---

## Hiển thị

- Heuristic của Board 1.
- Heuristic của Board 2.
- Expanded Nodes.
- Steps.
- Running Time.
- Belief Size.
- Visited States.

---

# Highlight đặc biệt

## Ô đúng vị trí

- Màu trắng.

## Ô sai vị trí

- Màu đỏ nhạt.

## Ô trống

- Màu xanh lá nhạt.
- Viền nét đứt.

---

# Các thành phần chính

| Hàm | Chức năng |
|------|------------|
| `misplaced()` | Tính số ô sai vị trí |
| `apply_action()` | Áp dụng action lên board |
| `sensorless_bfs()` | Thuật toán Sensorless BFS |
| `random_board()` | Sinh board ngẫu nhiên |
| `draw_board()` | Vẽ một bàn cờ |
| `draw()` | Hiển thị belief state |
| `animate()` | Animation lời giải |
| `solve()` | Chạy thuật toán |

---

# Ví dụ

## Belief State ban đầu

```text
{
    Board1,
    Board2
}
```

---

## Sau action RIGHT

```text
{
    RIGHT(Board1),
    RIGHT(Board2)
}
```

---

## Mục tiêu

```text
{
    GOAL
}
```

Khi belief state chỉ còn một trạng thái duy nhất và trạng thái đó là Goal.

---

# Công nghệ sử dụng

- Python 3
- Tkinter
- Collections (deque)
- Random
- Time

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy file

```bash
python Non_observable.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Sensorless Search
```

Đặc điểm:

- Tìm kiếm trong môi trường không quan sát được.
- Trạng thái được biểu diễn bằng Belief State.
- Sử dụng Breadth First Search.
- Đảm bảo tìm được lời giải nếu tồn tại.
- Tìm kiếm trên tập trạng thái thay vì một trạng thái đơn lẻ.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**