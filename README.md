# Thien_phan — Demo redirect (GitHub Pages)

URL cố định cho khách: **https://ido241117.github.io/Thien_phan/**

## Bật GitHub Pages (lần đầu)

1. Vào repo → **Settings** → **Pages**
2. **Source**: Deploy from branch → branch `main`, folder `/ (root)`
3. Save — đợi 1–3 phút rồi mở link trên

## Sáng — bật demo

1. Chạy `run.md` + `cloudflared` trên VPS → copy URL tunnel (vd. `https://xxx.trycloudflare.com/map`)
2. Sửa `index.html` — thay **cả 2 chỗ** `TUNNEL_URL` bằng URL vừa copy
3. `git add index.html && git commit -m "redirect: bật demo" && git push`
4. Đợi Pages deploy (~1–3 phút), test tab ẩn danh
5. Gửi khách link GitHub Pages (không gửi URL tunnel)

### Template sáng

```html
<!doctype html>
<html lang="vi">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta http-equiv="refresh" content="0; url=TUNNEL_URL" />
    <title>Đang mở App...</title>
  </head>
  <body>
    <p>Đang chuyển sang App...
      <a href="TUNNEL_URL">Bấm vào đây</a> nếu không tự chuyển.</p>
  </body>
</html>
```

## Chiều — đóng demo

1. Thay toàn bộ `index.html` bằng template đóng bên dưới
2. `git add index.html && git commit -m "closed: tắt demo" && git push`
3. **Sau khi push xong** mới tắt tunnel / VPS

### Template chiều

```html
<!doctype html>
<html lang="vi">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>App đang tạm đóng</title>
    <style>
      body { font-family: system-ui, sans-serif; max-width: 32rem; margin: 4rem auto; padding: 0 1rem; }
    </style>
  </head>
  <body>
    <h1>App tạm thời đã đóng</h1>
    <p>Máy chủ app hoạt động trong giờ hành chính. Vui lòng quay lại vào ngày làm việc tiếp theo hoặc liên hệ dev.</p>
  </body>
</html>
```