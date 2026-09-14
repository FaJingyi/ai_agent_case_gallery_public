# Reference Mapping

材料名到源文件/实体/分镜的紧凑索引。`File` 列是 `09_h3_package/assets/` 下的包内图片文件名；`h3_request.json` 使用 H3 输入白名单 `03_asset_inventory/h3_input_asset_inventory.json.eligible_h3_input_assets[]` 的 media_url。

| Label | File | Role | Segment | Purpose |
| --- | --- | --- | --- | --- |
| 全局素材1 `<Subject 1>` (`<Picture 1>`) | ASSET_001.png | target_nail_art_pattern_reference (user_assets) | VS001_SEG1-4 | 目标美甲图案/配色/材质/立体装饰(显式替换) |
| 人物1 `<Subject 2>` (`<Picture 2>`) | RF_PERSON_001.png | person_reference (generated_reference_frames) | VS001_SEG3, VS001_SEG4 | 非特定身份表演者外观一致性锚点 |
| 场景1 `<Subject 3>` (`<Picture 3>`) | RF_SCENE_001.png | scene_reference (generated_reference_frames) | VS001_SEG1-4 | 暗调室内场景/光线/色调一致性锚点 |

## Media URLs (used by `h3_request.json`)

- `<Picture 1>` ASSET_001: `http://10.42.1.1:30100/v1/assets/asset_fa659afc64254b2eb2efcfca76c59d26/content`（白名单 `ASSET_001` 用户素材原始 URL）。包内 `assets/ASSET_001.png` 是 768x768 的 720p 级缩放副本，仅用于包内尺寸校验与映射；实体仍是同一用户素材。
- `<Picture 2>` RF_PERSON_001: `http://10.42.1.1:30100/v1/assets/asset_845e824cdd8d4f55863a03bb04b71903/content`（768x1024）
- `<Picture 3>` RF_SCENE_001: `http://10.42.1.1:30100/v1/assets/asset_927dd1b5c43c43f6987eeab7457b8dfb/content`（768x1376）

## Reference video (`<Video 1>`, no picture number)

- `test_data/nail-6/nail-6.mp4` — `http://10.42.1.1:30100/v1/assets/asset_b2b5d57bdcef45348fb28f8d59f8657a/content`
- role: `motion_camera_timing_reference`; 只参考构图/运镜/动作机制/镜头顺序/时间节奏/空间关系/连续性/信息揭示结构。

Picture 顺序与 `minimax_h3_prompt.md` / `h3_request.json` 的 `content[]` 图片顺序一致：`<Picture 1>`=ASSET_001, `<Picture 2>`=RF_PERSON_001, `<Picture 3>`=RF_SCENE_001；H3 图片数量 3/5。
