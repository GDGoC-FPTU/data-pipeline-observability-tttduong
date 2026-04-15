# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.duongttt@vinuni.edu.vn
**Name:** Tạ Thị Thùy Dương

---

## Mo ta

Bài lab này xây dựng một ETL pipeline tự động đọc dữ liệu JSON, kiểm tra chất lượng dữ liệu (validate), biến đổi (transform) và lưu kết quả ra file csv. Ngoài ra, stress test để mô phỏng ảnh hưởng của "dữ liệu bẩn" lên kết quả phân tích của AI Agent. 

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Buoc 1: Chay pipeline voi du lieu sach
python solution.py
# Output: processed_data.csv

# Buoc 2: Tao du lieu rac
python generate_garbage.py
# Output: garbage_data.csv

# Buoc 3: Chay agent simulation voi tung bo du lieu
python agent_simulation.py 
```

### Chay Tests
```bash
pytest tests/
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
├── agent_simulation.py      # Script gia lap AI Agent
├── generate_garbage.py      # Tao du lieu rac cho stress test
├── raw_data.json            # Du lieu dau vao
└── README.md                # File nay
```

---

## Ket qua

- **Tổng số records đọc vào:** 5
- **Records hợp lệ (sau validate):** 3 (loại bỏ 2 records: giá âm va category rỗng)
- **Records bị loại:** 2
- **Transformations:** tính `discounted_price` = price * 0.9, chuẩn hoá category thành Title Case, thêm cột `processed_at`
- **Output:** `processed_data.csv` với 3 records đã xử lý
