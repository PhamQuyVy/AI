# Simple Reflex Agent - AI cơ bản

## Giới thiệu

Đây là project mô phỏng **Simple Reflex Agent** trong môn Trí tuệ nhân tạo (AI).

Agent hoạt động dựa trên:

* trạng thái hiện tại của môi trường
* tập luật có sẵn (rule-based)
* không ghi nhớ lịch sử trước đó

Project gồm các ví dụ:

1. Agent giải bài toán 8-puzzle (ma trận 3x3), chỉ thực hiện bước đi
2. Agent chọn hướng di chuyển dựa trên vị trí ô trống, hoàn thành sắp xếp cả bài
3. Robot hút bụi trong môi trường có vật cản

---

# Nội dung project

## 1. Simple Reflex Agent cho bài toán 8-Puzzle

### Mô tả

Chương trình nhận vào ma trận 3x3.
Trong đó:

* `0` đại diện cho ô trống (blank)
* Agent xác định vị trí ô trống
* Dựa vào bảng luật để chọn hướng di chuyển hợp lệ

Ví dụ:

```text
1 2 3
4 0 5
6 7 8
```

Ô trống ở giữa nên có thể:

* UP
* DOWN
* LEFT
* RIGHT

Agent sẽ chọn ngẫu nhiên một hướng hợp lệ.

---

## 2. Rule Table

Agent sử dụng bảng luật:

```python
RULE_TABLE = {
    (0,0): ["DOWN", "RIGHT"],
    (0,1): ["DOWN", "LEFT", "RIGHT"],
    (0,2): ["DOWN", "LEFT"],
    ...
}
```

Ý nghĩa:

* Key: vị trí ô trống
* Value: các hướng di chuyển hợp lệ

Ví dụ:

```python
(0,0): ["DOWN", "RIGHT"]
```

Nếu ô trống ở góc trên bên trái thì chỉ được:

* đi xuống
* đi sang phải

---

## 3. Robot hút bụi thông minh

### Mô tả

Project còn mô phỏng robot hút bụi hoạt động trong môi trường 3x3.

Quy ước:

* `0` = sạch
* `1` = bẩn
* `2` = chướng ngại vật
* `R` = vị trí robot

Robot sẽ:

1. cảm nhận môi trường bằng sensor
2. xác định ô bẩn gần nhất
3. di chuyển đến vị trí phù hợp
4. hút bụi khi gặp ô bẩn

---

# Các thành phần chính

## Sensor

Có nhiệm vụ cảm nhận trạng thái môi trường.

Ví dụ:

```python
sensor(state)
```

Dùng để:

* tìm vị trí ô trống
* xác định ô sạch/bẩn

---

## Processor

Xử lý dữ liệu nhận được từ sensor.

Ví dụ:

```python
processor(blank_pos)
```

Processor sẽ:

* đọc rule table
* xác định hành động hợp lệ
* chọn hành động tiếp theo

---

## Actuator

Thực hiện hành động.

Ví dụ:

```python
actuator(move)
```

Agent sẽ:

* di chuyển
* hút bụi
* cập nhật trạng thái môi trường

---

# Công nghệ sử dụng

* Python
* Jupyter Notebook
* Random module

---

# Cách chạy project

## 1. Clone project

```bash
git clone https://github.com/PhamQuyVy/AI.git
```

## 2. Mở thư mục project

```bash
cd AI
```

## 3. Chạy notebook

```bash
jupyter notebook
```
# Kiến thức AI áp dụng

Project minh họa các khái niệm:

* Simple Reflex Agent
* Rule-based Agent
* Environment Perception
* Sensor / Processor / Actuator
* Problem Solving trong AI

---

# Ưu điểm

* Dễ hiểu
* Dễ mô phỏng
* Phù hợp cho người mới học AI
* Minh họa rõ cách agent hoạt động

---

# Hạn chế

* Không học từ dữ liệu
* Không ghi nhớ lịch sử
* Chỉ hoạt động theo luật cố định
* Khả năng tối ưu chưa cao

---

# Tác giả

* Phạm Quý Vỹ
* Sinh viên ngành Data Engineering
* Trường Đại học Sư phạm TP.HCM (HCMUTE)
