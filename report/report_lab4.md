# 📄 REPORT – GEOMETRIC TRANSFORMS

## 1. Mathematical Formulas for Transformations

Affine transformation tổng quát:

y = A x + b

Trong đó:
- A: ma trận biến đổi
- b: vector tịnh tiến

### Translation
x' = x + tx
y' = y + ty

### Scaling
x' = sx * x
y' = sy * y

### Rotation
x' = x cosθ - y sinθ
y' = x sinθ + y cosθ

### Shear
Shear theo X: x′=x+kx​y,y′=y
Shear theo Y: x′=x,y′=y+ky​x

---

## 2. Forward Mapping vs Inverse Mapping

### Forward Mapping
Với forward mapping, mỗi điểm ảnh trong ảnh gốc sẽ được ánh xạ trực tiếp sang vị trí mới trong ảnh kết quả. Tuy nhiên, phương pháp này thường gây ra hiện tượng mất dữ liệu do một số pixel trong ảnh mới không được gán giá trị, dẫn đến các vùng trống hay còn gọi là “holes”.

### Inverse Mapping
Inverse mapping thực hiện theo hướng ngược lại, tức là duyệt từng pixel trong ảnh đầu ra và tìm vị trí tương ứng của nó trong ảnh gốc. Cách tiếp cận này đảm bảo rằng mọi pixel trong ảnh kết quả đều có giá trị, từ đó tránh được hiện tượng lỗ hổng.

---

## 3. Screenshots of Outputs



---

## 4. Comparison: Basic vs Improved Implementation

Qua quá trình thực nghiệm, có thể nhận thấy sự khác biệt rõ ràng giữa phương pháp cài đặt cơ bản và phương pháp cải tiến. Phương pháp cơ bản thường sử dụng forward mapping, dẫn đến hiện tượng mất pixel và chất lượng ảnh kém. Ngược lại, phương pháp cải tiến sử dụng inverse mapping giúp đảm bảo mọi pixel đều được gán giá trị, từ đó nâng cao độ chính xác và chất lượng hình ảnh.

---

## 5. Comparison: NumPy vs OpenCV

Việc so sánh giữa cài đặt bằng NumPy và thư viện OpenCV cho thấy OpenCV vượt trội hơn về cả tốc độ và chất lượng. Cài đặt bằng NumPy thường phải duyệt từng pixel nên tốc độ xử lý chậm, đồng thời không hỗ trợ nội suy nên ảnh có thể bị răng cưa. Trong khi đó, OpenCV được tối ưu hóa ở mức thấp hơn và cung cấp nhiều phương pháp nội suy, giúp ảnh sau biến đổi mượt và chính xác hơn.

---

## 6. Why Order Matters

Một đặc điểm quan trọng của các phép biến đổi affine là chúng không có tính giao hoán, nghĩa là việc thay đổi thứ tự thực hiện các phép biến đổi sẽ dẫn đến kết quả khác nhau. Ví dụ, khi thực hiện phép xoay trước rồi mới phóng to, hình ảnh sẽ được phóng theo hệ trục đã xoay. Ngược lại, nếu phóng to trước rồi mới xoay, toàn bộ ảnh đã được mở rộng sẽ bị xoay, dẫn đến kết quả khác biệt.

Tương tự, trong trường hợp kết hợp tịnh tiến và xoay, nếu thực hiện tịnh tiến trước thì tâm xoay sẽ bị thay đổi, khiến đối tượng quay quanh một vị trí khác. Ngược lại, nếu xoay trước rồi mới tịnh tiến, hình dạng và hướng của đối tượng được giữ nguyên, chỉ thay đổi vị trí trong ảnh.

Do đó, có thể kết luận rằng thứ tự thực hiện các phép biến đổi ảnh hưởng trực tiếp đến kết quả cuối cùng và cần được lựa chọn cẩn thận trong các ứng dụng thực tế.

---

