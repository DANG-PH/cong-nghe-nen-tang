# Đề 06 – Nền tảng học trực tuyến cho 1.000 sinh viên

Học phần **Nhập môn Công nghệ nền tảng (RIPT1304)** · Lớp RIPT1304-20261-01 · Nhóm: Phạm Hải Đăng, Lê Đình Thành, Bùi Thị Vân Anh, Chu Hồng Đức · Hạn nộp **24/11/2026**.

Repo này chứa toàn bộ bài làm của nhóm: hồ sơ nộp cho thầy, 4 tài liệu học (mỗi người 1 bản) và sheet phân công.
Hệ thống minh hoạ là Hanni (web học tiếng Trung); thứ được chấm là cách nhóm thiết kế, đo, khôi phục và mở rộng hệ thống.

## Bắt đầu từ đâu

1. **Mở tài liệu học của bạn** trong thư mục [`tai-lieu-hoc/`](tai-lieu-hoc/). Chưa dùng dòng lệnh, Git, Docker bao giờ thì đọc **Phần 0** trước
   (cài công cụ, lệnh tối thiểu, cách hoàn tác khi sửa sai). Rồi phần 1 (kiến thức chung, Kubernetes cho người mới, **buổi thực hành đầu tiên**
   từng bước có "thấy gì là đúng"), rồi các phần riêng. Mọi đường dẫn tệp đều bấm được và mở đúng dòng trên GitHub.
2. **Đọc báo cáo của bạn** trong [`ho-so-nop/bao-cao/ca-nhan/`](ho-so-nop/bao-cao/ca-nhan/) và báo cáo nhóm
   [`ho-so-nop/bao-cao/Bao-cao-nhom.pdf`](ho-so-nop/bao-cao/Bao-cao-nhom.pdf).
3. **Tự chạy lại phần của bạn** theo mục "Chạy lại" trong tài liệu học.
4. **Tập trình bày 3 phút và ôn vấn đáp** bằng 2 phần cuối tài liệu học.

## Bạn là ai, đọc gì

| Thành viên | Tài liệu học | Báo cáo cá nhân (theo mã SV) | Cấu hình, script chính | Kết quả đo chính |
| --- | --- | --- | --- | --- |
| **Phạm Hải Đăng** (Sinh viên 1: kiến trúc, bảng tính tài nguyên, lab, API, giám sát) | [1-Pham-Hai-Dang.pdf](tai-lieu-hoc/1-Pham-Hai-Dang.pdf) | [B24DCCC047](ho-so-nop/bao-cao/ca-nhan/RIPT1304-20261-01_NhomXX_06_B24DCCC047_BaoCaoCaNhan.docx) | [k8s/app/api.yaml](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/k8s/app/api.yaml), [k8s/app/config.yaml](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/k8s/app/config.yaml), [bảng tính tài nguyên](ho-so-nop/so-do-va-bang/bang-tai-nguyen-ip-quyen.xlsx) | [ket-qua-kt2/](ho-so-nop/data/raw/gha-09-11/ket-qua-kt2/) |
| **Lê Đình Thành** (Sinh viên 2: web học liệu, video HLS, Nginx/CDN, đo trình duyệt) | [2-Le-Dinh-Thanh.pdf](tai-lieu-hoc/2-Le-Dinh-Thanh.pdf) | [B24DCCC251](ho-so-nop/bao-cao/ca-nhan/RIPT1304-20261-01_NhomXX_06_B24DCCC251_BaoCaoCaNhan.docx) | [trang /hoc-lieu](ho-so-nop/cau-hinh-ma-nguon/hanni-client/), [k8s/media-manifest.json](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/k8s/media-manifest.json), [k8s/app/media.yaml](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/k8s/app/media.yaml) | [lighthouse/](ho-so-nop/data/raw/lighthouse/), [so-sanh-video/](ho-so-nop/data/raw/gha-09-11/ket-qua-phu/so-sanh-video/) |
| **Bùi Thị Vân Anh** (Sinh viên 3: kịch bản tải, Kiểm thử 1 và 2, tổng hợp số liệu) | [3-Bui-Thi-Van-Anh.pdf](tai-lieu-hoc/3-Bui-Thi-Van-Anh.pdf) | [B24DCCC007](ho-so-nop/bao-cao/ca-nhan/RIPT1304-20261-01_NhomXX_06_B24DCCC007_BaoCaoCaNhan.docx) | [k6/](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/k6/), [scripts/chay-kt2.sh](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/scripts/chay-kt2.sh) | [kt2-tong-hop.xlsx](ho-so-nop/data/kt2-tong-hop.xlsx), [bang-kiem-thu.xlsx](ho-so-nop/bang-kiem-thu.xlsx) |
| **Chu Hồng Đức** (Sinh viên 4: sao lưu, khôi phục, Kiểm thử 3, phân quyền, mở rộng) | [4-Chu-Hong-Duc.pdf](tai-lieu-hoc/4-Chu-Hong-Duc.pdf) | [B24DCCC065](ho-so-nop/bao-cao/ca-nhan/RIPT1304-20261-01_NhomXX_06_B24DCCC065_BaoCaoCaNhan.docx) | [k8s/backup/](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/k8s/backup/), [scripts/](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/scripts/), [luật cảnh báo](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/observability/rules/hanni-slo.yml) | [ket-qua-kt3/](ho-so-nop/data/raw/gha-09-11/ket-qua-kt3/), [rpo-rto.xlsx](ho-so-nop/data/rpo-rto.xlsx) |

