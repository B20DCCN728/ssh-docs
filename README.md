## 🧬 **Bảng lệnh SSH trong Ubuntu**

| 🔢 **STT** | 💻 **Lệnh** | 🧠 **Chức năng** | ⚙️ **Cú pháp cơ bản** | 📘 **Ví dụ minh họa** |
|:--:|:--|:--|:--|:--|
| 1 | **`ssh`** | Kết nối đến máy chủ từ xa qua giao thức SSH | `ssh [user@]hostname` | `ssh user@192.168.1.10` |
| 2 | **`ssh -p`** | Kết nối SSH với cổng tùy chỉnh | `ssh -p [port] [user@]hostname` | `ssh -p 2222 root@server.com` |
| 3 | **`ssh -i`** | Dùng private key để đăng nhập | `ssh -i /path/to/key user@host` | `ssh -i ~/.ssh/id_ed25519 user@remote` |
| 4 | **`ssh -L`** | Tạo SSH Tunnel (forward port) | `ssh -L local_port:remote_host:remote_port user@host` | `ssh -L 8080:localhost:80 user@server` |
| 5 | **`ssh -N`** | Mở kết nối SSH mà không chạy lệnh | `ssh -N -L 8080:localhost:80 user@host` | (dùng cho tunneling) |
| 6 | **`ssh -X` / `-Y`** | Cho phép chạy ứng dụng GUI từ xa | `ssh -X user@host` | `ssh -Y dev@192.168.1.50` |
| 7 | **`scp`** | Copy file giữa máy cục bộ và máy chủ từ xa | `scp source destination` | `scp test.txt user@host:/home/user/` |
| 8 | **`scp -r`** | Copy thư mục đệ quy | `scp -r local_dir user@host:/remote/dir` | `scp -r ./project user@192.168.1.10:/var/www/` |
| 9 | **`scp -P`** | Copy file qua SSH port khác | `scp -P 2222 file user@host:/path` | `scp -P 2200 backup.zip root@server:/tmp/` |
| 10 | **`sftp`** | Giao diện FTP qua SSH (tương tác) | `sftp [user@]hostname` | `sftp user@192.168.1.10` |
| 11 | **`sftp put/get`** | Upload / Download file qua SSH | `put local_file` / `get remote_file` | `put main.py` / `get /etc/nginx/nginx.conf` |
| 12 | **`ssh-keygen`** | Tạo SSH key mới | `ssh-keygen -t rsa -b 4096 -C "email"` | `ssh-keygen -t ed25519 -C "me@ptit.edu.vn"` |
| 13 | **`ssh-copy-id`** | Copy public key lên server (đăng nhập không cần mật khẩu) | `ssh-copy-id [user@]host` | `ssh-copy-id user@192.168.1.5` |
| 14 | **`ssh-add`** | Thêm private key vào SSH agent | `ssh-add [key_path]` | `ssh-add ~/.ssh/id_ed25519` |
| 15 | **`ssh-add -l`** | Liệt kê các key đang được SSH agent quản lý | `ssh-add -l` | — |
| 16 | **`ssh-add -D`** | Xóa toàn bộ key trong agent | `ssh-add -D` | — |
| 17 | **`ssh-agent`** | Chạy trình quản lý SSH key trong nền | `eval "$(ssh-agent -s)"` | — |
| 18 | **`sshd`** | SSH Daemon (dịch vụ SSH server) | `sudo systemctl start ssh` | `sudo systemctl status ssh` |
| 19 | **`sshfs`** | Mount thư mục từ xa qua SSH như ổ đĩa cục bộ | `sshfs user@host:/remote_dir local_mount` | `sshfs user@192.168.1.10:/data ./remote_data` |
| 20 | **`fusermount -u`** | Unmount thư mục đã mount bằng SSHFS | `fusermount -u local_mount` | `fusermount -u ./remote_data` |
| 21 | **`rsync -e ssh`** | Đồng bộ file/thư mục hiệu quả qua SSH | `rsync -avz -e ssh src user@host:/dst` | `rsync -avz ./app/ user@server:/var/www/app/` |
| 22 | **`ssh -v` / `-vvv`** | Bật chế độ debug chi tiết khi kết nối | `ssh -vvv user@host` | (hữu ích khi lỗi xác thực) |

---

### 🧩 **Tóm tắt nhanh theo nhóm**

| **Nhóm lệnh** | **Lệnh liên quan** | **Công dụng chính** |
|----------------|--------------------|----------------------|
| Kết nối SSH | `ssh`, `ssh -p`, `ssh -i`, `ssh -L`, `ssh -X` | Đăng nhập, tạo tunnel, hiển thị GUI |
| Truyền file | `scp`, `sftp`, `rsync -e ssh` | Truyền file an toàn |
| Quản lý khóa | `ssh-keygen`, `ssh-copy-id`, `ssh-add`, `ssh-agent` | Sinh, thêm và quản lý SSH key |
| Dịch vụ SSH | `sshd`, `systemctl ssh` | Quản lý dịch vụ SSH server |
| Gắn ổ đĩa từ xa | `sshfs`, `fusermount -u` | Mount thư mục qua SSH |

