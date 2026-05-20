# 8 Puzzle Solver - IDS Algorithm

## Giới thiệu

Đây là bài thực hành về thuật toán **Iterative Deepening Search (IDS)** trong môn Trí Tuệ Nhân Tạo (AI).

Chương trình mô phỏng bài toán **8-Puzzle** bằng Python kết hợp Tkinter GUI để trực quan hóa quá trình tìm kiếm lời giải.

Thuật toán IDS là sự kết hợp giữa:

* DFS (Depth-First Search)
* BFS (Breadth-First Search)

IDS sẽ tìm kiếm theo chiều sâu nhưng tăng dần giới hạn độ sâu sau mỗi lần lặp.

---

# Mô tả bài toán 8-Puzzle

Bài toán gồm:

* Ma trận 3x3
* Các số từ `1 → 8`
* Một ô trống đại diện bởi `0`

Mục tiêu:

```text id="y5i0gr"
1 2 3
4 5 6
7 8 0
```

Agent cần tìm chuỗi bước di chuyển để đưa trạng thái hiện tại về trạng thái đích.

---

# Chức năng

* Sinh ngẫu nhiên bàn cờ hợp lệ
* Kiểm tra trạng thái solvable
* Giải bài toán bằng IDS
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

# Thuật toán IDS

## Ý tưởng hoạt động

IDS sẽ:

1. Tìm kiếm với depth = 0
2. Nếu chưa thấy goal:

   * tăng depth lên 1
3. Chạy lại DFS với depth mới
4. Lặp cho đến khi tìm được lời giải

---

## Depth Limited Search

Thuật toán sử dụng:

* Stack (LIFO)
* Depth Limit
* Tránh lặp trạng thái

Pseudo:

```text id="w0qhz9"
1. Push trạng thái đầu vào stack
2. Pop node trên cùng
3. Kiểm tra goal
4. Nếu chưa vượt depth limit:
      sinh node con
      thêm vào stack
5. Lặp lại đến khi tìm thấy lời giải
```

---

## Iterative Deepening Search

```text id="4o13e9"
for depth = 0 → MAX_DEPTH:
    chạy Depth Limited Search
    nếu tìm thấy goal:
        trả về lời giải
```

---

# Các thành phần chính

| Hàm                            | Chức năng                  |
| ------------------------------ | -------------------------- |
| `generate_children()`          | Sinh trạng thái con        |
| `get_direction()`              | Xác định hướng di chuyển   |
| `is_solvable()`                | Kiểm tra trạng thái hợp lệ |
| `generate_board()`             | Sinh bàn cờ ngẫu nhiên     |
| `ids()`                        | DFS có giới hạn độ sâu     |
| `iterative_deepening_search()` | IDS chính                  |
| `update_board()`               | Hiển thị bàn cờ            |
| `animate_solution()`           | Animation lời giải         |

---

# Công nghệ sử dụng

* Python 3
* Tkinter GUI
* Jupyter Notebook

---

# Cấu trúc project

```text id="jtbmnr"
IDS/
│
├── IDS.ipynb
└── README.md
```

---

# Cách chạy chương trình

## Clone project

```bash id="s4ty3n"
git clone https://github.com/PhamQuyVy/AI.git
```

---

## Chạy notebook

Mở file `.ipynb` bằng:

* Jupyter Notebook
* VS Code
* Google Colab

Sau đó chạy file:

```text id="7z4g08"
IDS.ipynb
```

---

# Hướng dẫn sử dụng

1. Chạy toàn bộ cell trong notebook
2. Nhấn nút **Shuffle**
3. Nhấn nút **Solve IDS**
4. Quan sát animation lời giải

---

# Ví dụ kết quả

```text id="f2e6mu"
Expanded Nodes: 4213
Steps: 20
Time: 156.22 ms
```

---

# Giao diện chương trình

Giao diện gồm:

* Bàn cờ 8 Puzzle
* Danh sách bước di chuyển
* Nút Shuffle
* Nút Solve IDS
* Thông tin node mở rộng và thời gian chạy

---

# Ưu điểm của IDS

* Tìm được lời giải tối ưu như BFS
* Tiết kiệm bộ nhớ hơn BFS
* Phù hợp với không gian trạng thái lớn

---

# Nhược điểm của IDS

* Lặp lại nhiều node ở các tầng trên
* Có thể chậm nếu lời giải quá sâu

---

# Kiến thức AI áp dụng

Project sử dụng:

* Uninformed Search
* Depth Limited Search
* Iterative Deepening Search (IDS)
* State Space Search

---

# Tác giả

**24133077 Phạm Quý Vỹ**