Muốn biết **sửa thông số nào ở tệp nào, lệnh gì để áp dụng** (thao tác hay bị yêu cầu khi bảo vệ): xem phần "Sửa và cấu hình trực tiếp" trong tài
liệu học của bạn, hoặc bảng chung [infra/README.md, mục "Sửa nhanh khi bảo vệ"](ho-so-nop/cau-hinh-ma-nguon/hanni-server/infra/README.md).

## Repo có gì

```
├── README.md                        ← tệp này
├── Hanni-RIPT1304-Phan-cong.xlsx    ← sheet phân công, 2 tab: Tổng quan, Công việc (nội bộ, không nộp)
├── tai-lieu-hoc/                    ← 4 tài liệu học, mỗi người 1 bản (nội bộ, không nộp)
└── ho-so-nop/                       ← ĐÚNG những gì nộp cho thầy (mục "Hồ sơ nộp chung" của phiếu đề)
    ├── README.md                    ← phiên bản, cách dựng lại hệ thống, cách chạy kiểm thử
    ├── bao-cao/                     ← báo cáo nhóm (.docx, .pdf) và 4 báo cáo cá nhân theo mẫu của thầy
    ├── so-do-va-bang/               ← sơ đồ hệ thống, bảng tài nguyên/IP/quyền, bảng tính tài nguyên
    ├── cau-hinh-ma-nguon/           ← cấu hình, script, mã nguồn nhóm viết cho đề
    ├── bang-kiem-thu.xlsx           ← bảng kiểm thử có giờ chạy
    ├── data/                        ← dữ liệu đo gốc (raw/, không sửa tay) và bảng tổng hợp
    ├── evidence/                    ← minh chứng theo ca kiểm thử (danh mục ở evidence/README.md)
    └── video-demo.mp4               ← video demo 6 phút
```

Mã nguồn đầy đủ, chạy được: [DANG-PH/hanni-server, nhánh feat/scaling](https://github.com/DANG-PH/hanni-server/tree/feat/scaling) và
[DANG-PH/hanni-client, nhánh feat/hoc-lieu](https://github.com/DANG-PH/hanni-client/tree/feat/hoc-lieu).

## Lấy repo về máy

```
git clone https://github.com/DANG-PH/cong-nghe-nen-tang.git
```

Không dùng git thì bấm **Code → Download ZIP** trên trang GitHub. Dựng lab để chạy lại phần của mình: xem mục 1.6 trong tài liệu học
hoặc [ho-so-nop/README.md](ho-so-nop/README.md). Máy yếu không dựng nổi thì nhắn Đăng chạy trên GitHub Actions.

## Quy tắc chung

- **Không sửa tay dữ liệu gốc** trong `ho-so-nop/data/raw/` và `ho-so-nop/evidence/`: thầy dùng chúng để kiểm số trong báo cáo.
- Báo cáo cá nhân đã điền đủ, chỉ còn **số nhóm** (chỗ `XX` trong tên tệp và dòng "Nhóm"), Đăng điền khi thầy công bố.
- Không đưa mật khẩu, dữ liệu cá nhân thật vào repo.
- Hạn nộp 24/11/2026; nhóm gom và nộp thư mục `ho-so-nop/` lên Drive thầy cung cấp trong ngày 23/11.

Nhóm có dùng trợ lý AI (Claude Code) để soạn bản nháp mã, chạy đo và soạn tài liệu; mọi số liệu lấy từ tệp đo gốc trong `ho-so-nop/data/raw/`.
Mỗi thành viên chịu trách nhiệm hiểu và giải thích phần của mình khi bảo vệ.
