<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/9958e927-0a64-43fe-bdc1-00c78bf3af54" /># 📄 REPORT – GEOMETRIC TRANSFORMS

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
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/2769d550-9866-4b96-a9ef-848b39897442" /> 
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/d1ca2b34-d28a-420b-a545-9ee223e065bf" />
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/f45e1f8a-8abc-451e-bdbc-0cd3a89db902" />
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/7672084b-9b34-4c13-835b-1018c2ad1024" />
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/7e7c2a38-3bea-4848-85b5-60b99aee31ea" />
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/e574cf42-33cd-4f2b-b1a9-174afcd8455d" />
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/60d37aa0-4343-47cc-b7c2-87abc7adc864" />
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/674b2389-48d5-49a9-b373-fff6200c8a1c" />
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/423ce223-fc07-436b-81b5-4db452e766ce" />
<img width="389" height="411" alt="image" src="https://github.com/user-attachments/assets/1ffd150e-9a0f-4528-84cb-fc6d805cf2f5" />
<img width="500" height="411" alt="image" src="https://github.com/user-attachments/assets/773b7792-db86-46d9-9a24-58babfa25520" />
<img width="912" height="427" alt="image" src="https://github.com/user-attachments/assets/6b7d6c76-045b-4ee2-813d-96a2df92364f" />
<img width="912" height="427" alt="image" src="https://github.com/user-attachments/assets/984537c8-6c6d-456a-af24-f41dfb023476" />















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

