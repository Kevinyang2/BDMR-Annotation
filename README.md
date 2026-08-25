# BDMR Annotation

A lightweight browser-based multi-user video annotation tool for producing QVHighlights/QV-M2-style JSONL annotations.

The server is implemented in a single Python file using only the Python 3.12 standard library. It supports video/query tasks, temporal windows, saliency scores, task packages, annotator/reviewer roles, review, and JSONL export.

## Included

- `tools/video_annotation_app.py`: annotation server and browser UI.
- `tools/video_annotation_app_README.md`: detailed workflow documentation.
- `data/samples/bdmr_train_en_100.jsonl`: 100 English BDMR annotation records for trying the import workflow.
- `data/samples/README.md`: sample provenance, sanitization, and field notes.

Videos, extracted features, checkpoints, user databases, uploaded files, and in-progress annotations are intentionally not included.

## Start

```powershell
python tools\video_annotation_app.py --host 127.0.0.1 --port 7860
```

Open <http://127.0.0.1:7860> and import `data/samples/bdmr_train_en_100.jsonl` from the reviewer interface.

To match records to local videos named after their `vid` field:

```powershell
python tools\video_annotation_app.py `
  --host 127.0.0.1 `
  --port 7860 `
  --video_root D:\path\to\videos `
  --import_jsonl train:data\samples\bdmr_train_en_100.jsonl
```

For LAN use, listen on `0.0.0.0` and restrict the Windows firewall rule to your private local subnet. Do not expose this development server directly to the public Internet.

Runtime state is stored under `annotation_workspace/` and is ignored by Git.

## Compatibility

Python 3.12 is recommended. The current implementation imports the deprecated standard-library `cgi` module and will require migration before Python 3.13.

## Data sample

The included English sample is drawn from this project's own BDMR annotation workspace. Local absolute `video_path` values were removed before publication; see `data/samples/README.md` for the exact extraction details.
