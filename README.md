# Gửi và nhận Email thông qua giao thức bảo mật PGP

## Các bước chi tiết của giao thức được thực hiện như sau:

- Giả sử Alice muốn gửi một email an toàn đến Bob, cô ấy cần thực hiện các bước sau:

    1. Tạo một khóa phiên (session-key) ngẫu nhiên ***Ks*** và mã hóa nó bằng khóa công khai của Bob sử dụng thuật toán RSA.

    2. Mã hóa nội dung email dạng văn bản gốc với khóa phiên ***Ks*** được tạo ở bước (1).

    3. Gửi cả khóa phiên đã được mã hóa từ bước (1) ***Ks*** cùng với email đã được mã hóa từ bước (2).

- Ở phía người nhận, Bob cần thực hiện các bước sau khi nhận được email từ Alice:

    1. Giải mã khóa phiên ***Ks***đã nhận được bằng khóa riêng tư của Bob.

    2. Sử dụng khóa phiên đã giải mã để giải mã email đã nhận.

- [Lý thuyết PGP protocol](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/PGP_Protocol.md)

- [Hướng dẫn cấu hình và demo](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/Config_guide_and_demo.md)

