# Báo cáo cá nhân — Ngày 2 Object Detection

Đổi tên file theo `MSSV_HoTen.md`, ví dụ `20241234_NguyenVanAn.md`. Điền kết quả thật, xóa dòng hướng dẫn khi nộp. Xem [quy định nộp](../../SUBMISSION.md).

## 1. Thông tin học viên

- Họ tên: Nguyễn Quốc Việt
- MSSV: 202603224
- Email: vietnguyen10022001@gmail.com
- Lớp: L2B
- Link repo bài làm: https://github.com/nguyenquocviet1002/K5-L2B-DAY02-NguyenQuocViet-2A202603224-ObjectDetection-
- Link Colab đã chạy:https://colab.research.google.com/github/nguyenquocviet1002/K5-L2B-DAY02-NguyenQuocViet-2A202603224-ObjectDetection-/blob/main/notebooks/day2_annotation_to_yolo.ipynb?hl=vi#scrollTo=3e0508d8

## 2. Schema và mini guideline

Dẫn tới [GUIDELINE_MINI.md](../../GUIDELINE_MINI.md). Tóm tắt ba ca mơ hồ đã quyết định, cách áp dụng schema và phần cần giảng viên làm rõ.

## 3. Annotation và self-QC

- Số file nhãn train: 50
- Kết quả checker và lỗi đã xử lý: đủ 50 file nhãn
- Danh sách ít nhất 10 ảnh đã rà bằng mắt: kiểm tra từ ảnh 001 - 010
- Lỗi bỏ sót/box/class phát hiện khi rà và cách sửa: không phát hiện bỏ sót
- Commit khóa nhãn ban đầu: https://github.com/nguyenquocviet1002/K5-L2B-DAY02-NguyenQuocViet-2A202603224-ObjectDetection-/commit/f7d752f5760db0d6c52c901e5fbe5997f82b36d1

## 4. Gold QC và rework

| Chỉ số | Trước sửa | Sau sửa nếu có |
|---|---:|---:|
| TP | 446 | |
| FP | 453 | |
| FN | | 207 |
| Precision | 0.4961 | |
| Recall | 0.683 | |
| F1 | 0.5747 | |
| mean_iou_of_matches | 0.8471 | |
| passed | false | |

Dẫn tới `outputs/annotation_evaluation.json` [Truy cập link](../../outputs/annotation_evaluation.json) trong repo. Nếu rework, ghi ảnh, lỗi đã kiểm, quyết định sửa/giữ và lý do. Không suy nguyên nhân chỉ từ FP/FN. Không có rework thì ghi rõ.

## 5. Kết quả YOLO

- Runtime, GPU/CPU, phiên bản Ultralytics và Torch: Ultralytics 8.4.208 🚀 Python-3.13.16 torch-2.14.1+cu130 CUDA:0 (Tesla T4, 14913MiB)
- Các tham số thay đổi so với notebook nếu có và lý do: không thay đổi gì
- Đường dẫn best checkpoint trong phiên chạy: [Link](./assets/yolo26_runs/vehicle_annotation/weights/best.pt)

| Chỉ số trên 10 ảnh eval | Giá trị |
|---|---:|
| Precision | 0.4105453698519763 |
| Recall | 0.23026854853628678 |
| mAP50 | 0.27225886498171903 |
| mAP50–95 | 0.20168300309748077 |

Đặt cả 2 folder `assets/eval_predictions/` và `assets/yolo26_runs/` (giải nén từ `day2_colab_outputs.zip`) cạnh báo cáo và dẫn link tương đối. Không chỉ ghi số; chỉ ra ít nhất một ảnh và vật thể cụ thể.

Trả lời bốn câu hỏi cuối notebook:

1. Lớp nào recall thấp nhất? Ảnh nào minh họa?
```
lớp có recall thấp nhất là truck
ảnh minh hoạ là ảnh drive_051.jpg
```

2. Nếu mAP50 cao nhưng mAP50–95 thấp, cần kiểm điều gì trên box?
```
cần kiểm tra lại box có bị vẽ quá rộng hay là quá chật không
kiểm tra box có bị dài hay ngắn hơn không ở 1 số cạnh
```

3. Lỗi class nào có thể liên quan guideline? Dữ kiện nào hỗ trợ nhận xét?
```
lỗi nhận biết về car và van, khó phân định rạch ròi nếu chưa có quy định cụ thể
ảnh drive_051.jpg nhầm lẫn giữa van và car
```
4. Vì sao không dùng 10 ảnh eval để train? Vai trò validation của chúng trong notebook là gì?
```
để tránh việc rò rỉ dữ liệu, tránh mô hình học vẹt gây ra kết quả sai lệch
vai trò của chúng là đánh giá tính trực quan, tinh chỉnh các tham số như Threshold và IoU, phát hiện lỗi dữ liệu trong guideline
```

## 6. Khó khăn và cách xử lý

| Bước/thời điểm | Lỗi quan sát | Cách đã thử | Kết quả/còn thiếu |
|---|---|---|---|
| bước gán nhãn class | nhầm lẫn giữa car và van | bb theo guideline mini tự định nghĩ | vẫn còn sai lệch vì mô tả class chưa được chuẩn |

## 7. Tự đánh giá theo rubric

Đối chiếu [RUBRIC.md](../../RUBRIC.md): phần nào đã có kết quả, phần nào còn thiếu hoặc chưa kiểm được. Không tự nhận hoàn thành bước chưa chạy.
```
các phần đã có kết quả
phần Gold-set annotation QC có số điểm f1 chưa khớp
```

## 8. Công cụ AI và tài liệu tham khảo

Ghi công cụ đã dùng, dùng ở bước nào và phần đã tự kiểm tra; không dùng thì ghi rõ. Liệt kê nguồn ngoài repo được sử dụng. Không ghi mật khẩu/token hoặc đính kèm gold train.
