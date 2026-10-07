# Sass variables và mixins

Bài chuyển CSS mẫu sang SCSS có biến và mixins. CSS đã biên dịch giữ nguyên định dạng ban đầu.

## Tổ chức
```text
abstracts/
  _variables.scss
  _mixins.scss
base/
  _typography.scss
components/
  _buttons.scss
  _cards.scss
main.scss
styles.css
original/styles.css
index.html
demo.css
package.json
package-lock.json
```

## Cách áp dụng
- _variables.scss: các biến màu, font-size, padding, radius và shadow.
- _mixins.scss: button-style($bg-color) nhận màu nền; box-style dùng biến để định dạng card.
- _typography.scss: h1 dùng $font-large; h2 dùng $font-medium; cả hai dùng $text-color.
- _buttons.scss: @include mixins.button-style(vars.$primary-color).
- _cards.scss: @include mixins.box-style.
- main.scss: nạp các module bằng @use. Mỗi partial tự nạp biến/mixins cần thiết.

Dùng @use theo hệ thống module của Dart Sass. Tài liệu: https://sass-lang.com/documentation/at-rules/use/.

## Cài và chạy
Mở terminal trong thư mục dự án:
```powershell
npm.cmd ci
npm.cmd run build
```
Mở index.html bằng trình duyệt.

Nếu Sass đã cài toàn cục:
```powershell
sass.cmd main.scss styles.css --no-source-map
```

## Thử đổi biến
```powershell
npm.cmd run watch
```
Đổi $primary-color từ red thành #7153d9 trong abstracts/_variables.scss, lưu và tải lại trang: cả hai nút sẽ đổi màu. Đổi $font-large để điều chỉnh h1; $card-radius để điều chỉnh cả hai card. Dừng bằng Ctrl+C.

Không sửa styles.css trực tiếp vì đây là đầu ra biên dịch.

## Trang minh họa
Hai nút dùng cùng class button, hai card dùng cùng class card, cho thấy định dạng được tái sử dụng. demo.css chỉ thêm bố cục minh họa responsive và không thay thế màu, font-size, padding, radius, shadow của CSS mẫu.

## Kiểm tra
- npm run build: thành công.
- CSS đầu ra khớp original/styles.css sau khi bỏ khoảng trắng.
- Kiểm tra đổi biến màu chung để xác nhận cả hai nút được cập nhật.
- Kiểm tra giao diện desktop/mobile; desktop.png và mobile.png là ảnh kết quả.

Node.js v22.19.0, Dart Sass 1.105.1. Không đưa node_modules lên GitHub.
