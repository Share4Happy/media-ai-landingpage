# LHU Media AI — Trợ lý Giám định & Đánh giá Tiêu chuẩn Kỹ thuật Nội dung Số

Landing page giới thiệu **LHU Media AI** — nền tảng hỗ trợ tổ chức và quản lý cuộc thi sáng tạo số với tích hợp AI phân tích video, hướng đến 4 nhóm người dùng: Ban tổ chức, Ban giám khảo, Thí sinh và Cộng đồng.

## Tính năng

- **Quản lý cuộc thi** — Tạo thể lệ, mốc thời gian, tiêu chí chấm điểm và giải thưởng.
- **Đăng ký & nộp bài** — Cổng thông tin trực tuyến cho thí sinh đăng ký và tải video.
- **AI Video Analysis** — Nhận diện kỹ thuật quay, chuyển động camera và khung hình tự động.
- **Chấm điểm giám khảo** — Giao diện chấm điểm chuyên nghiệp tích hợp báo cáo tham khảo AI.
- **Tổng hợp điểm tự động** — Tính toán, xếp hạng và xuất báo cáo kết quả.
- **Bình chọn cộng đồng** — Môi trường tương tác, theo dõi và bình chọn tác phẩm.

## Công nghệ sử dụng

- [React 19](https://react.dev/)
- [Vite 8](https://vitejs.dev/)
- [Oxlint](https://oxc.rs/docs/guide/usage/linter.html)

## Yêu cầu

- Node.js 20.19+ hoặc 22.12+ (khuyến nghị LTS)
- npm (đi kèm Node.js)

## Cài đặt & chạy local

```bash
# Cài đặt dependencies
npm install

# Chạy môi trường phát triển (HMR)
npm run dev

# Build sản phẩm vào thư mục dist/
npm run build

# Preview bản build
npm run preview

# Kiểm tra lint
npm run lint
```

Mở trình duyệt theo URL hiển thị trong terminal (mặc định `http://localhost:5173`).

## Deploy lên GitHub Pages

Dự án được triển khai tự động lên GitHub Pages thông qua GitHub Actions khi push lên nhánh `main`.

Trang sẽ có địa chỉ mặc định: **https://phatnd249.github.io/media-ai-landingpage/**

Vì dùng URL mặc định (không custom domain), `vite.config.js` đã được cấu hình:

```js
export default defineConfig({
  base: '/media-ai-landingpage/',
  plugins: [react()],
})
```

### Bật GitHub Pages lần đầu

1. Vào repository trên GitHub → **Settings**.
2. Chọn mục **Pages** ở thanh bên trái.
3. Tại **Build and deployment → Source**, chọn **GitHub Actions**.
4. Push lên nhánh `main` (hoặc vào tab **Actions** chọn workflow *Deploy to GitHub Pages* → **Run workflow**).
5. Workflow sẽ build bằng `npm ci` + `npm run build` (Node 20) và deploy thư mục `dist`.

### Cấu hình custom domain (tùy chọn)

Nếu muốn dùng domain riêng:

1. Đổi `base` trong `vite.config.js` thành `'/'`.
2. Tạo file `public/CNAME` với nội dung là domain, ví dụ:
   ```
   domain.com
   ```
3. Thêm file rỗng `public/.nojekyll` để tránh GitHub Pages xử lý qua Jekyll.
4. Khai báo domain tại **Settings → Pages → Custom domain** và cấu hình bản ghi DNS (CNAME) trỏ về `phatnd249.github.io`.

> Ghi chú: Các thư mục `node_modules` và `dist` đã được liệt kê trong `.gitignore`; GitHub Actions sẽ tự cài dependencies và build lại trên môi trường của nó.

## Cấu trúc thư mục

```
media-ai/
├── index.html              # Entry HTML
├── vite.config.js          # Cấu hình Vite
├── package.json
└── src/
    ├── main.jsx            # Điểm khởi chạy React
    ├── App.jsx             # Component gốc
    ├── assets/             # Hình ảnh & tài nguyên
    ├── components/
    │   ├── sections/       # Các section của landing page
    │   └── ui/             # Component UI dùng chung
    ├── data/               # Dữ liệu nội dung (features, solution, ...)
    └── styles/             # CSS global & variables
```