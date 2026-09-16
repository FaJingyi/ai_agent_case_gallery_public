# 复刻大纲审阅稿（shot_structure）

- `status`: `ready_with_assumptions`
- `generation_scope`: `single_generation_task`
- `replication_mode`: `shot_structure`
- 目标时长: 15.0s, 16:9（参考视频 2560x1440）
- 目标主体: 姜黄虎斑猫（`generation_assumption`，无用户素材）
- 目标文字: `"MetaX"`（用户文本确认）
- `output_dir`: `outputs/minimax-replication-outline-dry-run`
- 时间精度: 一位小数，截断

## 复刻来源

- `01_reference_video_analysis/reference_video_analysis.json`（`common_reference_video_analyzer.final.v1`）
- `05_replication_readiness/replication_readiness_check.json`：`ready_with_assumptions`，阻塞项 0
- 默认参考视频作为 H3 输入（`<video_1>`，前 15 秒截断版本）

## 参考元素处理计划（摘要）

| 元素 | decision | 目标绑定 |
| --- | --- | --- |
| 心形双圆视口遮罩 | inherit | 全部 4 个 shot 的黑色遮罩构图 |
| 移焦落焦 + 缓推 | inherit | U1 开场 |
| 横幅飘动 | inherit | U2 |
| 水平动态模糊 + 红色故障线转场 | inherit | U1/U2/U3 结尾 |
| 大特写镜面反射揭示 | inherit | U4 结尾 |
| 参考品牌字母 | adapt | 保留版式，文字替换为 `"MetaX"` |
| 参考人物模特 | adapt | 替换为姜黄虎斑猫 |
| 参考场景（深色候车亭/米色混凝土立面/裸混凝土天台） | adapt | 砂岩候车亭 / 红陶砖墙 / 绿化天台 |
| 参考品牌身份与人物身份 | discard | 仅审计 |

## 时间轴

### U1 0.0-4.0s | 砂岩候车亭落焦揭示

- 镜头: 眼平建立镜头，居中于心形视口；缓推；散焦→锐利
- 场景: `scene_pavilion` 浅暖砂岩候车亭横楣，深色凸起字母 `"MetaX"`，后墙投影
- 主体: `cat_1` / `cat_state_resting` 姜黄虎斑猫卧在长椅上
- 文本: 画内 `"MetaX"`（横楣）
- 参考帧: `scene_pavilion`、`cat_state_resting`
- 状态: 结果 `ready_with_assumptions`

| segment | 时间 | reference_function | 内容 |
| --- | --- | --- | --- |
| U1_S1 | 0.0-1.1 | visual_display | 散焦→落焦，揭示横楣字母与猫 |
| U1_S2 | 1.1-3.6 | action_or_interaction | 缓推，字母与猫持续可读 |
| U1_S3 | 3.6-4.0 | transition | 水平动态模糊 + 红色故障线退出 |

### U2 4.5-8.0s | 红陶砖墙旗帜低角度揭示

- 镜头: 低角度，轻微漂移
- 场景: `scene_brickwall` 高红陶砖墙 + 窄石台，深色挂杆悬挂青绿布幔，黑色竖排 `"MetaX"`，深蓝天
- 主体: `cat_1` / `cat_state_perched` 猫踞坐台上，尾巴垂落
- 文本: 画内 `"MetaX"`（布幔竖排）
- 参考帧: `scene_brickwall`、`banner`、`cat_state_perched`
- 状态: 结果 `ready_with_assumptions`

| segment | 时间 | reference_function | 内容 |
| --- | --- | --- | --- |
| U2_S1 | 4.5-6.5 | visual_display | 低角度揭示布幔与猫 |
| U2_S2 | 6.5-8.0 | action_or_interaction | 布幔强力飘动，随后动态模糊退出 |

### U3 8.5-11.5s | 天台钢制招牌前主体入画

- 镜头: 眼平中景，轻微漂移
- 场景: `scene_rooftop` 绿化天台，矮混凝土女儿墙 + 种植箱灌木，后方喷漆钢板大字 `"MetaX"`，远处城市楼群
- 主体: `cat_1` / `cat_state_standing` 猫立于女儿墙，侧身，尾上扬
- 文本: 画内 `"MetaX"`（钢板）
- 参考帧: `scene_rooftop`、`cat_state_standing`
- 状态: 结果 `ready_with_assumptions`

| segment | 时间 | reference_function | 内容 |
| --- | --- | --- | --- |
| U3_S1 | 8.5-10.0 | visual_display | 猫入画，字母在身后 |
| U3_S2 | 10.0-11.5 | action_or_interaction | 猫换姿转头，随后动态模糊退出 |

### U4 12.0-15.0s | 大特写镜面反射揭示收尾

- 镜头: 眼平大特写，固定机位
- 场景: `scene_closeup` 猫脸佩戴大号镜面银墨镜，猫爪搭在左侧镜框，背景天空与浅色建筑边缘散焦
- 主体: `cat_1` / `cat_state_sunglasses` → `cat_state_sunglasses_turn`
- 文本: 画内 `"MetaX"` 仅出现在镜片反射中
- 参考帧: `cat_state_sunglasses`、`sunglasses_worn`（预算合并）
- 状态: 结果 `ready_with_assumptions`

| segment | 时间 | reference_function | 内容 |
| --- | --- | --- | --- |
| U4_S1 | 12.0-13.5 | action_or_interaction | 猫爪搭框并小幅调整 |
| U4_S2 | 13.5-15.0 | closing_or_prompt | 轻微转头，反射字母在镜片中位移并保持到结束 |

## 文字与 logo 策略

- 画内实体文字（`in_scene_text_logo_plan[]`）：`"MetaX"` 随载体透视、材质与光照变化，进入 H3 生成描述。
- 后期叠加（`post_overlay_plan[]`）：左下角红色等宽标题、左下说明行、右下 field note，由 ffmpeg/opencv 叠加；H3 只生成 clean plate 并预留安全区。
- 缺口: `M003 overlay headline and field-note copy`（说明行与 field note 文案缺失），已在 prompt 中省略。

## 参考帧摘要

- `plan_required`: true
- 人物实体: 0；主体实体: 2（`cat_1`、`banner`）；场景实体: 3
- 状态参考帧: 7；H3 图片预算: 8
- 规划文件: `07_reference_frame_plan/reference_frame_plan.json`

## 记忆点迁移

- 心形双圆视口、移焦落焦、缓推、动态模糊+红色故障线转场、镜面反射收尾：保留机制。
- 原始品牌字母、原始人物身份与原始叠加文案：不迁移，仅审计。

## 缺失项与假设

- 缺失: `M001 cat reference asset`、`M002 MetaX logo artwork`、`M003 overlay headline and field-note copy`
- 假设: 猫外观为中性的姜黄虎斑猫；场景按可见差异锚点改写；`"MetaX"` 为同版式纯文字。

## 音频

- `unsupported_skipped`: music / bgm / sfx / singing / audio_mood_curve / beat_alignment
