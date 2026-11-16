# Đính chính tác giả commit

Theo yêu cầu chủ repo, ngày 16/11/2026 đã sửa email noreply bị nhập sai trong 8 commit của tài khoản tích hợp duydat1412. Tài khoản thasneem-810 không phải thành viên được xác nhận và không phải tác giả thực hiện công việc trong phiên này.

Email đúng được xác minh bằng GitHub API user: 116702145+duydat1412@users.noreply.github.com. Chỉ sửa các header author/committer có email sai; giữ nguyên ngày, thông điệp, nội dung cây file và cấu trúc merge. Các commit hậu duệ đổi SHA theo parent mới. Chữ ký commit cũ không thể giữ hiệu lực sau rewrite nên đã loại bỏ; không giả chữ ký mới.

Đã sao lưu toàn bộ refs trong bundle cục bộ trước thay đổi, kiểm tra git bundle verify thành công; backup không đẩy lên GitHub để tránh giữ lịch sử sai trong nhánh dự phòng. Bốn nhánh được đẩy đồng thời bằng --atomic và --force-with-lease theo SHA từng nhánh.

GitHub Contributors API sau sửa chỉ trả về duydat1412 và tranduy123-hue. Các URL commit/PR lịch sử có thể vẫn lưu snapshot SHA cũ; đó không phải lịch sử hiện hành trên các nhánh. Bảng ánh xạ đầy đủ: [commit-map.json](commit-map.json).

## Mốc bằng chứng mới

- Baseline: 58959f46d045999323276153b82fa441ce8b041f
- Backend: 4c4389f7cd60c2305aef28f11d41d2b2a02bf4c0
- Merge backend: aca5c6da221efed466c57875dd83880d5c36a217
- Merge giải quyết conflict: 27832d6d4cff9031c39bb3dab5d166de9f12fccc
- Tích hợp hoàn chỉnh trước đính chính tài liệu: 04c94881c52f4bc1a67f1331994f53e1f300e5bd

## Thành viên đã clone trước khi sửa

Cách đơn giản: giữ thư mục cũ (đặc biệt nếu có thay đổi chưa đẩy), clone lại repo vào thư mục mới rồi chuyển phần đang làm sang nhánh mới. Không pull/merge lịch sử cũ vào main vì sẽ đưa email sai trở lại. Nếu có commit chưa đẩy cần giữ, nhờ trưởng nhóm hỗ trợ cherry-pick từng commit lên lịch sử mới; không xóa thư mục cũ trước khi bảo toàn phần việc đó.

Việc sửa này không thay thế review hay đóng góp test thật của thành viên; KAN-18 vẫn theo dõi riêng.
