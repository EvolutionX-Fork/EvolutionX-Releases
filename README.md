# 📱 Hướng Dẫn Cài ROM Custom Evolution

🇺🇸 [View in English](README-EN.md)

> ⚠️ **Cảnh báo:** Việc flash ROM có thể xóa toàn bộ dữ liệu và có thể brick máy nếu thực hiện sai. Hãy sao lưu dữ liệu trước khi bắt đầu.

---

## 🔧 Yêu Cầu Trước Khi Bắt Đầu

- Máy tính đã cài **ADB & Fastboot**
- **Bootloader đã được mở khóa (unlocked)**
- File ROM: `evo_rom.zip`
- File boot: `boot.img`
- Đã bật **USB Debugging** trên điện thoại
- Cáp USB chất lượng tốt

---

## 📋 Các Bước Thực Hiện

### Bước 1 — Flash Boot Image

Kết nối điện thoại với máy tính qua USB, khởi động vào chế độ **Fastboot**, sau đó chạy lệnh:

```bash
fastboot flash boot boot.img
```

> ✅ Chờ cho đến khi terminal hiển thị `OKAY` hoặc `Finished` là thành công.

---

### Bước 2 — Khởi Động Vào Recovery

Sau khi flash boot thành công, khởi động máy vào chế độ **Recovery** bằng tổ hợp phím phần cứng (thường là `Volume Up + Power`) hoặc dùng lệnh:

```bash
fastboot reboot fastboot
fastboot reboot recovery
```

---

### Bước 3 — Wipe Data (Xóa Dữ Liệu)

Trong menu Recovery, thực hiện **Wipe Data / Factory Reset** để tránh xung đột với ROM cũ.

```
Recovery Menu → Wipe → Wipe Data / Factory Reset → Confirm
```

> ⚠️ Thao tác này sẽ **xóa toàn bộ dữ liệu** trên máy. Hãy chắc chắn đã sao lưu trước.

---

### Bước 4 — Vào Chế Độ ADB Sideload

Trong Recovery, chọn tùy chọn **ADB Sideload**:

```
Recovery Menu → Apply Update → Apply from ADB
```

Màn hình sẽ hiển thị trạng thái chờ kết nối từ máy tính.

---

### Bước 5 — Flash ROM Evolution qua ADB Sideload

Trên máy tính, chạy lệnh sau để bắt đầu cài ROM:

```bash
adb sideload evo_rom.zip
```

> ⏳ Quá trình này có thể mất vài phút. Đừng rút cáp USB trong lúc đang flash.  
> ✅ Khi hoàn thành, màn hình Recovery sẽ hiển thị thông báo thành công.

---

## 🚀 Hoàn Tất

Sau khi sideload xong, quay lại menu Recovery và chọn **Reboot System Now** để khởi động vào ROM Evolution.

```
Recovery Menu → Reboot → Reboot System
```

Lần khởi động đầu tiên có thể mất **5–10 phút**. Hãy kiên nhẫn chờ đợi.

---

## ❓ Xử Lý Lỗi Thường Gặp

| Lỗi | Nguyên nhân | Cách xử lý |
|-----|-------------|------------|
| `fastboot: command not found` | Chưa cài ADB/Fastboot | Cài Android Platform Tools |
| `no devices found` | Máy chưa nhận USB | Kiểm tra driver & cáp USB |
| Sideload bị dừng giữa chừng | Cáp USB kém | Dùng cáp khác, thử lại |
| Máy bị bootloop | Chưa wipe data | Wipe data rồi flash lại |

---

*🎉 Chúc bạn flash ROM thành công!*