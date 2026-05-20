# 8 Puzzle Solver - DFS Algorithm

## Giới thiệu

Đây là bài thực hành về thuật toán **Depth-First Search (DFS)** trong môn Trí Tuệ Nhân Tạo (AI).

Chương trình mô phỏng bài toán **8-Puzzle** bằng Python kết hợp Tkinter GUI để trực quan hóa quá trình tìm kiếm lời giải.

Thuật toán DFS sẽ ưu tiên đi sâu vào một nhánh trước khi quay lui để tìm nhánh khác.

---

# Mô tả bài toán 8-Puzzle

Bài toán gồm:

* Ma trận 3x3
* Các số từ `1 → 8`
* Một ô trống đại diện bởi `0`

Mục tiêu:

```text id="92lc54"
1 2 3
4 5 6
7 8 0
```

Agent cần tìm chuỗi bước di chuyển để đưa trạng thái hiện tại về trạng thái đích.

---

# Chức năng

* Sinh ngẫu nhiên bàn cờ hợp lệ
* Kiểm tra trạng thái solvable
* Giải bài toán bằng DFS
* Cho phép nhập giới hạn độ sâu
* Hiển thị animation từng bước
* Hiển thị:

  * Số node đã mở rộng
  * Số bước lời giải
  * Thời gian thực thi
* Hiển thị danh sách hướng di chuyển:

  * UP
  * DOWN
  * LEFT
  * RIGHT

---

# Thuật toán DFS

## Ý tưởng hoạt động

DFS sẽ:

1. Bắt đầu từ trạng thái gốc
2. Đi sâu xuống các node con
3. Nếu không tìm được lời giải:

   * quay lui
4. Tiếp tục tìm ở nhánh khác

---

## Cơ chế hoạt động

Thuật toán sử dụng:

* Stack (LIFO)
* Depth Limit
* Kiểm tra trạng thái đã thăm

Pseudo:

```text id="vq3n4n"
1. Push trạng thái ban đầu vào stack
2. Pop node trên cùng
3. Kiểm tra goal state
4. Nếu chưa vượt depth limit:
      sinh trạng thái con
      thêm vào stack
5. Lặp lại đến khi tìm được lời giải
```

---

# Các thành phần chính

| Hàm              | Chức năng                  |
| ---------------- | -------------------------- |
| `get_children()` | Sinh trạng thái con        |
| `get_move()`     | Xác định hướng di chuyển   |
| `dfs()`          | Thuật toán DFS             |
| `is_solvable()`  | Kiểm tra trạng thái hợp lệ |
| `random_board()` | Sinh bàn cờ ngẫu nhiên     |
| `draw()`         | Hiển thị bàn cờ            |
| `solve()`        | Giải bài toán              |
| `animate()`      | Animation lời giải         |

---

# Công nghệ sử dụng

* Python 3
* Tkinter GUI
* Jupyter Notebook

---

# Cấu trúc project

```text id="mgn6vf"
DFS/
│
├── DFS.ipynb
└── README.md
```

---

# Cách chạy chương trình

## Clone project

```bash id="n9rl0y"
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy notebook

Mở file `.ipynb` bằng:

* Jupyter Notebook
* VS Code
* Google Colab

Sau đó chạy file:

```text id="3fhy2w"
DFS.ipynb
```

---

# Hướng dẫn sử dụng

1. Chạy toàn bộ cell trong notebook
2. Nhấn nút **Shuffle**
3. Nhập giới hạn độ sâu
4. Nhấn nút **Solve**
5. Quan sát animation lời giải

---

# Ví dụ kết quả

```text id="2rj6mf"
Nodes: 3521
Steps: 18
Time: 245.12 ms
```

---

# Giao diện chương trình

Giao diện gồm:

* Bàn cờ 8 Puzzle
* Danh sách bước di chuyển
* Ô nhập depth limit
* Nút Shuffle
* Nút Solve
* Thông tin node mở rộng và thời gian chạy

---

# Ưu điểm của DFS

* Bộ nhớ sử dụng thấp
* Cài đặt đơn giản
* Tìm kiếm nhanh ở một số trường hợp

---

# Nhược điểm của DFS

* Không đảm bảo lời giải tối ưu
* Có thể đi rất sâu
* Dễ bị lặp nếu không kiểm tra trạng thái

---

# Kiến thức AI áp dụng

Project sử dụng:

* Uninformed Search
* Depth-First Search (DFS)
* State Space Search
* Depth Limited Search

---

# Tác giả

**PhamQuyVy**
