\# Bài 3: Cấu hình xác thực SSH và Đẩy dự án lên GitHub



\## 1. Mục tiêu



\* Khởi tạo cặp khóa SSH sử dụng thuật toán Ed25519.

\* Cấu hình xác thực SSH với tài khoản GitHub.

\* Cấu hình repository cục bộ sử dụng giao thức SSH.

\* Đẩy mã nguồn và lịch sử commit lên GitHub bằng SSH.



\## 2. Tạo khóa SSH Ed25519



Sử dụng OpenSSH trên Windows để tạo cặp khóa Ed25519:



```powershell

ssh-keygen -t ed25519 -C "it209-devops-vps"

```



Cặp khóa được lưu trong thư mục:



```text

C:\\Users\\dohoa\\.ssh\\

```



Các file khóa:



```text

it209\_devops\_ed25519

it209\_devops\_ed25519.pub

```



Trong đó:



\* `it209\_devops\_ed25519`: khóa private, không công khai và không đưa lên GitHub.

\* `it209\_devops\_ed25519.pub`: khóa public, được sử dụng để thêm vào tài khoản GitHub.



\## 3. Cấu hình SSH với GitHub



File cấu hình SSH:



```text

C:\\Users\\dohoa\\.ssh\\config

```



Nội dung:



```text

Host github.com

&#x20;   HostName github.com

&#x20;   User git

&#x20;   IdentityFile \~/.ssh/it209\_devops\_ed25519

&#x20;   IdentitiesOnly yes

```



Public key được thêm vào:



\*\*GitHub → Settings → SSH and GPG keys → New SSH key\*\*



\## 4. Kiểm tra kết nối SSH tới GitHub



Lệnh kiểm tra:



```powershell

ssh -T git@github.com

```



Kết quả:



```text

Hi Anhdozxc! You've successfully authenticated, but GitHub does not provide shell access.

```



Kết quả trên xác nhận tài khoản GitHub đã được xác thực thành công bằng SSH.



\## 5. Kiểm tra và cấu hình remote repository



Lệnh kiểm tra:



```powershell

git remote -v

```



Remote `origin` được cấu hình bằng giao thức SSH:



```text

origin  git@github.com:Anhdozxc/HN\_KS24\_CNTT2\_-IT-209-\_Devops\_Fundamentals\_DoHoangAnh\_Session04\_Ex02.git (fetch)

origin  git@github.com:Anhdozxc/HN\_KS24\_CNTT2\_-IT-209-\_Devops\_Fundamentals\_DoHoangAnh\_Session04\_Ex02.git (push)

```



URL remote có đúng định dạng SSH:



```text

git@github.com:username/repository.git

```



\## 6. Commit và đẩy bài lên GitHub



Thực hiện:



```powershell

git add homework/session\_04/ex3/README.md

git commit -m "Bài 3: Cấu hình SSH Ed25519"

git push -u origin main

```



Quá trình push sử dụng giao thức SSH để xác thực với GitHub.



\## 7. Đường dẫn repository GitHub



Repository:



https://github.com/Anhdozxc/HN\_KS24\_CNTT2\_-IT-209-\_Devops\_Fundamentals\_DoHoangAnh\_Session04\_Ex02



Thư mục bài tập:



```text

homework/session\_04/ex3/

```



\## 8. Kết luận



Đã hoàn thành:



\* Tạo cặp khóa SSH Ed25519.

\* Cấu hình SSH với GitHub.

\* Kiểm tra xác thực SSH thành công.

\* Cấu hình remote `origin` bằng giao thức SSH.

\* Commit và push bài tập lên GitHub.



Không đưa khóa private lên GitHub.



