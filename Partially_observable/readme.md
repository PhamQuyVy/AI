# Partially Observable Search - 8 Puzzle

## Giới thiệu

Đây là chương trình mô phỏng bài toán:

```text
8 Puzzle
```

sử dụng mô hình:

```text
Partially Observable Search
```

được xây dựng bằng:

```text
Python + Tkinter
```

Trong môi trường quan sát một phần, tác nhân (Agent) không thể nhìn thấy toàn bộ trạng thái hiện tại của bàn cờ mà chỉ quan sát được một phần thông tin.

Do đó Agent phải duy trì một tập các trạng thái khả dĩ gọi là:

```text
Belief State
```

để suy luận vị trí thực tế của mình.

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

# Môi trường quan sát một phần

Agent không nhìn thấy toàn bộ bàn cờ.

Ví dụ chỉ quan sát được hàng đầu tiên:

```text
1 2 3
? ? ?
? ? ?
```

Các ô còn lại được xem là chưa biết.

Thông tin quan sát được gọi là:

```text
Observation
```

---

# Belief State

Do không biết chính xác trạng thái hiện tại nên Agent phải lưu tập tất cả trạng thái có thể xảy ra.

Ví dụ:

```text
Belief State =
{
    State A,
    State B,
    State C
}
```

Mỗi khi nhận được Observation mới, Agent sẽ loại bỏ các trạng thái không phù hợp.

---

# Ý tưởng thuật toán

Thuật toán hoạt động theo các bước:

1. Khởi tạo Belief State ban đầu.
2. Quan sát một phần trạng thái.
3. Cập nhật Belief State.
4. Sinh các trạng thái kế tiếp.
5. Loại bỏ trạng thái không khớp Observation.
6. Tiếp tục tìm kiếm.
7. Dừng khi tìm thấy Goal.

---

# Observation Function

Hàm quan sát dùng để lấy phần thông tin mà Agent nhìn thấy.

Ví dụ:

```text
Observation =
(1, 2, 3)
```

Agent chỉ biết ba ô đầu tiên của bàn cờ.

---

# Belief Update

Sau mỗi bước di chuyển:

```text
Belief' = Update(Belief, Observation)
```

Các trạng thái không tạo ra Observation tương ứng sẽ bị loại bỏ.

---

# Quy trình hoạt động

```text
Start

↓

Observation

↓

Belief State

↓

Generate Successors

↓

Update Belief

↓

Goal Test

↓

Goal Found
```

---

# Pseudocode

```text
function PartiallyObservableSearch(start):

    initialize belief state

    while belief state not empty:

        observe environment

        update belief state

        for each possible state:
            generate successors

        if goal reached:
            return solution
```

---

# Heuristic

Chương trình sử dụng:

```text
Misplaced Tiles
```

---

## Công thức

```text
h(n) =
số ô sai vị trí
```

không tính ô trống.

---

## Ví dụ

### Trạng thái hiện tại

```text
1 2 3
4 0 6
7 5 8
```

### Goal

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

Kết quả:

```text
h(n) = 2
```

---

# Chức năng giao diện

## Bao gồm

- Hiển thị bàn cờ 8 Puzzle.
- Hiển thị Observation.
- Hiển thị Belief State.
- Animation lời giải.
- Shuffle trạng thái ngẫu nhiên.
- Solve tự động.
- Step-by-step.
- Hiển thị:

  - Steps
  - Expanded Nodes
  - Execution Time
  - Heuristic h(n)

---

# Hiển thị trực quan

## Ô đúng vị trí

```text
Màu trắng
```

## Ô sai vị trí

```text
Màu đỏ nhạt
```

## Ô trống

```text
Màu xanh nhạt
```

---

# Các thành phần chính

| Hàm | Chức năng |
|------|-----------|
| `observe()` | Lấy Observation |
| `update_belief()` | Cập nhật Belief State |
| `misplaced()` | Tính heuristic |
| `get_neighbors()` | Sinh trạng thái con |
| `search()` | Thuật toán tìm kiếm |
| `draw()` | Vẽ bàn cờ |
| `animate()` | Animation lời giải |
| `shuffle()` | Sinh trạng thái ngẫu nhiên |

---

# Ví dụ

## Observation

```text
1 2 3
? ? ?
? ? ?
```

## Belief State

```text
{
    State 1,
    State 2,
    State 3,
    ...
}
```

## Sau khi cập nhật

```text
Belief Size giảm dần
```

và Agent xác định được trạng thái chính xác hơn.

---

# Kết quả đầu ra

Thuật toán trả về:

```text
Đường đi từ trạng thái đầu
đến trạng thái đích
```

kèm:

- Số bước.
- Số node mở rộng.
- Thời gian thực thi.
- Belief State cuối cùng.

---

# Công nghệ sử dụng

- Python 3
- Tkinter
- Queue / BFS
- Belief State Representation

---

# Cách chạy chương trình

## Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

## Chạy chương trình

```bash
python Partially_observable.ipynb
```

---

# Kiến thức AI áp dụng

Project sử dụng:

```text
Partially Observable Search
```

Đặc điểm:

- Agent không nhìn thấy toàn bộ môi trường.
- Phải duy trì Belief State.
- Liên tục cập nhật theo Observation.
- Giảm dần độ không chắc chắn.
- Hỗ trợ ra quyết định trong môi trường thiếu thông tin.

---

# Tác giả

**24133077 - Phạm Quý Vỹ**