# Evidence — Day 22: LangSmith + Prompt Versioning

## Phân tích kết quả RAGAS: V1 vs V2

| Metric            | V1 (ngắn gọn) | V2 (có cấu trúc) |
|-------------------|---------------|-------------------|
| faithfulness      | 0.9625        | 0.9286            |
| answer_relevancy  | 0.9111        | 0.8923            |
| context_recall    | 1.0000        | 1.0000            |
| context_precision | 0.9417        | 0.9483            |

**V1 thắng về faithfulness và answer_relevancy**: prompt yêu cầu trả lời
ngắn gọn (2-4 câu) khiến model bám sát context, ít sinh thêm thông tin
ngoài dữ liệu — mỗi claim trong câu trả lời ngắn đều dễ đối chiếu được
với context nên faithfulness cao hơn.

**V2 nhỉnh hơn về context_precision**: phong cách "xác định facts liên
quan rồi trình bày có tổ chức" khiến câu trả lời khai thác đều các đoạn
context được truy xuất. Tuy nhiên câu trả lời dài hơn (3-5 câu) mở rộng
diễn giải, làm tăng nhẹ rủi ro claim không bám sát context.

**Kết luận**: với bộ QA dạng factual ngắn, prompt ngắn gọn (V1) là lựa
chọn tốt hơn; cả 2 version đều đạt faithfulness ≥ 0.9.
