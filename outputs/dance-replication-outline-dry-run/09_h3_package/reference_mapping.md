# 素材映射（Step 9 / H3 Ref2VA）

本文件既是从 `h3_packager_input.md` 素材名到来源文件、绑定实体与分镜的紧凑索引，也是 H3 Ref2VA `picture n` 到真实文件、角色、分镜和用途的映射表。H3 request JSON 由步骤 10 生成。

## picture n 映射表

| Label | File | Role | Segment | Purpose |
| --- | --- | --- | --- | --- |
| `picture 1` | `assets/rf_person_001.png` | person_reference | 分镜1-5 | 人物1 目标主体外观一致锚点（欧美女性舞者） |
| `picture 2` | `assets/rf_scene_001.png` | scene_reference | 分镜1-5 | 场景1 户外篮球场场景锚点 |

## 素材索引

| 素材名 | 类型 | 包内文件 | 媒体 URL | 来源 | 绑定实体 | 绑定分镜 | 用途 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 参考视频 | video | - (URL 输入) | http://10.42.1.1:30100/v1/assets/asset_c6c2c84b8c3c4e86b2f02626d9899757/content | `01_reference_video_analysis/analyzer_run/01_video_segments/segments/VS001.mp4` | - | 分镜1-5 | 仅参考运动结构/镜头语言/节奏/空间关系 |
| 人物1 | image | `assets/rf_person_001.png` (768x1360) | http://10.42.1.1:30100/v1/assets/asset_3c559c34f1f44395a6dbd582e4fc8e96/content | `08_reference_frames/rf_person_001.png` (master 1536x2720, generated_from_outline) | person1 | 分镜1-5 | 目标主体一致外观锚点 |
| 场景1 | image | `assets/rf_scene_001.png` (768x1360) | http://10.42.1.1:30100/v1/assets/asset_3e73b919e8744621b19d8086e5cdaf79/content | `08_reference_frames/rf_scene_001.png` (master 1536x2720, generated_from_outline) | scene1 | 分镜1-5 | 户外篮球场场景锚点 |
| 全局素材1 | text | 无 | 无 | `global_appearance#prop1` | prop1 | 分镜1-5 | 篮球架/篮筐背景陈设（已含于场景1 参考帧） |

## H3 输入顺序

1. `<Video 1>` = 参考视频（`asset_reference_video_001`）。
2. 用户素材：无。
3. `<Picture 1>` = `picture 1` = `assets/rf_person_001.png`（人物1），`<Picture 2>` = `picture 2` = `assets/rf_scene_001.png`（场景1）。
