# Hồ sơ đề 06: Nền tảng học trực tuyến cho 1.000 sinh viên

Học phần Nhập môn Công nghệ nền tảng (RIPT1304). Hệ thống minh hoạ: Hanni, web học tiếng Trung.

Lớp: **RIPT1304-20261-01** · Nhóm: ............ · Mã đề tài: 06 · Ngày nộp: 23/11/2026

| Vị trí trong phiếu đề | Họ tên | Mã sinh viên | Phần việc chính |
| --- | --- | --- | --- |
| Sinh viên 1 | Phạm Hải Đăng | B24DCCC047 | Kiến trúc, bảng tính tài nguyên, lab k3s, API học liệu, giám sát |
| Sinh viên 2 | Lê Đình Thành | B24DCCC251 | Web học liệu, 3 học liệu, phát học liệu qua Nginx (vai CDN), đo phía trình duyệt |
| Sinh viên 3 | Bùi Thị Vân Anh | B24DCCC007 | Kịch bản tải, Kiểm thử 1 và 2, tổng hợp số liệu |
| Sinh viên 4 | Chu Hồng Đức | B24DCCC065 | Sao lưu, khôi phục, Kiểm thử 3, kiểm thử phân quyền, đánh giá mở rộng |

## Nội dung hồ sơ

Theo mục "Hồ sơ nộp chung" của phiếu giao đề.

| Thư mục hoặc tệp | Nội dung |
| --- | --- |
| `bao-cao/Bao-cao-nhom.docx`, `.pdf` | Báo cáo nhóm: 16 trang nội dung chính và 1 trang phụ lục cấu hình |
| `bao-cao/ca-nhan/` | 4 báo cáo cá nhân theo mẫu của đề (phiếu đóng góp cá nhân), mỗi bản có `.docx` và `.pdf`, tên tệp `Lớp_Nhóm_Đề_MSSV_BaoCaoCaNhan` |
| `so-do-va-bang/` | Sơ đồ kiến trúc, sơ đồ lab, bảng tài nguyên, IP, phân quyền và bảng tính tài nguyên |
| `cau-hinh-ma-nguon/` | Cấu hình, script và mã nguồn nhóm viết cho đề này, trích từ 2 repo bên dưới |
| `bang-kiem-thu.xlsx` | Bảng kiểm thử: đầu vào, thao tác, mong đợi, thực tế, đạt hay chưa, minh chứng có giờ chạy |
| `data/raw/` | Dữ liệu đo gốc, không sửa tay: k6, CPU/RAM, HAR, Lighthouse |
| `data/kt2-tong-hop.xlsx`, `data/rpo-rto.xlsx` | Bảng tổng hợp tính từ dữ liệu gốc |
| `evidence/` | Minh chứng theo ca kiểm thử, danh mục ở `evidence/README.md` |
| `video-demo.mp4` | Video demo 5–7 phút |

Mã nguồn đầy đủ nằm trên GitHub, ở nhánh riêng, chưa gộp vào nhánh chính nên web đang chạy cho người dùng không đổi:

| Repo | Nhánh | Commit | Nội dung |
| --- | --- | --- | --- |
| `github.com/DANG-PH/hanni-server` | `feat/scaling` | `4ef8a31` | API, `infra/` (lab k3s, k6, sao lưu, diễn tập, giám sát) |
| `github.com/DANG-PH/hanni-client` | `feat/hoc-lieu` | `3e78214` | Trang `/hoc-lieu`, test trình duyệt |

## Phiên bản

| Thành phần | Phiên bản |
| --- | --- |
| Docker Engine | 29.9.3 |
| k3s | v1.31.6+k3s1 (`rancher/k3s:v1.31.6-k3s1`) |
| Node.js trong image API | 22 (`node:22-slim`) |
| NestJS / TypeORM | 11 / 0.3.31 |
| Next.js / React | 16.3.4 / 19.2.8 |
| PostgreSQL / Redis | 16 / 7 (alpine) |
| PgBouncer | 1.24.1 |
| Nginx học liệu | `nginx:alpine` |
| Prometheus / Alertmanager / Grafana | 3.3.0 / 0.28.1 / 11.6.0 |
| Loki / Alloy / Jaeger | 3.4.2 / 1.8.3 / 2.5.0 |
| k6 | 0.57.0 |
| ffmpeg dựng học liệu | `linuxserver/ffmpeg:7.1.1` |

## Yêu cầu máy

Docker và Docker Compose v2, `make`, `bash`, `curl`, `python3`; còn trống từ 3 GB RAM, 8 GB đĩa. Mọi công cụ khác chạy trong container. Windows dùng qua WSL 2. Chỉ dùng dữ liệu giả.

## Dựng lại hệ thống

```bash
git clone -b feat/scaling https://github.com/DANG-PH/hanni-server.git
cd hanni-server/infra
make up              # tạo học liệu mẫu, bật 2 node, sinh mật khẩu ngẫu nhiên
make images          # build image API, nạp vào 2 node
make deploy          # PostgreSQL + bản sao, PgBouncer, Redis, API, worker, Nginx học liệu, tự thêm bản API, chặn mạng
make seed            # tạo bảng, nạp từ vựng, 1.000 tài khoản giả
make observability   # Prometheus, Alertmanager, Grafana, Loki, Jaeger
make status          # mọi pod phải ở trạng thái Running
```

