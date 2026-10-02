\# Báo cáo Bài 2: Quản lý nhánh và Giải quyết xung đột



\## 1. Tạo nhánh feature-update



Từ nhánh `main`, tạo nhánh `feature-update`:



```bash

git switch -c feature-update

```



\## 2. Tạo thay đổi trên nhánh feature-update



Chỉnh sửa file `README.md` trên nhánh `feature-update` và tạo commit:



```bash

git add homework/session\_04/ex2/README.md

git commit -m "Update README on feature branch"

```



\## 3. Tạo thay đổi trên nhánh main



Chuyển về nhánh `main`, chỉnh sửa cùng một dòng trong `README.md` với nội dung khác:



```bash

git switch main

git add homework/session\_04/ex2/README.md

git commit -m "Update README on main branch"

```



\## 4. Tạo Merge Conflict



Thực hiện:



```bash

git merge feature-update

```



Git phát hiện xung đột vì hai nhánh cùng thay đổi một vùng trong file `README.md`.



\## 5. Giải quyết xung đột thủ công



Mở file `README.md` và xử lý các ký hiệu xung đột:



```text

<<<<<<< HEAD

=======

>>>>>>> feature-update

```



Sau đó lựa chọn nội dung phù hợp, xóa toàn bộ các ký hiệu đánh dấu xung đột và lưu file.



\## 6. Hoàn tất Merge



Sau khi giải quyết xung đột:



```bash

git add homework/session\_04/ex2/README.md

git commit -m "Merge feature-update into main and resolve conflict"

```



\## 7. Kiểm tra lịch sử commit



Sử dụng:



```bash

git log --graph --oneline --decorate --all

```



Kết quả cho thấy nhánh `feature-update` tách ra từ `main` và được gộp trở lại bằng một merge commit có hai nhánh tổ tiên.



