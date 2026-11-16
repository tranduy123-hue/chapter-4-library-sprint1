# Hệ thống Quản lý Thư viện — Sprint 1 Mini

Bài thực hành Chương 4: Phát triển, Tích hợp và Đảm bảo chất lượng.

Trạng thái hướng dẫn: service thêm sách, SQLite, form HTML và unit test đã tích hợp.

- **Jira:** https://duygk45.atlassian.net/browse/KAN-12
- **Repository:** https://github.com/tranduy123-hue/chapter-4-library-sprint1
- **Backend PR #1:** https://github.com/tranduy123-hue/chapter-4-library-sprint1/pull/1
- **UI / tích hợp PR #2:** https://github.com/tranduy123-hue/chapter-4-library-sprint1/pull/2
- **CI:** https://github.com/tranduy123-hue/chapter-4-library-sprint1/actions

## Chạy ứng dụng

Yêu cầu Python 3.11 hoặc 3.12, có SQLite (bản Python chuẩn). Không cần cài thư viện ngoài.

~~~sh
git clone https://github.com/tranduy123-hue/chapter-4-library-sprint1.git
cd chapter-4-library-sprint1
python app.py
~~~

Mở http://127.0.0.1:8765. Dừng bằng Ctrl+C. Có thể chọn cổng và database:

~~~sh
python app.py --port 8766 --database demo.sqlite3
~~~

Database tạo tự động, không đưa vào Git. Đây là demo local; chưa có đăng nhập/phân quyền để triển khai công khai.

## User Story và tiêu chí chấp nhận

> Là thủ thư, tôi muốn thêm sách mới vào hệ thống để quản lý tài sản thư viện.

- Nhập tên sách, tác giả, ISBN; lưu id tự tăng, title, author, isbn vào SQLite.
- Tên/tác giả không rỗng; tối đa 255/150 ký tự; giữ nội dung nhập khi báo lỗi.
- ISBN-10/13 có checksum hợp lệ; bỏ khoảng trắng/gạch nối; chuẩn hóa X. ISBN duy nhất sau chuẩn hóa, kể cả hai lần ghi đồng thời.
- ISBN-10 và ISBN-13 tương đương coi là hai chuỗi riêng; không quy đổi chéo trong Sprint 1.
- Hiển thị sách đã lưu; khởi động lại vẫn còn dữ liệu.
- Tiền phạt: 5.000 đ/ngày, quá 10 ngày tăng 20% toàn bộ tiền phạt, <=0 ngày bằng 0.

Dữ liệu thử: **Clean Code / Robert C. Martin / 9780132350884**. Nhập lại **978-0-13-235088-4** để kiểm tra báo trùng.

## Kiểm thử

~~~sh
python -B -W error::ResourceWarning -m unittest discover -s tests -v
~~~

32 test: 7 repository, 10 service/validation, 7 tiền phạt, 8 HTTP integration. Test có Arrange–Act–Assert; dùng database tạm, không sửa dữ liệu thật. GitHub Actions kiểm tra Python 3.11 và 3.12.

| Test theo đề | Đầu vào (ngày) | Kết quả (đ) |
|---|---:|---:|
| testNoFine | 0 | 0 |
| testNormalFine | 5 | 25.000 |
| testHeavyFine | 11 | 66.000 |
| Biên âm | -1 | 0 |
| Biên không phụ thu | 10 | 50.000 |

Bổ sung: ISBN rỗng/sai/trùng, persistence, SQL injection, race condition, HTML escaping, CSRF Unicode, giữ form và chặn đọc mã nguồn qua HTTP.

## Sprint Planning

| ID | Task | Vai trò đề xuất | Giờ | Jira |
|---|---|---|---:|---|
| T1 | Bảng Book và UNIQUE ISBN | A | 1 | [KAN-13](https://duygk45.atlassian.net/browse/KAN-13) |
| T2 | Book Entity, BookRepository | B | 2 | [KAN-14](https://duygk45.atlassian.net/browse/KAN-14) |
| T3 | Service addBook, kiểm tra ISBN | B | 3 | [KAN-15](https://duygk45.atlassian.net/browse/KAN-15) |
| T4 | Form HTML, HTTP, xử lý lỗi | C | 4 | [KAN-16](https://duygk45.atlassian.net/browse/KAN-16) |
| T5 | Unit Test AAA, FineCalculator | A + trưởng nhóm | 3 | [KAN-17](https://duygk45.atlassian.net/browse/KAN-17) |
| T6 | Nhánh, PR, conflict, review | Cả nhóm | 2 | [KAN-18](https://duygk45.atlassian.net/browse/KAN-18) |
| | **Tổng ước lượng, không phải giờ thực tế** | | **15** | |

Đề cho phép Python thay Java; unittest tương đương JUnit. T5 tăng từ 2h mẫu lên 3h để gồm FineCalculator.

## Thành viên và bằng chứng

| Vai trò đề xuất | GitHub | Phần để thành viên kiểm tra/đóng góp |
|---|---|---|
| Trưởng nhóm | [tranduy123-hue](https://github.com/tranduy123-hue) | FineCalculator, 3 test theo đề, tích hợp |
| A | [lequanbaodepzai](https://github.com/lequanbaodepzai) | Database, >=2 test repository |
| B | [phanvanhao1103-create](https://github.com/phanvanhao1103-create) | Service, >=2 test service |
| C | [phanthanhthinhptt27-cmd](https://github.com/phanthanhthinhptt27-cmd) | Form/validation, >=2 test HTTP |

Đã gửi invitation tới 3 thành viên; đối chiếu tài khoản qua email commit công khai. Không đăng email riêng vào repo.

Mã/test hiện tại do trợ lý AI hỗ trợ tạo. Role A/B/C là phân công mô phỏng, **không chứng minh thành viên đã tự viết test**. Commit dùng tài khoản tích hợp duydat1412. Review từ owner ghi rõ AI-assisted; **không thay cho review độc lập của một trong ba thành viên**. Trước khi nộp đủ tiêu chí nhóm, thành viên cần accept invitation, tự đọc/chạy/đóng góp >=2 test cho phần mình và để lại review/comment thật trên PR. KAN-18 theo dõi phần này.

Lịch sử đã được sửa email tác giả theo yêu cầu chủ repo; xem [đính chính và hướng dẫn đồng bộ bản clone](docs/attribution-repair.md).

## Git workflow và conflict thật

Giữ ba nhánh main, feature/add-book-service, feature/add-book-ui trên remote sau merge. Không viết tính năng trực tiếp trên main.

Hai feature branches từ cùng baseline sửa cùng dòng trạng thái README. PR #1 merge trước; nhánh UI merge origin/main và gặp conflict README thật. Bản trước xử lý: [docs/conflict-before.txt](docs/conflict-before.txt); giải thích: [docs/git-workflow.md](docs/git-workflow.md). Dòng cuối kết hợp service và UI; commit giải quyết là merge commit có hai parent.

## Cấu trúc

- library/: entity, repository, service, fine calculator.
- schema.sql: bảng books và UNIQUE ISBN.
- app.py + web/: HTTP app và giao diện tiếng Việt.
- tests/: unit test và HTTP integration.
- docs/: workflow, báo cáo và bằng chứng.
- .github/workflows/tests.yml: CI.
