---
name: folder-yaml
description: Read and write `.folder.yaml`, the metadata file a folder keeps about itself (description and notes on its files). Use when exploring a folder tree, describing or annotating folders and files, or moving files between folders.
---
# .folder.yaml
A folder can describe itself in a hidden `.folder.yaml` inside it. The file travels with the folder and is committed with it. All keys are optional:
```yaml
desc: 天气数据抓取和展示    # what this folder is for
file-desc:                 # file NAME in this folder → what it is
  fetch.py: 抓取入口，每小时跑一次
```
Keep keys you don't recognise exactly as they are.
## Read
In an unfamiliar tree, find and read every `.folder.yaml` first (skip `.git` and dependency folders). It is the quickest map of what each part is for.
## Write
- Use a targeted in-place edit. Change only your key and keep comments, other keys, key order and quoting. Never round-trip the file through a YAML serializer.
- `desc` and every `file-desc` value: one line saying what it is actually for, plus anything non-obvious. Never just restate the name or type ("a folder", "the code", "Python script").
- Keep each description as short as it can be while still making the purpose clear; 65 bytes in UTF-8 is the hard maximum, not a target.
- Write descriptions in the system's language.
- `file-desc` keys are names in this folder, never paths. A subfolder describes itself with its own `desc`.
- Delete a key when it becomes empty; delete the file when nothing is left.
- UTF-8; the file name is exactly `.folder.yaml`.
- When you rename a file, rename its `file-desc` key. When you move a file to another folder, remove its entry from the old folder's `.folder.yaml` and add it to the new folder's (create the file if needed).
