***1. Cài đặt Thunderbird và OpenPGP trên cả hai máy***

    sudo apt update && sudo apt install thunderbird -y

***2. Tạo cặp khóa PGP trên mỗi máy***

Mỗi máy sẽ có một cặp khóa riêng (khóa công khai và khóa riêng tư).

***Trên Kali Linux***: 

1. Mở terminal, tạo cặp khóa PGP:

        gpg --full-generate-key

2. Chọn thông tin như sau:

- ***Loại khóa***: RSA and RSA (default)
- ***Độ dài khóa***: 4096
- ***Thời gian hết hạn***: Tùy chọn (ví dụ: 0 để không hết hạn).
- ***Tên và email***: Nhập thông tin.
- ***Mật khẩu bảo vệ khóa***: Nhập mật khẩu an toàn.

![img](0)

3. Kiểm tra danh sách khóa đã tạo:

        gpg --list-keys

![img](1)

4. Xuất khóa công khai để gửi cho máy Ubuntu:

        gpg --export -a "tên hoặc email" > public_key_kali.asc

![img](2)

5. Xuất khóa riêng tư (dùng để tạo chữ ký điện tử):

        gpg --export-secret-key -a "tên hoặc email" > private_key_kali.asc

    *Lưu ý, cần nhập mật khẩu đã tạo khi xuất khóa riêng tư.*

![img](3)

***Trên Ubuntu***

- Thực hiện tương tự các bước trên để tạo cặp khóa cho Ubuntu.

![img](4)

- Sau đó, xuất khóa công khai của Ubuntu:

        gpg --export -a "tên hoặc email của bạn" > public_key_ubuntu.asc

![img](5)

- Xuất khóa riêng tư của Ubuntu: 

![img](25)

***3. Trao đổi khóa công khai giữa hai máy***

***Chuyển khóa từ Kali sang Ubuntu***

Trên Kali, copy khóa công khai qua Ubuntu bằng ***SCP*** (nếu cả hai máy kết nối mạng).

Địa chỉ IP của máy Ubuntu: 

![img](6)

Sử dụng lệnh ***scp*** trên máy Kali: 

    scp public_key_kali.asc thinh181@192.168.152.163:~

![img](8)

***Lưu ý***, cần cài đặt ssh trên máy Ubuntu và khởi động ssh. 

![img](7)

Trên Ubuntu, nhập khóa công khai của máy Kali:

![img](9)

***Chuyển khóa từ Ubuntu sang Kali***

Đảm bảo ssh server bên Kali đang hoạt động: 

![img](10)

Địa chỉ IP của máy Kali: 

![img](11)

Sử dụng lệnh ***scp*** trên máy Ubuntu: 

![img](12)

Trên máy Kali, import khóa công khai của máy Ubuntu: 

![img](13)

***4. Cấu hình Thunderbird để sử dụng PGP***

***Bước 1: Mở Thunderbird và thêm tài khoản email***

1. Mở Thunderbird trên cả hai máy.

2. Thêm tài khoản email.

3. Đảm bảo Thunderbird có thể gửi và nhận email bình thường.

***Máy Kali***: 

![img](14)

![img](15)

![img](16)

***Máy Ubuntu***

![img](17)

![img](18)

![img](19)

***Bước 2: Cấu hình OpenPGP***

1. Vào Thunderbird, chọn Tools (hoặc Settings).

2. Chọn Account Settings > End-to-End Encryption.

3. Chọn Add Key > Import an existing OpenPGP key.

4. Chọn khóa PGP (private_key_kali.asc trên Kali, private_key_ubuntu.asc trên Ubuntu).

5. Sau khi nhập thành công, đặt khóa này làm khóa mặc định cho tài khoản email.

*Lưu ý, cần chọn khóa riêng tư làm khóa mặc định nhằm tạo chữ ký điện tử xác định danh tính bên gửi thì mới có thể encrypt được mail.* 

***Máy Kali***

![img](20)

![img](21)

![img](22)

![img](23)

*Lưu ý, cần nhập mật khẩu đã tạo khi sinh khóa riêng tư nếu muốn import key.*

![img](24)


***Máy Ubuntu***

![img](26)

![img](27)

![img](28)

***5. Gửi email mã hóa từ Kali sang Ubuntu***

1. Trên Thunderbird của Kali, soạn email mới.

2. Nhập địa chỉ email của Ubuntu.

3. Chọn Encrypt

4. Soạn nội dung, nhấn Send.

***Máy Kali***

Chọn private_key_kali làm khóa mặc định: 

![img](29)

Soạn mail và chọn encrypt: 

*Khi được yêu cầu khóa công khai của bên nhận, click vào Resolve*. 

![img](30)

Chọn Import Public Keys From File...

![img](31)

Chọn public_key_ubuntu:

![img](32)

Chọn Accept và Import: 

![img](33)

Import thành công khóa công khai của máy Ubuntu: 

![img](34)

Chọn Encrypt và Send Email:

![img](35)

***Máy Ubuntu***

Trong trường hợp private_key_ubuntu chưa được import: 

![img](36)

Không xem được email gửi từ bên Kali đã được mã hóa bằng public_key_ubuntu:

![img](37)

Trong trường hợp đã import private_key_ubuntu: 

![img](38)

Xem được email: 

![img](39)

















