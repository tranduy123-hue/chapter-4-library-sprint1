# Bàn giao review và đóng góp test của nhóm

Mã nguồn trên main đã có 32 test pass và CI Python 3.11/3.12. Phần còn lại theo đề là bằng chứng tham gia của thành viên thật. Không đánh dấu các ô này chỉ dựa trên mã do AI hỗ trợ tạo.

## Nhận việc

- [ ] lequanbaodepzai: accept invitation, đọc schema và repository, tự đóng góp ít nhất 2 test database.
- [ ] phanvanhao1103-create: accept invitation, đọc service, tự đóng góp ít nhất 2 test logic thêm sách.
- [ ] phanthanhthinhptt27-cmd: đã accept invitation; đọc form/HTTP, tự đóng góp ít nhất 2 test xử lý biểu mẫu.
- [ ] tranduy123-hue: đọc FineCalculator; tự xác nhận và đóng góp ít nhất 2 test trong phạm vi của mình.
- [ ] Ít nhất một thành viên khác tác giả PR để lại review/comment thật dựa trên đọc mã và chạy test.

## Quy trình cho mỗi người

~~~sh
git clone https://github.com/tranduy123-hue/chapter-4-library-sprint1.git
cd chapter-4-library-sprint1
git switch -c feature/your-test-task
python -B -W error::ResourceWarning -m unittest discover -s tests -v
~~~

Đọc phần được phân công, tự viết hoặc cải thiện ít nhất hai test có kiểm tra hành vi thực và Arrange/Act/Assert rõ ràng. Không chỉ đổi tên test, sao chép lại test hiện có hoặc dùng git commit với danh tính của người khác. Commit bằng tài khoản của chính mình, push nhánh và mở PR vào main. Trong mô tả PR, nêu hai ca kiểm thử và kết quả chạy. Một thành viên khác đọc và review trước merge.

Gợi ý phạm vi còn có ích, không phải bằng chứng đã làm:

- Database: kết nối thứ hai đọc được dữ liệu đã commit; initialize hai lần không xóa sách.
- Service: checksum ISBN sai không để lại bản ghi; thay khoảng trắng tên/tác giả được lưu đúng.
- HTTP: body vượt giới hạn trả 413; content type khác trả 415; dữ liệu lỗi không làm mất sách đã lưu.
- Tiền phạt: 1 ngày = 5.000đ; 12 ngày = 72.000đ; mỗi test nêu rõ quy tắc đang bảo vệ.

## Nội dung review cần có

Ghi câu nhận xét của chính bạn sau khi đọc mã, kèm môi trường chạy và kết quả. Kiểm tra ISBN duy nhất, biên 10/11 ngày, thông báo lỗi form, dữ liệu lưu lại sau mở database. Nếu phát hiện lỗi, để lại yêu cầu cụ thể; không approve khi chưa đọc/chạy.

## Đính chính liên kết tác giả commit

Cấu hình Git ban đầu của trợ lý dùng nhầm ID số trong email noreply của tài khoản tích hợp. Vì vậy một số commit cũ có thể được GitHub liên kết tới thasneem-810; tài khoản đó không được xác nhận là thành viên hoặc người đóng góp của bài này. Tác vụ tạo mã và commit được thực hiện bởi trợ lý qua tài khoản tích hợp duydat1412. ID đã được xác minh qua GitHub API là 116702145; cấu hình các commit mới đã được sửa và .mailmap ghi ánh xạ đúng cho các công cụ hỗ trợ nó. Sau đó chủ repo đã yêu cầu sửa triệt để: lịch sử trên tất cả nhánh đã được viết lại để đính chính email sai, với bản sao lưu và force-with-lease. GitHub Contributors API đã loại tài khoản liên kết sai. Chi tiết và bảng SHA cũ/mới ở [attribution-repair.md](attribution-repair.md).

PR bàn giao chứa bản sửa này và vẫn chờ review thật của nhóm. Không dùng liên kết tác giả sai hoặc review bot làm bằng chứng tham gia nhóm.

## Gắn bằng chứng vào Jira

Dán link PR, commit và review thật vào https://duygk45.atlassian.net/browse/KAN-18. Chỉ chuyển mục này và KAN-12 sang Done khi có đủ bằng chứng thành viên theo đề. Review AI-assisted có sẵn trong PR #1/#2 vẫn giữ nguyên nhãn công khai.
