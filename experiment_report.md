# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600287
**Name:** Tạ Thị Thùy Dương
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. | 9 | Du lieu sach, khong co outlier. Agent phan tich chinh xac: 3 san pham hop le, gia trung binh dung, category chinh xac (Electronics, Furniture). |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 3 | Du lieu co duplicate ID, outlier gia, null values. Agent tra loi sai: phan loai sai category. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung garbage data, Agent AI cho ket qua sai vi nhieu ly do:

1. **Duplicate IDs**: Trùng lặp ID khiến Agent đếm số lượng sản phẩm bị sai, dẫn đến thống kê không chính xác về số lượng hàng tồn kho hoặc doanh thu.

2. **Outlier giá**: Các giá trị bất thường (ví dụ: giá = -10 hoac giá = 999999) làm lệch giá trị trung bình, median. Agent có thể báo cáo giá trung bình cao bất thường mà không biết là do dữ liệu bị lỗi.

3. **Null values va empty fields**: Các trường castegory rỗng/null khiến Agent không thể phân nhóm sản phẩm đúng, làm sai báo cáo theo danh mục.

4. **Wrong data types**: ví dụ khi trường price chứa chuỗi thay vì số, Agent không thể thực hiện phép tính số học, dẫn đến lỗi/ kết quả không mong muốn.

5. **Kết luận**: Chất lượng dữ liệu đầu vào ảnh hưởng trực tiếp đến độ chính xác của AI agent response. Dù prompt có tốt đến đâu, nếu dữ liệu đầu vào bị lỗi thì kết quả đầu ra cũng sẽ sai. 

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Đồng ý.

Vì dữ liệu chất lượng cao quan trọng hơn prompt tốt. Một Agent với prompt đơn giản nhưng dữ liệu sạch, sẽ cho jeets quả chính xác hơn một Agent với prompt phức tạp nhwung dữ liệu bị lỗi. Bước validata và clean dữ liệu trước khi đưa vào pipeline là cực kỳ quan trọng để đảm bảo kết quả đáng tin cậy. 
