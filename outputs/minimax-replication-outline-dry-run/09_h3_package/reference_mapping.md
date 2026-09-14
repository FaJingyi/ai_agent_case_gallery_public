# H3 Packager Reference Mapping

## H3 picture 映射 (Ref2VA)

| Label | File | Role | Segment | Purpose |
| --- | --- | --- | --- | --- |
| picture 1 | assets/FRAME_SCENE1.png | scene reference (SCENE_1) | 分镜1 / TU001 | scene appearance anchor: ground-level street with the MetaX bus-stop shelter |
| picture 2 | assets/FRAME_SCENE2.png | scene reference (SCENE_2) | 分镜2 / TU002 | scene appearance anchor: building facade with the vertical MetaX banner |
| picture 3 | assets/FRAME_SCENE3.png | scene reference (SCENE_3) | 分镜3 / TU003 | scene appearance anchor: open rooftop with the 3D MetaX lettering |

参考图数量 3 / 上限 5。参考视频以 URL 形式作为 `<Video 1>` 输入，不占 picture 名额。

## 参考视频

| 素材名 | 包内文件 | 服务 URL | 绑定实体 | 适用分镜 | 用途 |
| --- | --- | --- | --- | --- | --- |
| 参考视频 | assets/reference_video_first15s.mp4 | http://10.42.1.1:30100/v1/assets/asset_5811419d16594adfbf8cca2096cbde3c/content | ref_video_excerpt_15s | 分镜1-4 | motion_structure_reference / camera_language_reference / beat_timing_reference / single_shot_rhythm_reference |

## 全局素材

| 素材名 | 包内文件 | 服务 URL | 来源实体 | 来源阶段 | 适用分镜 | 用途 |
| --- | --- | --- | --- | --- | --- | --- |
| 场景1 | assets/FRAME_SCENE1.png | http://10.42.1.1:30100/v1/assets/asset_6adfc892670d45389061bc3aa90ddefa/content | SCENE_1 | 生成参考帧 FRAME_SCENE1 | 分镜1 (TU001_S1, TU001_S2) | scene_appearance_reference / scene_consistency_anchor |
| 场景2 | assets/FRAME_SCENE2.png | http://10.42.1.1:30100/v1/assets/asset_ef20323a1c6047f88ba2b99917d3683a/content | SCENE_2 | 生成参考帧 FRAME_SCENE2 | 分镜2 (TU002_S1, TU002_S2) | scene_appearance_reference / scene_consistency_anchor |
| 场景3 | assets/FRAME_SCENE3.png | http://10.42.1.1:30100/v1/assets/asset_ca3e83e13fcb4e9a9aa194c2cdf48ba0/content | SCENE_3 | 生成参考帧 FRAME_SCENE3 | 分镜3 (TU003_S1, TU003_S2) | scene_appearance_reference / scene_consistency_anchor |
| 全局素材1 | 图片路径无 | - | MAIN_SUBJECT_1 | 复刻大纲全局外观库 (生成假设) | 分镜3, 分镜4 | 主角外观描述 (猫) |
| 全局素材2 | 图片路径无 | - | PROP_1 | 复刻大纲全局外观库 (用户文字) | 分镜1-4 | 画面内实体字母 MetaX |
| 全局素材3 | 图片路径无 | - | PROP_2 | 复刻大纲全局外观库 (生成假设) | 分镜4 | 红色几何墨镜道具 |

## 备注

- 无人物实体: 模特已按用户要求替换为猫, 猫属于 main_subject, 按 person/scene-only 规则不规划人物参考帧.
- 场景1/2/3 均已通过步骤 8 提交前质检并生成可用媒体, 已进入 H3 输入白名单 (`03_asset_inventory/h3_input_asset_inventory.json`).
- 画面内实体文字仅限用户确认的 "MetaX"; 参考视频专属边缘等宽 UI 文案未确认, 以中性红层后期叠加.
