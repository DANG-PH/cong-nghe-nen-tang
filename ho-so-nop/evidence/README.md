# Danh mục minh chứng

Mọi số trong báo cáo đều dẫn về 1 tệp ở đây hoặc ở `data/`. Tệp gốc không sửa tay.

| Nội dung | Vị trí | Thời điểm |
| --- | --- | --- |
| Dựng lại lab từ README trên máy của Đăng | `evidence/dung-lai/dung-lai-tu-readme.log` | 07/11/2026 08:32 |
| Dựng lại lab trên máy ảo GitHub ở mỗi lượt đo | `data/raw/gha-09-11/ket-qua-*/dung-lab.txt` | 09/11/2026 |
| Kiểm thử 1: tải 30 tệp, so mã băm SHA-256, 3 lần | `data/raw/gha-09-11/ket-qua-kt3/kt1/`, `evidence/KT1/` | 09/11 11:48 UTC; 07/11 08:51 |
| Kiểm thử 1: ảnh trang học liệu khi là khách và khi đã đăng nhập | `evidence/KT1/trinh-duyet-*.png` | 07/11 |
| Giao diện: ảnh 360, 390, 1440 px, sáng và tối; quét tràn ngang, bàn phím | `evidence/SV2/` | 07/11 08:50 |
| Test trình duyệt 5 ca, Lighthouse 3 lần mỗi chế độ | `data/raw/gha-09-11/ket-qua-phu/web/`, `data/raw/lighthouse/` | 09/11 |
| Ghi request của 1 phiên học (HAR) | `data/raw/har/` | 07/11 08:59 |
| Kiểm thử 2: đo thăm dò, 3 mức × 3 lần trước và sau cải tiến, CPU/RAM | `data/raw/gha-09-11/ket-qua-kt2/` | 09/11 từ 11:48 UTC |
| Kiểm thử 2: bảng tổng hợp | `data/kt2-tong-hop.xlsx` | Tính từ tệp gốc |
| Kiểm thử 3: dừng API 3 lần, cảnh báo, học liệu sau khi bật lại | `data/raw/gha-09-11/ket-qua-kt3/kt3-a/` | 09/11 |
| Kiểm thử 3: mất dữ liệu và khôi phục | `data/raw/gha-09-11/ket-qua-kt3/kt3-b.txt` | 09/11 |
| Tắt từng thành phần, mất CSDL chính, khôi phục về đúng thời điểm | `data/raw/gha-09-11/ket-qua-kt3/chaos/`, `failover*.txt`, `pitr.txt` | 09/11 |
| Sao lưu: nhật ký, chép ra ngoài cụm, thử lỗi, so sánh 2 cách | `data/raw/gha-09-11/ket-qua-kt3/sao-luu/` | 09/11 |
| Kiểm thử phân quyền | `data/raw/gha-09-11/ket-qua-kt3/quyen.txt` | 09/11 |
| Đăng nhập, nộp bài, tự thêm bản API, bản sao, video, 2 cách tạo tải, HLS với MP4 | `data/raw/gha-09-11/ket-qua-phu/` | 09/11 |
| Bảng RPO/RTO | `data/rpo-rto.xlsx` | Tính từ tệp gốc |
| Video demo quay từ thao tác thật | `video-demo.mp4` | 10/11 |

Nhật ký đầy đủ, có giờ từng dòng, của lượt đo chính thức: `github.com/DANG-PH/hanni-server/actions/runs/42611229757`.
