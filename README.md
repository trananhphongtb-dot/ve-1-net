# Vẽ Đơn Giản (Android)

App Android (Capacitor 6) đóng gói từ bản web đã duyệt.

- Tên app: **Vẽ Đơn Giản**
- Package: `com.tranphong.ve1net`
- Version: 1.2 (versionCode 3)
- minSdk 24, targetSdk 36

## Nội dung

1. **Vẽ 1 Nét** — game vẽ 1 nét, 14 màn độ khó tăng dần, chấm nhỏ; thắng 1 màn thì tự vẽ lại không hướng dẫn, vẽ xong mới mở màn tiếp.
2. **Học Vẽ** — học vẽ từng nét (mèo, cá, nhà, hoa, ô tô, chim): mỗi lúc chỉ hiện 1 nét đứt, tô kín 90% mỗi nét mới qua bước; xong thì tự vẽ trên bảng trắng và chấm điểm /100.
3. **Vẽ Tự Do** — bảng vẽ tự do, 8 màu, 3 cỡ bút, tải PNG.

Chạy offline, không tài khoản.

## v1.2

Sửa bố cục safe-area: khung cố định 100dvh, tab trên nằm dưới safe-area-inset-top, nút dưới đẩy tận đáy, thanh thông báo nằm trong luồng (không cố định) — hình nền tràn được nhưng các nút không tràn lên thông báo.

## Build

Đẩy code lên `main` là GitHub Actions tự build debug APK
(`.github/workflows/build-apk.yml`, artifact `ve1net-apk`).
Bản web trong `www/index.html` được export từ artifact web
`ve-1-net-hoc-ve-don-gian` (sha256 `141c235161fc30ad1b2b0378845f0971bc4145f530a76ad86fc62bcb83dcfc9c`).

Icon launcher: `assets/icon.png` (bản base64 trong `assets-b64/`,
giải mã lúc build bằng `scripts/decode-assets.sh`).

Signing: debug APK ký bằng keystore cố định dùng chung với Bible Quiz / Kinh Koran
(`assets-b64/debug.keystore.b64`, cert SHA-256 F3:EF:92:34:FD:F8:7D:80:A7:85:ED:B6:CF:76:EB:56:6C:13:BC:64:55:E4:4C:D4:62:13:47:F4:45:54:6C:73),
workflow copy vào ~/.android/debug.keystore trước khi build. Lưu ý: v1.0 ký bằng key tạm của
runner (cert C4:C8:0D:07:...) nên v1.1 KHÔNG cài đè được lên v1.0 — cần gỡ v1.0 một lần duy nhất. Từ v1.1 trở đi mọi bản dùng chung khóa cố định này nên cài đè được lên nhau (v1.2 cài đè lên v1.1).