Dựng từ đầu mất khoảng 5 phút trên máy ảo GitHub, khoảng 3,5 phút trên máy của Đăng khi đã có sẵn image (nhật ký ở `evidence/dung-lai/`).

Web nối vào lab, mở ở `http://hanni.localhost:3000`. Không dùng `localhost` vì trình duyệt sẽ không nhận cookie đăng nhập (khác tên miền với API):

```bash
git clone -b feat/hoc-lieu https://github.com/DANG-PH/hanni-client.git
cd hanni-client && npm install
NEXT_PUBLIC_API_URL=http://api.hanni.localhost:18080/api npx next dev -H hanni.localhost -p 3000
```

Tạm dừng cho nhẹ máy: `make stop`, `make start`. Xoá sạch: `make down`.

## Chạy kiểm thử

Chạy trong `hanni-server/infra`.

| Ca | Lệnh | Kết quả ở |
| --- | --- | --- |
| Kiểm thử 1: tải đúng học liệu | `scripts/kt1.sh k6/ket-qua/kt1.txt` | Từng tệp đúng hay sai, tổng dung lượng, thời gian |
| Kiểm thử 1 trên trình duyệt | `cd hanni-client && BASE_URL=http://hanni.localhost:3000 npm run test:hoc-lieu` | 5 ca: có dữ liệu, trống, lỗi, khách, không xin được liên kết |
| Kiểm thử 2: 3 mức tải | `scripts/chay-kt2.sh k6/ket-qua/kt2 "10 24 36" 3` | Điều kiện đo, kết quả k6, CPU/RAM từng lần |
| Tìm điểm nghẽn | `scripts/k6.sh tang-dan.js -e MAX_RATE=150 -e STEP=45s -e MAX_VUS=300 --no-thresholds` | Tóm tắt k6, bảng Grafana "Mở rộng" |
| Kiểm thử 3: dừng dịch vụ | `scripts/kt3-dung-dich-vu.sh k6/ket-qua/kt3 3` | Gián đoạn, thời gian cảnh báo, học liệu đúng hay sai |
| Kiểm thử 3: mất dữ liệu | `scripts/kt3-mat-du-lieu.sh` | Số dòng trước và sau, RPO, RTO |
| Kiểm thử phân quyền | `scripts/kiem-quyen.sh k6/ket-qua/quyen.txt` | Mã trả về mong đợi và thực tế từng ca |
| Tắt từng thành phần | `scripts/do-gian-doan.sh <tệp csv>` cùng lúc với `scripts/chaos.sh api\|redis\|db\|node` | Gián đoạn theo giây |
| Sao lưu tay, khôi phục | `scripts/kubectl -n hanni create job --from=cronjob/hanni-backup sao-luu-tay`, rồi `scripts/restore.sh` | Nhật ký sao lưu, số dòng sau khôi phục |

Tiêu chí đạt: 95% lượt đọc dưới 300 ms, 95% lượt ghi dưới 500 ms, lỗi dưới 0,5%, không bỏ lượt nào, máy không phải dùng swap trong lúc đo.

Số đo chính thức chạy trên máy ảo GitHub Actions (4 nhân, 16 GB) vì laptop không đủ RAM: đẩy nhánh `feat/scaling` sang nhánh `do-lab` (`git push origin feat/scaling:do-lab`) thì workflow tự dựng lab rồi chạy toàn bộ kiểm thử. Kết quả lượt ngày 09/11 nằm ở `data/raw/gha-09-11/`.

## Sửa cấu hình khi bảo vệ

Mỗi thông số hay bị yêu cầu đổi (số bản API, ngưỡng CPU, giới hạn request, thời hạn liên kết, thêm học liệu, mức tải, giờ sao lưu,
ngưỡng cảnh báo…) đều ghi rõ sửa ở tệp nào, áp dụng bằng lệnh gì, kiểm tra lại ra sao, chia theo từng người, trong
`cau-hinh-ma-nguon/hanni-server/infra/README.md`, mục "Sửa nhanh khi bảo vệ". Quy tắc chung: sửa tệp, chạy `make deploy`;
nếu sửa `k8s/app/config.yaml` hoặc `k8s/media-manifest.json` thì chạy thêm `scripts/kubectl -n hanni rollout restart deployment/hanni-api`.

## Nguồn tham khảo và cách dùng AI

Nguồn mã, image và tài liệu tham khảo ở mục 7 và 8 của báo cáo nhóm. Dữ liệu từ vựng và ghi âm: krmanik/HSK-3.0 (CC BY-SA 4.0); nghĩa tiếng Việt: CVDICT (CC BY-SA 4.0); âm Hán Việt: Unihan (Unicode License V3).

Nhóm dùng trợ lý lập trình Claude Code (Anthropic) để soạn bản nháp mã hạ tầng, kịch bản đo, script diễn tập, chạy đo trên lab và soạn bản nháp tài liệu. Mọi số liệu lấy từ tệp gốc trong `data/raw/` và `evidence/`. Mỗi thành viên chạy lại phần của mình và chịu trách nhiệm giải thích khi bảo vệ.
