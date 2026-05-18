# 8-Puzzle Solver — BFS Version 1 & Version 2
---
# Giới thiệu
Project này mô phỏng bài toán:
# 8-Puzzle
sử dụng thuật toán:
# Breadth-First Search (BFS)
Bao gồm:
- BFS Version 1
- BFS Version 2
Mục tiêu chính:
- So sánh 2 cách kiểm tra GOAL trong BFS
- Quan sát sự khác nhau của frontier (queue)
- Minh họa hoạt động BFS bằng animation
---
# Bài toán 8-Puzzle
Puzzle gồm:
```text
1 2 3
4 5 6
7 8 _
```
Trong đó:

- `_` là ô trống
- được phép di chuyển:
  - lên
  - xuống
  - trái
  - phải

---
# Mục tiêu

Đưa board hiện tại về trạng thái:

```text
1 2 3
4 5 6
7 8 _
```
---
# Thuật toán sử dụng
# Breadth-First Search (BFS)

BFS là thuật toán tìm kiếm theo chiều rộng.

Hoạt động:

- Duyệt từng tầng
- Dùng Queue (FIFO)
- Luôn tìm được đường đi ngắn nhất

---

# BFS Version 1

## Ý tưởng

```text
Sinh node con
→ kiểm tra GOAL ngay
→ mới insert queue
```

Node đích:

```text
KHÔNG BAO GIỜ vào queue
```

---

# Code đặc trưng — BFS v1

```python
for child in neighbors(state):

    if child in visited:
        continue

    if child == GOAL:
        return path + [child], nodes

    visited.add(child)

    queue.append((child, path + [child]))
```

---

# Điểm quan trọng của BFS v1

## Goal Test

```python
if child == GOAL
```

xảy ra:

```text
NGAY KHI sinh node con
```

---

# Luồng hoạt động BFS v1

```text
POP node
→ sinh node con
→ check GOAL
→ insert queue
```

---

# BFS Version 2

## Ý tưởng

```text
Sinh node con
→ insert queue
→ POP khỏi queue
→ check GOAL
```

Node đích:

```text
CÓ vào queue
```

---

# Code đặc trưng — BFS v2

```python
board, path = queue.popleft()

if board == GOAL:
    return path, nodes
```

---

# Điểm quan trọng của BFS v2

## Goal Test

```python
if board == GOAL
```

xảy ra:

```text
SAU KHI POP khỏi queue
```

---

# Luồng hoạt động BFS v2

```text
POP node
→ check GOAL
→ sinh node con
→ insert queue
```

---

# So sánh BFS v1 và BFS v2

| BFS v1 | BFS v2 |
|---|---|
| Check GOAL khi sinh con | Check GOAL khi POP |
| Goal không vào queue | Goal có vào queue |
| Duyệt ít node hơn | Duyệt nhiều node hơn |
| Return sớm hơn | Return muộn hơn |
| Tối ưu hơn một chút | Chuẩn theo AIMA 4th |

---

# Khác biệt quan trọng nhất

## BFS v1

```python
if child == GOAL
```

---

## BFS v2

```python
if board == GOAL
```

---

# Frontier (Queue)

Cả hai version đều dùng:

```python
from collections import deque
```

Vì:

- append() O(1)
- popleft() O(1)

---

# Cấu trúc dữ liệu

| Thành phần | Ý nghĩa |
|---|---|
| queue | frontier BFS |
| visited / reached | trạng thái đã duyệt |
| path | đường đi |
| neighbors() | sinh node con |

---

# Hàm sinh trạng thái con

```python
def neighbors(board):
```

Chức năng:

- tìm vị trí ô trống
- sinh các trạng thái hợp lệ

Bao gồm:

- lên
- xuống
- trái
- phải

---

# Kiểm tra solvable

Không phải board nào cũng giải được.

Project sử dụng:

```python
def is_solvable(board):
```

Dựa trên:

```text
Inversion Count
```

Nếu:

```text
inversions % 2 == 0
```

thì puzzle giải được.

---

# Animation

Sau khi BFS tìm được lời giải:

- Các ô vuông sẽ tự di chuyển
- Hiển thị từng trạng thái
- Mô phỏng lời giải ngắn nhất

---

# Các chức năng

## Shuffle

Tạo board ngẫu nhiên.

---

## Solve

Chạy BFS tìm lời giải.

---

## Step

Đi từng bước thủ công.

---

## Reset

Đưa về trạng thái đích.

---

# Thông tin hiển thị

| Thông tin | Ý nghĩa |
|---|---|
| Nodes | số node đã duyệt |
| Steps | số bước lời giải |
| Time | thời gian chạy |

---

# Độ phức tạp

## Time Complexity

```text
O(b^d)
```

---

## Space Complexity

```text
O(b^d)
```

Trong đó:

- b = branching factor
- d = depth

---

# Ưu điểm của BFS

- Tìm được đường đi ngắn nhất
- Complete
- Dễ cài đặt

---

# Nhược điểm của BFS

- Tốn RAM
- Frontier tăng rất nhanh
- Chậm với không gian trạng thái lớn

---

# Cách chạy chương trình

## Chạy BFS v1

```bash
python bfs_v1.py
```

---

## Chạy BFS v2

```bash
python bfs_v2.py
```

---

# Yêu cầu

- Python 3.x
- Tkinter

Tkinter thường có sẵn.

---

# Điều khiển

| Phím | Chức năng |
|---|---|
| S | Shuffle |
| Space | Solve |
| Right Arrow | Step |

---

# Ví dụ

## Start

```text
1 2 3
4 5 6
_ 7 8
```

---

## Goal

```text
1 2 3
4 5 6
7 8 _
```

---

# Ý nghĩa học thuật

Project minh họa:

- State Space Search
- BFS
- Queue
- Goal Test
- Artificial Intelligence Search

Đặc biệt là sự khác nhau giữa:

```text
Goal Test Before Insert
```

và

```text
Goal Test After Pop
```

---

# Kết luận

BFS v1 và BFS v2 đều tìm được:

```text
Đường đi ngắn nhất
```

Tuy nhiên:

- BFS v1 kiểm tra GOAL sớm hơn
- BFS v2 kiểm tra GOAL muộn hơn

Nên:

```text
BFS v2 thường duyệt nhiều node hơn
```

do node đích đã được đưa vào queue trước khi phát hiện.