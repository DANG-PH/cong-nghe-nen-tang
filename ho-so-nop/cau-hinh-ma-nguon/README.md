# Cấu hình, script và mã nguồn

Trích từ 2 repo, chỉ gồm các tệp nhóm viết hoặc sửa cho đề 06 (so với nhánh chính). Bản đầy đủ chạy được ở GitHub, xem README của hồ sơ.

| Thư mục | Nội dung |
| --- | --- |
| `hanni-server/infra/compose.yaml`, `Makefile` | Cụm k3s 2 node trong Docker, các lệnh dựng lab |
| `hanni-server/infra/k8s/` | Cấu hình Kubernetes: API, worker, PostgreSQL + bản sao, PgBouncer, Redis, Nginx học liệu, tự thêm bản API, chặn mạng, sao lưu |
| `hanni-server/infra/k6/` | Kịch bản tạo tải: tự học, xem video, thi thử, tăng dần, đăng nhập |
| `hanni-server/infra/scripts/` | Script kiểm thử 1, 2, 3, kiểm thử phân quyền, tắt từng thành phần, sao lưu, khôi phục |
| `hanni-server/infra/observability/` | Prometheus, Grafana (3 bảng), luật cảnh báo, Loki, Jaeger |
| `hanni-server/infra/media/` | Nguồn học liệu và script dựng video HLS, PDF, MP3 |
| `hanni-server/infra/ci/`, `.github/workflows/` | Chạy toàn bộ kiểm thử và quay video demo trên GitHub Actions |
| `hanni-server/src/` | API học liệu (`modules/resources`), số liệu đo (`infra/metrics`), giới hạn request theo tài khoản, lưu tạm, chống gửi trùng bài |
| `hanni-client/app/(site)/hoc-lieu/`, `components/resources/`, `lib/resources.ts` | Trang Web học liệu |
| `hanni-client/tests/hoc-lieu.test.ts` | Test tự động trang học liệu |
