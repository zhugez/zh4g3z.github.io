# Writeup Junior Hacking Talents CTF

# by ZhugeZ

## Networking:

## HTTP 101:

Với bài này ta chỉ cần truy cập tên miền của đề bài cho ” [http://http.kid.cyberjutsu-lab.tech/](http://http.kid.cyberjutsu-lab.tech/) ”
bằng cổng 5555 là ra flag. Link truy cập sẽ có dạng như sau: [http://http.kid.cyberjutsu-](http://http.kid.cyberjutsu-)
lab.tech:5555/

Và đây là kết quả :


FLAG: CTF{Hypertext_Transfer_Protocol}

## Domain Name System 101:

Ta có thể thấy bài này yêu cầu ta tìm IP của tên miền đã cho. Để giải bài này có nhiều cách
nhưng theo mình có hai hướng đơn giản như sau 1 là dùng extension trên chrome để tìm( mình


thường xài “ip whois & flags”) và cách thứ 2 là dùng cmd để ping tới tên miền web. Bây giờ ta
lần lượt thử từng cách nào.

Cách 1:

Truy cập vào tên miền dã cho thử, nhưng ở đây ta thấy server web không phản hồi lại..

Xem ra cách này không được rồi. Next tới cách 2 nha

Cách 2:

Ta mở cmd lên nhập lệnh sau vào: ping onepiece.kid.cyberjutsu-lab.tech. Và đây là thành
quả:

Dãy số tô màu vàng chính là địa chỉ ip ta cần tìm. Giờ thì đem đi submit thôi nào ^^.

FLAG: CTF{93.13.33.22}


## Socket 101:

Theo như đề bài ta thấy yêu cầu ta kết nối tới server bằng giao thức TCP vì vậy để làm được bài
này chúng ta cần phải có kiến thức về TCP/IP( Mình sẽ đính kèm link tài liệu tham khảo bên
dưới).

Link tham khảo TCP/IP: https://vi.wikipedia.org/wiki/TCP/IP

https://www.cloudflare.com/learning/ddos/glossary/tcp-ip/

Ở đây mình sử dụng netcat để mở một cổng kết nối TCP tới cổng với IP đã cho. Lệnh có dạng
như sau: nc <ip> <port>. Và đây là thành quả:

Giờ thì đi submit flag thôi nè :>

FLAG: CTF{connect_to_somewhere}


## File Sharing 101:

Ở bài này ta thấy đề yêu cầu ta kết nối tới server bằng giao thức FTP vì vậy để làm được bài này
chúng ta cần phải có kiến thức về FTP( Tương tự bài trước thì bài này mình cũng mình sẽ đính
kèm link vài nguồn tham khảo bên dưới).

Link tham khảo: https://vi.wikipedia.org/wiki/FTP

https://quantrimang.com/ftp-la-gi- 168304

Để thực hiện việc kết nối FTP thuận tiện hơn thì mình sử dụng tool Winscp trên Windows(mình
sẽ để link tải và hướng dẫn sử dụng Winscp phía dưới)

Link tải Winscp: https://winscp.net/download/WinSCP-5.19.2-Setup.exe

Link hướng dẫn sử dụng; https://winscp.net/eng/docs/start


Giờ ta chọn phương thức kết nối FTP rồi lần lượt điền IP , user,pass đề cho vào thôi(Port để mặc
định 22 nha).



Khi kết nối thành công ta thấy trên server có file flag.txt. Mở lên thử xem nào!

Ta đa! Flag đây rồi giờ đi submit thôi nào ^^

FLAG: CTF{File_Transfer_Protocol}

## Packet capture 101:

Nhiệm vụ của ta là tìm ra địa chỉ trang web mà nạn nhân đã truy cập trong khoảng thời gian bị
lừa đảo. Bài này cung cấp cho ta 1 file .pcapng. Ta dùng wireshark để phân tích file này.


Ta thấy khá nhiều gói tin. Bây giờ check thử từng gói xem sao.

Đây ta đã tìm ra được link trang web lừa dảo https://xacminhgarenavn.xyz/.

```
 FLAG: CTF{https://xacminhgarenavn.xyz/}
```
Giờ đi submit thôi nào :>


## Bài t ậ p quá h ạ n:

Theo ta thấy bài này yêu cầu tải lại file bài tập trên 1 trang web về mà đã hết hạn tải. Người ta
cung cấp cho mình 1 file gì đó, tải về giải nén ra thử ta thấy 1 file Accesss log và 1 file .pcapng

Trước hết ta phân tích file log-chat.pcapng bằng wireshark. Kiểm tra từng gói tin thử ta thấy đây
ghi lại đoạn chat giữa Minh và người bạn đây ta tìm thấy được password gì đó.

Tạm lưu lại password “emyeukhoahoc***2003”


Tiếp theo phân tích file access.log. Ta tìm lịch sử truy cập tới trang web tải bài tập.

Ở đây mình sử dụng Regrex để lọc ra đường dẫn các file mà Minh đã tải về trên trang web bài
tập.


Ở đây mình sẽ kiểm tra xem file các file Minh tải về (tải file bằng cách sử dụng đường dẫn đã lọc
được ). Giờ mình kiểm tra từ file có dung lượng lớn nhất nha :>

Ta thấy bắt điền password dể giải nén.


Ta điền thử password ta tìm được ở trên. Giải nén thành công ta thấy có file “ bai-tap-hinh-hoc-
lop-8.docx” mở lên thử và flag đây rồi ^^


Flag: CTF{1-l0ve-m4th-b9247d7608a7e63ae119982ff59db431}

Đem submit kiếm 200 điểm thôi nào. (^.^)


