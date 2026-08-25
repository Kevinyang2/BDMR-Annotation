# English BDMR annotation sample

`bdmr_train_en_100.jsonl` contains the first 100 non-empty records from the project's own English annotation file:

```text
annotation_workspace/merged_chinese_qv_final_20260512_221647/annotations_en/train.jsonl
```

All annotation fields and values are preserved except `video_path`, which was intentionally removed because it contained machine-specific absolute paths. The sample is a compact input for demonstrating the annotation tool.

Each line is a JSON object describing a query/video pair. Fields can include `qid`, `vid`, `query`, `duration`, `relevant_windows`, `relevant_clip_ids`, `saliency_scores`, and `split`. Referenced videos are not included.

