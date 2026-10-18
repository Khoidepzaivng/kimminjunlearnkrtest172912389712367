# Hàn Ngữ Min Jun

Nền tảng học tiếng Hàn với 6 cấp độ, bài học từ vựng, lưu tiến độ, hỏi đáp và thanh toán khóa học.

## Chạy trên Replit

Ứng dụng dùng `pnpm`, PostgreSQL, Clerk và Stripe.

1. Cài gói: `pnpm install`
2. Trong Replit, kết nối Clerk và Stripe; không chép khóa bí mật vào GitHub.
3. Tạo/cập nhật bảng dữ liệu: `pnpm --filter @workspace/db run push`
4. Chạy API và trang web bằng các workflow đã cấu hình trong Replit.

API gọi Stripe qua kết nối Replit và chỉ cấp khóa học sau khi kiểm tra phiên
thanh toán thành công, đúng mã giá và đúng số tiền. Tệp
`scripts/src/seed-courses.ts` tạo bốn sản phẩm có giá được ghi trong trang gốc;
chạy bằng `pnpm --filter @workspace/scripts exec tsx src/seed-courses.ts`.
Hai khóa Cao cấp 5–6 hiện chưa có giá trong tài liệu gốc nên chưa thể mua.

## Đăng nhập và quyền giáo viên

Người học có thể đăng ký hoặc đăng nhập bằng Clerk. Để mở trang giáo viên,
thêm địa chỉ email của giáo viên vào biến môi trường `TEACHER_EMAILS`, phân
cách nhiều địa chỉ bằng dấu phẩy. Có thể thay thế bằng `publicMetadata.role`
trong Clerk (`teacher` hoặc `admin`). Không cấp quyền từ giao diện người dùng.

## Đưa mã lên GitHub

Không đưa `.env`, khóa Stripe/Clerk, hoặc dữ liệu người học lên GitHub. Dự án
dùng kết nối Stripe do Replit quản lý; nếu chạy ở nhà cung cấp khác, cần cấu
hình lại cách lấy khóa Stripe và thông tin Clerk bằng kho bí mật của máy chủ đó.

Mã dự án không khai báo giấy phép MIT mặc định. Việc bán hoặc cấp phép sản phẩm
thương mại cần được chủ sở hữu quyết định riêng.
