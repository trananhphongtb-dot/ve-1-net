# Vẽ 1 Nét — Học Vẽ Đơn Giản (Android)

App Android (Capacitor 6) đóng gói từ bản web đã duyệt.

- Tên app: **Vẽ 1 Nét**
- Package: `com.tranphong.ve1net`
- Version: 1.0 (versionCode 1)
- minSdk 24, targetSdk 36

## Nội dung

1. **Vẽ 1 Nét** — game vẽ 1 nét, 14 màn độ khó tăng dần, chấm nhỏ; thắng 1 màn thì tự vẽ lại không hướng dẫn, vẽ xong mới mở màn tiếp.
2. **Học Vẽ** — học vẽ từng nét (mèo, cá, nhà, hoa, ô tô, chim): mỗi lúc chỉ hiện 1 nét đứt, tô kín 90% mỗi nét mới qua bước; xong thì tự vẽ trên bảng trắng và chấm điểm /100.
3. **Vẽ Tự Do** — bảng vẽ tự do, 8 màu, 3 cỡ bút, tải PNG.

Chạy offline, không tài khoản.

## Build

Đẩy code lên `main` là GitHub Actions tự build debug APK
(`.github/workflows/build-apk.yml`, artifact `ve1net-apk`).
Bản web trong `www/index.html` được export từ artifact web
`ve-1-net-hoc-ve-don-gian` (sha256 `dab2868308dc2987baaff02c2aaf24b66c7a74dc995bd4156a9ab45bd5465067`).

Icon launcher: `assets/icon.png` (bản base64 trong `assets-b64/`,
giải mã lúc build bằng `scripts/decode-assets.sh`).
