# 参考视频复刻最终交付审阅稿

- schema: `common_replication_outline.v2`  status: **ready_with_assumptions**
- 参考视频: `test_data/dance/2_2_case2-H3-original.mp4` (10.125s, 竖屏 9:16, 24fps)
- 用户需求: 参考视频生成一条新视频，一位欧美女性在户外篮球场上跳舞
- 目标主体: 欧美女性舞者（人物1）；目标场景: 户外篮球场（场景1）
- 复刻模式: `shot_structure`；time_precision: truncate 到 0.1s
- timeline_unit_count: **1**（单镜头连续，无剪辑）
- temporal_segment_count: **5**（镜头内部节拍）
- h3_prompt_shot_count: **5**（prompt-level `[Shot 1]-[Shot 5]`，对应 5 个 temporal segments，**不是**新增/拆分参考镜头）

## 参考视频功能继承

- 结构/时间: 单镜头连续约 10.1s；固定机位、平视、中心全身构图，无剪辑点。
- 运镜/构图: 竖屏 9:16，主体居中，头顶与脚下留空间，中等景深。
- 动作机制: 静止起手 → 摆臂 → 上肢节拍 → 下肢交叉步/踢腿 → 单脚支撑收束；重心左右转移与节拍停顿。
- 场景风格: 户外开阔硬质场地 + 白色画线、自然漫射光、冷调低饱和、写实纪录质感。
- 信息节拍: 单镜头内动作能量逐步提升后自然收束。

## 分镜级审阅

| segment | 时间 | 参考功能 | 目标功能 | 场景迁移 | 主体/动作迁移 | 画面内实体文字/logo | 后期叠加 | 参考帧决策 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SEG001 | 0.0-1.0s | visual_display | opening_pose_and_establish | 户外看台/跑道 → 户外篮球场（保开阔硬质场地+白线+漫射光，改场边陈设为篮球架/围网） | 参考男性 → 欧美女性；静止站立起手，重心居中 | 无 | 无（不生成文字层） | 使用 rf_person_001 + rf_scene_001 | 无 | ready_with_assumptions |
| SEG002 | 1.0-2.0s | action_or_interaction | arm_extension_phrase | 同上，机位/光线/场景连续 | 双臂侧展收回，肩臂带动躯干轻微摆动 | 无 | 无 | 使用 rf_person_001 + rf_scene_001 | 无 | ready_with_assumptions |
| SEG003 | 2.0-4.0s | action_or_interaction | punch_beat_phrase | 同上，场景无跳变 | 双拳胸前/向前往复，重心随节拍左右移动 | 无 | 无 | 使用 rf_person_001 + rf_scene_001 | 无 | ready_with_assumptions |
| SEG004 | 4.0-7.0s | action_or_interaction | cross_step_kick_phrase | 同上，篮球架/篮筐保持背景陈设 | 交叉步、踢腿、转身晃动，重心左右转移，幅度增大 | 无 | 无 | 使用 rf_person_001 + rf_scene_001 | 无 | ready_with_assumptions |
| SEG005 | 7.0-10.1s | action_or_interaction | single_leg_groove_and_settle | 同上，连续到镜头结束 | 单脚支撑、另一脚点地/抬起，动作流畅收束 | 无 | 无 | 使用 rf_person_001 + rf_scene_001 | 无 | ready_with_assumptions |

## 文字、logo 与音频

- 画面内实体文字/logo: `in_scene_text_logo_plan[]` 为空；参考视频本身无可见文字/logo/水印，目标侧不新增可读文字。
- 后期叠加: `post_overlay_plan[]` 为空；H3 生成 clean plate，无需渲染文字层。
- 台词/口播/旁白: 无；ASR 检测到疑似歌曲人声，归入 `unsupported_audio`（`unsupported_skipped`），不复刻音乐/音效/唱歌/节奏。

## 参考帧

- 计划: `07_reference_frame_plan/reference_frame_plan.json`（2 帧，`person1` + `scene1`）。
- 生成: `rf_person_001`（人物1 纯人物参考图）、`rf_scene_001`（场景1 纯场景参考图），均由 `tool-sensenova-image-generation-skill` 文生图成功产出。
- 质检: 提交前质检 `passed`；两张参考帧已进入 H3 白名单；H3 包内副本按 768 短边预处理（768x1360）。

## H3 打包与生成状态

- H3 打包 handoff: `09_h3_package/h3_packager_input.md`（固定 `参考视频` / `音乐` / `全局素材` / `分镜内容` 结构）。
- Packager: `packager-minimax-h3` → `09_h3_package/minimax_h3_prompt.md`（Ref2VA 六段式）、`reference_mapping.md`、`pre_generation_checklist.md`、`_blueprint.md`。
- 校验: `validate_minimax_h3_package.py` 通过，`image_count=2`，`issues=[]`。
- 可提交 H3 request: `09_h3_package/h3_request.json`（model MiniMax-H3，768P，9:16，duration 10，1 参考视频 + 2 参考图）。
- 提交前素材顺序: `<Video 1>` 参考视频 → 用户素材（无）→ `<Picture 1>` 人物1 → `<Picture 2>` 场景1。
- H3 视频生成状态: **not_submitted**（dry-run 边界，仅产出 request/package，未提交、未运行 H3 视频生成）。

## 缺失项与假设

- 缺失输入: `mi_001 actor_identity`（生成回退，不阻塞）、`mi_002 post_overlay_text`（省略/中性化，不阻塞）。
- 生成假设: `ga_001`（女性主体外观合理补全）、`ga_002`（不可识别表演者）、`ga_003`（篮球场场景落地）。
- 阻塞项: 无。
