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

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image.png?raw=true)

3. Kiểm tra danh sách khóa đã tạo:

        gpg --list-keys

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image1.png?raw=true)

4. Xuất khóa công khai để gửi cho máy Ubuntu:

        gpg --export -a "tên hoặc email" > public_key_kali.asc

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image2.png?raw=true)

5. Xuất khóa riêng tư (dùng để tạo chữ ký điện tử):

        gpg --export-secret-key -a "tên hoặc email" > private_key_kali.asc

    *Lưu ý, cần nhập mật khẩu đã tạo khi xuất khóa riêng tư.*

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image3.png?raw=true)

***Trên Ubuntu***

- Thực hiện tương tự các bước trên để tạo cặp khóa cho Ubuntu.

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image4.png?raw=true)

- Sau đó, xuất khóa công khai của Ubuntu:

        gpg --export -a "tên hoặc email của bạn" > public_key_ubuntu.asc

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image5.png?raw=true)

- Xuất khóa riêng tư của Ubuntu: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image25.png?raw=true)

***3. Trao đổi khóa công khai giữa hai máy***

***Chuyển khóa từ Kali sang Ubuntu***

Trên Kali, copy khóa công khai qua Ubuntu bằng ***SCP*** (nếu cả hai máy kết nối mạng).

Địa chỉ IP của máy Ubuntu: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image6.png?raw=true)

Sử dụng lệnh ***scp*** trên máy Kali: 

    scp public_key_kali.asc thinh181@192.168.152.163:~

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image8.png?raw=true)

***Lưu ý***, cần cài đặt ssh trên máy Ubuntu và khởi động ssh. 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image7.png?raw=true)

Trên Ubuntu, nhập khóa công khai của máy Kali:

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image9.png?raw=true)

***Chuyển khóa từ Ubuntu sang Kali***

Đảm bảo ssh server bên Kali đang hoạt động: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image10.png?raw=true)

Địa chỉ IP của máy Kali: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image11.png?raw=true)

Sử dụng lệnh ***scp*** trên máy Ubuntu: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image12.png?raw=true)

Trên máy Kali, import khóa công khai của máy Ubuntu: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image13.png?raw=true)

***4. Cấu hình Thunderbird để sử dụng PGP***

***Bước 1: Mở Thunderbird và thêm tài khoản email***

1. Mở Thunderbird trên cả hai máy.

2. Thêm tài khoản email.

3. Đảm bảo Thunderbird có thể gửi và nhận email bình thường.

***Máy Kali***: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image14.png?raw=true)

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image15.png?raw=true)

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image16.png?raw=true)

***Máy Ubuntu***

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image17.png?raw=true)

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image18.png?raw=true)

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image19.png?raw=true)

***Bước 2: Cấu hình OpenPGP***

1. Vào Thunderbird, chọn Tools (hoặc Settings).

2. Chọn Account Settings > End-to-End Encryption.

3. Chọn Add Key > Import an existing OpenPGP key.

4. Chọn khóa PGP (private_key_kali.asc trên Kali, private_key_ubuntu.asc trên Ubuntu).

5. Sau khi nhập thành công, đặt khóa này làm khóa mặc định cho tài khoản email.

*Lưu ý, cần chọn khóa riêng tư làm khóa mặc định nhằm tạo chữ ký điện tử xác định danh tính bên gửi thì mới có thể encrypt được mail.* 

***Máy Kali***

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image20.png?raw=true)

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image21.png?raw=true)

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image22.png?raw=true)

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image23.png?raw=true)

*Lưu ý, cần nhập mật khẩu đã tạo khi sinh khóa riêng tư nếu muốn import key.*

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image24.png?raw=true)

***Máy Ubuntu***

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image26.png?raw=true)

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image27.png?raw=true)

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image28.png?raw=true)

***5. Gửi email mã hóa từ Kali sang Ubuntu***

1. Trên Thunderbird của Kali, soạn email mới.

2. Nhập địa chỉ email của Ubuntu.

3. Chọn Encrypt

4. Soạn nội dung, nhấn Send.

***Máy Kali***

Chọn private_key_kali làm khóa mặc định: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image29.png?raw=true)

Soạn mail và chọn encrypt: 

*Khi được yêu cầu khóa công khai của bên nhận, click vào Resolve*. 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image30.png?raw=true)

Chọn Import Public Keys From File...

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image31.png?raw=true)

Chọn public_key_ubuntu:

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image32.png?raw=true)

Chọn Accept và Import: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image33.png?raw=true)

Import thành công khóa công khai của máy Ubuntu: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image34.png?raw=true)

Chọn Encrypt và Send Email:

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image35.png?raw=true)

***Máy Ubuntu***

Trong trường hợp private_key_ubuntu chưa được import: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image36.png?raw=true)

Không xem được email gửi từ bên Kali đã được mã hóa bằng public_key_ubuntu:

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image37.png?raw=true)

Trong trường hợp đã import private_key_ubuntu: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image38.png?raw=true)

Xem được email: 

![img](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/images/image39.png?raw=true)

















