# Git workflow và giải quyết conflict

1. Main baseline: 58959f4, README và .gitignore.
2. Nhánh service: backend 4c4389f, README 4f32afb, CI 735153d. PR #1 merge vào main: aca5c6d.
3. Nhánh UI từ baseline: 299dd22, sửa cùng dòng README theo nội dung form. PR #2.
4. Review độc lập AI phát hiện token Unicode gây TypeError; sửa và thêm regression test: 223b9f9.
5. Nhánh UI chạy git fetch origin rồi git merge origin/main. Git exit 1 là conflict thật cần xử lý:

~~~text
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
~~~

Bản marker trước giải quyết lưu tại conflict-before.txt. README cuối không chứa marker, giữ cả ý service và form, bổ sung hướng dẫn sử dụng.

6. git add README.md rồi git commit kết thúc merge; merge commit có hai parent, chứng minh lịch sử tích hợp.
7. Push UI; CI chạy lại; owner review công khai AI-assisted rồi merge PR #2. Giữ feature branches sau merge.

## Thành viên tiếp tục

Accept invitation, clone, tạo feature/ten-task từ main; tự đọc/chạy/đóng góp >=2 test trong phạm vi phân công; push PR. Thành viên khác để lại review thực dựa trên kết quả chạy. Nhãn A/B/C và review AI hiện có không giả lập người thật.
