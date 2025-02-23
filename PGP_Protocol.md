# PGP Protocol

## Content

- [Giới thiệu PGP](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/PGP_Protocol.md#gi%E1%BB%9Bi-thi%E1%BB%87u-giao-th%E1%BB%A9c-pgp-pretty-good-privacy)

- [Kiến trúc của PGP](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/PGP_Protocol.md#i-ki%E1%BA%BFn-tr%C3%BAc-c%E1%BB%A7a-pgp)

- [Hoạt động của PGP](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/PGP_Protocol.md#ii-ho%E1%BA%A1t-%C4%91%E1%BB%99ng-c%E1%BB%A7a-pgp)

- [Ứng dụng của PGP](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/PGP_Protocol.md#iii-%E1%BB%A9ng-d%E1%BB%A5ng-c%E1%BB%A7a-pgp)

- [Quy trình thực tế của PGP trong việc đảm bảo tính bí mật](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/PGP_Protocol.md#iv-quy-tr%C3%ACnh-th%E1%BB%B1c-t%E1%BA%BF-c%E1%BB%A7a-pgp-trong-vi%E1%BB%87c-%C4%91%E1%BA%A3m-b%E1%BA%A3o-t%C3%ADnh-b%C3%AD-m%E1%BA%ADt)

- [Quy trình xác thực người gửi qua PGP](https://github.com/DucThinh47/PGP-Protocol-Demo/blob/main/PGP_Protocol.md#v-quy-tr%C3%ACnh-x%C3%A1c-th%E1%BB%B1c-ng%C6%B0%E1%BB%9Di-g%E1%BB%ADi-qua-pgp)

### Giới thiệu giao thức PGP (Pretty Good Privacy)

- PGP do Philip Zimmermann phát triển năm 1991: 
    
    - Cung cấp tính riêng tư (bí mật)
    - Cung cấp tính xác thực

- PGP được sử dụng rộng rãi và đã được thừa nhận thành chuẩn (RFC 3156). 

- PGP cho phép: 

    - Mã hoá dữ liệu sử dụng kết hợp mã hoá khoá bí mật và mã hóa khóa công khai 

    - Mã hóa khóa công khai được sử dụng để trao đổi khóa bí mật

    - Mã hoá khoá bí mật dùng để mã hóa/giải mã thông điệp.

- Tạo và kiểm tra chữ ký số

### I. Kiến trúc của PGP

PGP sử dụng một kiến trúc kết hợp giữa mã hóa đối xứng và mã hóa bất đối xứng để tận dụng ưu điểm của cả hai phương pháp:

***1. Mã hóa đối xứng***: Sử dụng cùng một khóa để mã hóa và giải mã dữ liệu. PGP thường sử dụng các thuật toán như AES (Advanced Encryption Standard) hoặc IDEA (International Data Encryption Algorithm) để mã hóa dữ liệu.

***2. Mã hóa bất đối xứng***: Sử dụng cặp khóa công khai (public key) và khóa bí mật (private key). Khóa công khai được dùng để mã hóa dữ liệu, còn khóa bí mật được dùng để giải mã. PGP thường sử dụng thuật toán RSA hoặc ElGamal cho mã hóa bất đối xứng.

***3. Hàm băm***: PGP sử dụng các hàm băm như SHA-1 hoặc MD5 để tạo ra các giá trị băm (hash) của dữ liệu, giúp đảm bảo tính toàn vẹn của thông tin.

### II. Hoạt động của PGP

Quá trình hoạt động của PGP có thể được tóm tắt như sau:

***1. Tạo khóa***: Người dùng tạo ra một cặp khóa công khai và khóa bí mật. Khóa công khai được chia sẻ công khai, trong khi khóa bí mật được giữ kín.

***2. Mã hóa dữ liệu***:

- PGP tạo ra một khóa đối xứng ngẫu nhiên (session key) để mã hóa dữ liệu.

- Dữ liệu được mã hóa bằng khóa đối xứng này.

- Khóa đối xứng sau đó được mã hóa bằng khóa công khai của người nhận.

***3. Ký điện tử***: Người gửi có thể ký điện tử vào dữ liệu bằng cách sử dụng khóa bí mật của mình. Chữ ký điện tử giúp người nhận xác minh tính xác thực của dữ liệu.

***4. Giải mã dữ liệu***:

- Người nhận sử dụng khóa bí mật của mình để giải mã khóa đối xứng.

- Sau đó, khóa đối xứng được dùng để giải mã dữ liệu.

***5. Xác minh chữ ký***: Người nhận sử dụng khóa công khai của người gửi để xác minh chữ ký điện tử, đảm bảo rằng dữ liệu không bị giả mạo.

### III. Ứng dụng của PGP

PGP (Pretty Good Privacy) là một giao thức bảo mật được sử dụng rộng rãi để mã hóa và ký các thông điệp điện tử (email, tệp tin) nhằm bảo vệ tính bảo mật và toàn vẹn của dữ liệu. PGP có nhiều ứng dụng thực tế trong các lĩnh vực khác nhau:

***1. Bảo mật Email***

- Ứng dụng chính của PGP là mã hóa email để bảo vệ nội dung khỏi bị đọc trộm và xác thực người gửi qua chữ ký điện tử.

- Khi người dùng gửi một email, họ có thể mã hóa nó bằng khóa công khai của người nhận. Điều này đảm bảo rằng chỉ người nhận có khóa riêng tương ứng mới có thể giải mã được nội dung.

- PGP cũng cho phép người gửi chữ ký số (digital signing) email để xác thực rằng email thực sự được gửi từ họ, không bị giả mạo.

***2. Bảo vệ File***

- PGP không chỉ mã hóa email mà còn có thể được sử dụng để mã hóa các tệp tin hoặc thư mục. Điều này bảo vệ dữ liệu quan trọng, chẳng hạn như các tài liệu tài chính, thông tin cá nhân, hoặc dữ liệu doanh nghiệp.

- Các tệp tin này có thể được mã hóa và gửi qua các kênh không an toàn, nhưng chỉ người có khóa giải mã mới có thể mở và xem nội dung tệp.

***3. Bảo mật Giao Tiếp Qua Internet (Web)***

- PGP có thể được sử dụng để mã hóa các giao tiếp giữa người dùng và các dịch vụ trực tuyến, đặc biệt là khi cần bảo vệ thông tin nhạy cảm, như trong việc đăng nhập hoặc truyền tải thông tin tài chính.

- Một ví dụ phổ biến là trong các giao thức PGP Web of Trust và PGP-encrypted chat services. PGP có thể được tích hợp vào các công cụ nhắn tin như Enigmail (cho Thunderbird) hoặc Mailvelope (cho trình duyệt web) để bảo mật các cuộc trò chuyện trực tuyến.

***4. Xác thực người dùng và tạo chữ ký số***

- PGP được sử dụng để tạo ra chữ ký số, xác thực người dùng trong các giao dịch trực tuyến hoặc xác nhận tài liệu.

- Điều này rất quan trọng trong các môi trường yêu cầu bảo mật cao, chẳng hạn như trong các hệ thống giao dịch tài chính hoặc các nền tảng điện tử cần chứng minh tính hợp pháp của các tài liệu.

- Ví dụ: PGP có thể được sử dụng để ký hợp đồng điện tử trong các giao dịch hoặc trong các yêu cầu bảo mật về dữ liệu.

***5. Bảo vệ quyền riêng tư***

- PGP giúp bảo vệ quyền riêng tư của người dùng bằng cách mã hóa thông tin cá nhân, tránh được sự xâm phạm từ các tổ chức hoặc cá nhân không có thẩm quyền.

- Nó cũng giúp người dùng kiểm soát được ai có quyền truy cập vào thông tin của họ, thông qua việc sử dụng khóa công khai và khóa riêng.

***6. Bảo mật phần mềm***

- Một ứng dụng quan trọng khác của PGP là trong việc bảo vệ phần mềm. Các nhà phát triển phần mềm có thể sử dụng PGP để ký các bản phân phối phần mềm (ví dụ: tệp cài đặt, bản vá lỗi) để đảm bảo rằng phần mềm không bị thay đổi hoặc tấn công.

- Ví dụ: PGP có thể được sử dụng để ký các bản cập nhật phần mềm, đảm bảo rằng người dùng chỉ tải về các bản cập nhật hợp lệ và không bị nhiễm mã độc.

***7. Chuyển giao dữ liệu an toàn***

- PGP cũng được sử dụng để bảo vệ các giao dịch dữ liệu bảo mật khi truyền tải giữa các máy chủ hoặc giữa các bên trong một tổ chức. Dữ liệu có thể được mã hóa trước khi chuyển, và chỉ những người có quyền (bằng khóa riêng) mới có thể giải mã dữ liệu này.

- Điều này rất quan trọng đối với các tổ chức xử lý thông tin nhạy cảm như các ngân hàng, công ty bảo hiểm hoặc tổ chức chính phủ.

***8. Tạo ra môi trường web bảo mật***

- PGP có thể được tích hợp vào các trang web hoặc ứng dụng trực tuyến để tạo ra một hệ thống bảo mật mạnh mẽ. Ví dụ, khi người dùng muốn gửi thông tin nhạy cảm qua forms trên web, PGP có thể giúp mã hóa thông tin này ngay từ phía người dùng và giải mã ở phía máy chủ, giúp bảo vệ khỏi các mối đe dọa như tấn công man-in-the-middle.

- Cũng có thể kết hợp PGP với HTTPS để tăng cường mức độ bảo mật cho các giao dịch và thông điệp trực tuyến.

***9. Giao tiếp Bảo mật trong Các Tổ Chức Chính Phủ hoặc Doanh Nghiệp***

- PGP thường được sử dụng trong các tổ chức có yêu cầu bảo mật cao, chẳng hạn như các cơ quan chính phủ, quân đội, hoặc các công ty trong ngành tài chính và ngân hàng. Trong những môi trường này, PGP đảm bảo rằng thông tin nhạy cảm, như dữ liệu khách hàng, tài liệu pháp lý, và các giao dịch tài chính, luôn được bảo vệ.

- Các tổ chức có thể sử dụng PGP để kiểm tra tính toàn vẹn của tài liệu và bảo vệ các tài liệu mật khỏi bị sửa đổi hoặc giả mạo.

***10. Ứng Dụng trong Bảo mật Tổ Chức Mã Nguồn***

- Các tổ chức phát triển phần mềm có thể sử dụng PGP để bảo mật mã nguồn khi trao đổi mã nguồn phần mềm qua Internet. Việc mã hóa và ký số các tệp mã nguồn giúp đảm bảo rằng không có sự thay đổi trái phép hoặc khai thác bảo mật trong mã nguồn phần mềm.

PGP vẫn là một trong những công cụ bảo mật quan trọng, giúp người dùng và tổ chức bảo vệ thông tin và giao dịch của họ khỏi các mối đe dọa bảo mật trong môi trường kỹ thuật số.

### IV. Quy trình thực tế của PGP trong việc đảm bảo tính bí mật

***Bước 1: Tạo khóa đối xứng***

- Khi người gửi muốn gửi một email an toàn, họ sẽ bắt đầu bằng cách tạo ra một khóa đối xứng ngẫu nhiên. Khóa này sẽ được dùng để mã hóa nội dung của email (hoặc file) mà họ muốn gửi.

- Khóa đối xứng này được chọn ngẫu nhiên, có thể là một khóa AES hoặc bất kỳ thuật toán mã hóa đối xứng nào. 

***Bước 2: Mã hóa dữ liệu bằng khóa đối xứng***

- Người gửi sẽ sử dụng khóa đối xứng tạo ra ở bước 1 để mã hóa nội dung email hoặc file.

- Sử dụng mã hóa đối xứng vì nó rất nhanh, là phương pháp tối ưu cho việc mã hóa khối lượng dữ liệu lớn. 

***Bước 3: Mã hóa khóa đối xứng bằng khóa công khai***

- Sau khi dữ liệu đã được mã hóa, người gửi sẽ sử dụng khóa công khai của người nhận (có được từ chứng chỉ PGP của người nhận) để mã hóa khóa đối xứng mà đã sử dụng trong bước 1. 

- Việc này đảm bảo chỉ người nhận có khóa riêng tương ứng với khóa công khai của họ mới có thể giải mã được khóa đối xứng. 

***Bước 4: Gửi thông điệp***

- Người gửi gửi một email chứa: 	

    - Dữ liệu đã được mã hóa bằng khóa đối xứng.

    - Khóa đối xứng đã được mã hóa bằng khóa công khai của người nhận. 

- Cả hai phần này sẽ được gửi qua email tới người nhận.

***Bước 5: Người nhận giải mã***

- Khi người nhận nhận email, họ sẽ sử dụng khóa riêng của mình để giải mã khóa đối xứng đã được mã hóa. Vì chỉ có người nhận mới có khóa riêng của mình, họ là người duy nhất có thể giải mã. 

***Bước 6: Mã hóa dữ liệu với khóa đối xứng***

- Sau khi người nhận giải mã khóa đối xứng, họ sử dụng nó để giải mã dữ liệu đã được mã hóa ở bước 2, khôi phục lại nội dung email hoặc file. 

### V. Quy trình xác thực người gửi qua PGP

Sử dụng PGP, người nhận có thể xác thực người gửi thông qua chữ ký điện tử (digital signature), điều này giúp đảm bảo tính xác thực trong PGP, cũng như để bảo vệ tính không thể phủ nhận của thông điệp.

***Bước 1: Tạo chữ ký điện tử***

- Khi người gửi muốn gửi một email hoặc file, họ sẽ tạo chữ ký điện tử cho nội dung của thông điệp. 

- Để tạo chữ ký điện tử, người gửi sử dụng khóa riêng của mình, quy trình được thực hiện như sau: 

    - Người gửi tạo một hàm băm của nội dung thông điệp.

    - Sau đó mã hóa hàm băm này bằng khóa riêng của mình để tạo ra chữ ký điện tử. 

***Bước 2: Gửi thông điệp với chữ ký***

- Người gửi gửi thông điệp đến người nhận, cùng với chữ ký điện tử đã được tạo ra ở bước trên. Như vậy, thông điệp sẽ bao gồm: 

    - Nội dung email hoặc file.

    - Chữ ký điện tử (mã hóa hàm băm của thông điệp) 

    - Khóa công khai của người gửi (thường gửi kèm trong email hoặc có sẵn trong hệ thống PGP của người nhận)

***Bước 3: Kiểm tra chữ ký điện tử***

- Khi người nhận nhận được thông điệp, họ sẽ thực hiện các bước để kiểm tra chữ ký điện tử, cũng như xác thực người gửi:

    1. Lấy khóa công khai của người gửi. 

    2. Người nhận sử dụng khóa công khai của người gửi để giải mã chữ ký điện tử và thu được hàm băm của thông điệp mà người gửi đã ký. 

    3. Người nhận tính toán lại hàm băm của nội dung thông điệp mà họ đã nhận.

    4. So sánh hàm băm mà họ vừa tính toán với hàm băm mà họ đã giải mã từ chữ ký điện tử. Nếu hai giá trị khớp nhau, nghĩa là nội dung thông điệp chưa bị thay đổi và chữ ký là hợp lệ.

    5. Nếu chữ ký hợp lệ, người nhận có thể xác nhận rằng thông điệp thật sự được gửi bởi người có khóa riêng tương ứng với khóa công khai mà họ đã sử dụng, nghĩa là người gửi đã ký thông điệp này bằng khóa riêng của mình. 

### VI. Quy trình đầy đủ: Mã hóa và xác thực thông điệp trong PGP

***Bước 1: Tạo khóa và cài đặt hệ thống PGP***

- Cả người gửi và người nhận cần tạo cặp khóa PGP của riêng mình, bao gồm: 

    - Khóa công khai (public key) và khóa riêng (private key).

    - Khóa công khai được chia sẻ công khai, trong khi khóa riêng được giữ bí mật.

    - Người gửi và người nhận cần phải trao đổi khóa công khai của nhau, để mỗi người có thể sử dụng khóa công khai của đối phương. 

***Bước 2: Người gửi tạo thông điệp và chữ ký điện tử***

- Người gửi muốn gửi một email cho người nhận. Để đảm bảo tính xác thực và bảo mật, thực hiện các bước: 

    1. Tạo thông điệp (ví dụ: nội dung email)

    2. Tạo chữ ký điện tử: 

    - Người gửi tính toán hàm băm của nội dung thông điệp.

    - Người gửi sử dụng khóa riêng của mình để mã hóa hàm băm này, tạo ra chữ ký điện tử. 

    3. Mã hóa thông điệp:

    - Người gửi tạo một khóa đối xứng (còn gọi là session key) ngẫu nhiên (ví dụ: khóa AES).

    - Người gửi sử dụng khóa đối xứng này để mã hóa nội dung thông điệp.

    4. Mã hóa khóa đối xứng:

    - Tiếp theo, người gửi sử dụng khóa công khai của người nhận để mã hóa khóa đối xứng mà người gửi đã sử dụng để mã hóa thông điệp. 

    - Việc này đảm bảo chỉ người nhận mới có thể giải mã khóa đối xứng, nhằm giải mã thông điệp.

***Bước 3: Gửi thông điệp***

- Người nhận gửi email, bao gồm: 

    - Thông điệp đã mã hóa (mã hóa đối xứng).

    - Chữ ký điện tử (được tạo từ hàm băm của thông điệp, mã hóa bằng khóa riêng của người gửi).

    - Khóa công khai của người gửi (nếu người nhận chưa có).

***Bước 4: Người gửi nhận thông điệp***

- Khi người gửi nhận được email, sẽ thực hiện các bước sau để xác thực và giải mã thông điệp: 

    1. Giải mã khóa đối xứng: 

        - Người nhận sử dụng khóa riêng của mình để giải mã khóa đối xứng đã được người gửi mã hóa bằng khóa công khai của người nhận. 

    2. Giải mã thông điệp:

        - Sau khi có được khóa đối xứng,  người nhận sử dụng nó để giải mã nội dung thông điệp mà người gửi mã hóa. 

    3. Kiểm tra chữ ký điện tử:

        - Người nhận lấy khóa công khai của người gửi (nếu chưa có). 

        - Người nhận sử dụng khóa công khai này để giải mã chữ ký điện tử và thu được hàm băm của thông điệp gốc.

        - Người nhận tính toán lại hàm băm của thông điệp vừa giải mã.

        - Nếu hàm băm tính toán lại khớp với hàm băm từ chữ ký, chứng tỏ thông điệp còn nguyên vẹn và thực sự được gửi từ người gửi (vì chỉ có người gửi mới có khóa riêng để tạo ra chữ ký điện tử hợp lệ)

***Bước 5: Xác nhận thông điệp***

- Nếu chữ ký điện tử hợp lệ và nội dung thông điệp không bị thay đổi, người nhận có thể xác nhận: 

    - Thông điệp được mã hóa một cách bí mật (bởi vì chỉ người nhận mới có thể giải mã nội dung thông điệp nhờ khóa đối xứng).

    - Thông điệp được gửi từ đúng người gửi (vì chữ ký điện tử là hợp lệ).

### VII. Ưu điểm của PGP

- Lợi ích chính của mã hóa PGP nằm ở thuật toán không thể phá vỡ của nó.

- Nó được coi là một kỹ thuật hàng đầu để cải thiện bảo mật đám mây và thường được sử dụng bởi những người dùng cần mã hóa các cuộc trò chuyện riêng tư của họ.

- Điều này là do PGP có khả năng ngăn chặn tin tặc, chính phủ truy cập vào các tệp hoặc email được mã hóa bằng PGP.

### VIII. Nhược điểm của PGP

- Độ phức tạp của việc sử dụng: Nhược điểm lớn nhất của mã hóa PGP là nó thường không thân thiện với người dùng. Mã hóa dữ liệu và tệp bằng PGP cần thời gian và công sức, điều này có thể làm phức tạp việc gửi tin nhắn cho người dùng. Các tổ chức phải cung cấp đào tạo nhân viên nếu họ đang xem xét triển khai PGP.

- Quản lý khóa: Người dùng cần hiểu đầy đủ cách thức hoạt động của hệ thống PGP để đảm bảo họ không vô tình tạo ra lỗ hổng trong hệ thống phòng thủ bảo mật của mình. Điều này có thể là do sử dụng PGP không đúng cách hoặc mất hoặc làm hỏng khóa, khiến những người dùng khác của họ gặp rủi ro trong môi trường bảo mật cao.

- Thiếu ẩn danh: PGP sẽ mã hóa các tin nhắn mà người dùng gửi, nhưng nó không ẩn danh chúng. Do đó, người gửi và người nhận email được gửi thông qua giải pháp PGP có thể được theo dõi. Dòng chủ đề của tin nhắn cũng không được mã hóa, vì vậy hãy tránh bao gồm dữ liệu hoặc thông tin nhạy cảm. Người dùng muốn ẩn vị trí của họ có thể sử dụng các trình duyệt ẩn danh thông qua máy chủ proxy hoặc mạng riêng ảo (VPN). Họ cũng có thể sử dụng các ứng dụng nhắn tin được mã hóa, chẳng hạn như Signal, cung cấp mã hóa hoặc ẩn danh dễ sử dụng, đây là một giải pháp thay thế hiệu quả hơn cho việc mã hóa dữ liệu được lưu trữ.

- Khả năng tương thích: Không thể sử dụng PGP trừ khi cả người gửi và người nhận thông tin liên lạc đều sử dụng cùng một phiên bản phần mềm.















