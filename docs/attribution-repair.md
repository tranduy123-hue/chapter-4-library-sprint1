# Tài khoản sử dụng cho bài tập

Theo yêu cầu chủ repo, các commit do trợ lý tạo đã được chuyển sang danh tính tranduy123-hue (GitHub ID 344689080). Đây là mã được AI hỗ trợ; tên tài khoản trong commit không thay thế bằng chứng đóng góp cá nhân của thành viên.

Tài khoản tích hợp đăng nhập sẵn trên máy đã bị gỡ quyền collaborator. Từ lần sửa này, các thao tác ghi GitHub của trợ lý cho repo dùng token do chủ repo cung cấp, không dùng tài khoản tích hợp đó.

Đã sao lưu lịch sử hiện tại trước khi viết lại; cập nhật cả năm nhánh bằng atomic push và lease theo SHA chính xác. Nội dung cây file, ngày, thông điệp và cấu trúc merge của tất cả 18 commit được giữ nguyên, chỉ sửa danh tính tích hợp trong 14 commit và các SHA parent phụ thuộc. Chữ ký cũ không thể còn hợp lệ sau rewrite nên đã loại bỏ.

Bảng ánh xạ đợt đầu giữ tại [commit-map.json](commit-map.json); đợt chuyển sang chủ repo tại [owner-commit-map.json](owner-commit-map.json). SHA conflict hiện hành: 22d050eb2f82c4d45ab20c984e81e5472b7382ba. SHA tích hợp ứng dụng: a715ac3d710a7767be2d9a73372a16a90460d37a.

## Giới hạn lịch sử Pull Request

GitHub không cho đổi người tạo PR đã tồn tại. Các PR cũ và activity lịch sử vẫn có thể hiện tài khoản tích hợp, dù contributor của lịch sử nhánh đã sửa. Không xóa repo hay làm mất bằng chứng PR đã merge. PR mới được tạo bằng tài khoản chủ repo.

## Đồng bộ máy thành viên

Giữ nguyên thư mục clone cũ nếu có phần việc chưa đẩy. Clone lại repo vào thư mục mới rồi chuyển phần việc cần giữ sang lịch sử mới. Không merge lịch sử cũ trở lại, vì sẽ khôi phục danh tính đã loại bỏ. Không xóa bản cũ trước khi bảo toàn thay đổi.

Review và đóng góp test thật của thành viên vẫn theo dõi tại KAN-18.
