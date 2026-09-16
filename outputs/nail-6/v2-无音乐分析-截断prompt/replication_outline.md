# 复刻大纲审阅稿

- schema_version: `common_replication_outline.v2`
- status: `ready_with_assumptions`
- generation_scope: `single_generation_task`
- 参考视频: `test_data/nail-6/nail-6.mp4`（12.6s / 1080x1920 / 30fps，单一连续镜头）
- 目标视频: 竖屏 9:16 单一连续镜头自拍，12.6s
- 用户需求: 将参考视频里的美甲的图案替换成素材图片里的美甲图案，人物的装扮需要和美甲风格一致。
- 时间精度: 一位小数截断（`2.567 -> 2.5`）

## 1. 目标视频概述

| 项目 | 内容 |
| --- | --- |
| 主体 | 非身份化中性人物，双手十指佩戴目标哥特美甲，面部在结尾揭示 |
| 主体设计 | 素材图 `shangpin-3.png` 的 10 片长尖形穿戴甲：黑/棕/银 + 立体浮雕眼睛 + 珍珠 + 银色金属纹 + 金色边框水钻 |
| 场景 | 室内梳妆/美妆角落：深炭灰墙面、暗色丝绒帷幔、复古梳妆镜与暖色灯泡 |
| 装扮 | 与美甲风格一致：黑色高领长袖蕾丝上衣配银色刺绣与珍珠、深色近黑波浪发、暗色哥特妆、深色做旧金属配饰 |
| 镜头 | 竖屏中近景自拍、中心构图、紧凑特写、浅景深、手持近静止、无剪辑 |

## 2. 参考元素处理决策

| element_id | 类型 | 决策 | 参考元素 | 目标处理 |
| --- | --- | --- | --- | --- |
| ret_001 | time_structure | inherit | 单一连续镜头 12.633s | 保留总时长与三段内部节拍 |
| ret_002 | shot_structure | inherit | 单 shot，无拆分 | 保留 shot 数量与顺序 |
| ret_003 | camera | inherit | handheld_static、广角自拍、固定焦点 | 保留手持轻晃与焦段感 |
| ret_004 | composition | inherit | 竖屏中近景、三层空间 | 保留构图、前中后景与浅景深 |
| ret_005 | action_structure | inherit | 手部展示动作链 | 保留时间顺序与节拍 |
| ret_006 | other | inherit | 面部前方旋转展示戒指（micro_action） | 保留遮挡悬念机制 |
| ret_007 | other | inherit | 手指张开展示甲面（micro_action） | 保留甲面正对镜头展示 |
| ret_008 | other | adapt | 面部揭示后说话并头部轻倾 | 无目标台词，改为正向可见表情与头部轻倾 |
| ret_009 | subject_content | adapt | 参考美甲（白底+浅蓝渐变+闪粉） | 替换为目标哥特美甲设计（rb_001） |
| ret_010 | person_or_body | adapt | 参考人物装扮与身份 | 改为非身份化中性人物 + 暗色哥特华丽装扮（rb_002） |
| ret_011 | prop | adapt | 金戒指、金手链、金项链 | 改为深色做旧金属配饰 |
| ret_012 | scene_content | adapt | 汽车内部 | 改为室内梳妆空间，保留光比与空间结构 |
| ret_013 | visual_style | adapt | 明亮日常自拍 | 改为暗调华丽自拍 |
| ret_014 | transition | inherit | 无转场单一连续镜头 | 保留无剪辑结构 |
| ret_015 | dialogue_or_voiceover | adapt | 英文口播 | 无目标台词，改为正向可见表情 |
| ret_016 | unsupported_audio | discard | 音频分析 skipped | 音乐/BGM/音效保持 unsupported_skipped |
| ret_017 | incidental_detail | discard | 项链吊坠不可读图案/疑似 logo | 仅源侧审计，不进入目标画面 |

## 3. 记忆点迁移计划

| memory_id | 类型 | 保留机制 | 目标适配 | 绑定 |
| --- | --- | --- | --- | --- |
| vm_001 | visual / micro_action | 手部展示动作链的时间顺序与节拍 | 展示对象替换为目标美甲与深色金属配饰 | seg_001, seg_002, seg_003 |
| vm_002 | visual / spatial_reveal | 由局部（手部/甲面）到整体（面部）的揭示顺序 | 被揭示人物替换为非身份化中性人物 | seg_003 |
| sm_001 | script / opening_hook | 高辨识度局部细节特写开场、面部先遮挡后揭示 | 展示对象与场景替换为目标侧内容 | seg_001, seg_002 |
| sm_002 | script / information_release_sequence | 局部细节 -> 主体揭示 -> 情绪收束 | 口播替换为正向可见表情 | seg_001, seg_002, seg_003 |

- audio 记忆点为空；音乐、BGM、音效、疑似唱歌、声音情绪与卡点节奏保持 `unsupported_skipped`。

## 4. 场景迁移

**preserve_scene_style**: 光照层次、三层空间深度、竖屏中近景构图关系、自拍平视机位、中等背景密度、写实生活化自拍、手机竖屏手持质感、轻松亲密展示氛围。

**adapt_scene_content**: 地点由车内改为室内梳妆角落；陈设由车座椅/车窗/树木改为丝绒帷幔、复古梳妆镜、暖色灯泡与暗色摆件；材质由皮革/玻璃改为丝绒/做旧金属/镜面玻璃/深色木石；色彩由黑灰+窗外绿改为炭黑/深棕/银灰+暖金与珍珠白。

**scene_description_for_generation**: 室内梳妆/美妆角落：深炭灰墙面与暗色丝绒帷幔构成背景，右侧可见复古梳妆镜与暖色灯泡画内光源，深色木质台面上有少量暗金色与银黑色装饰摆件；画内暖色灯光与柔和侧向自然光混合，室内整体偏暗、局部镜面与金属形成高光，中等偏高反差；前景为目标人物双手与目标美甲，中景为面部与上身，背景柔和虚化，浅景深，氛围暗调华丽而亲密。

## 5. 时间轴与内部节拍

| segment | 时间 | 参考功能 | 目标功能 | 生成画面 | 动作/运镜 | 使用素材 | 参考帧决策 | 缺失/审计 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| seg_001 | 0.0-3.5s | action_or_interaction | 开场钩子：面部前方旋转展示美甲与配饰，遮挡制造悬念 | 目标人物双手十指交扣握拳举在面部前方，反复转动手腕；面部被遮挡 | 前景手部放大、中心构图；手持近静止、轻微晃动、无变焦 | `<Video 1>` 参考视频、`<Picture 1>` 目标美甲设计 | 人物参考图（初始状态）+ 场景参考图 | 无目标台词（审计）；面部不可见 | ready_with_assumptions |
| seg_002 | 3.5-7.0s | visual_display | 核心展示：张开手指把甲面正对镜头做紧凑特写 | 双手张开、指尖朝向镜头，目标甲面正对镜头完整展示，随后交叉叠放 | 甲面为画面重心，浅景深；镜头不动 | `<Video 1>` 参考视频、`<Picture 1>` 目标美甲设计 | 同上 | 无 | ready_with_assumptions |
| seg_003 | 7.0-12.6s | closing_or_prompt | 主体揭示与情绪收束：双手下移，面部揭示并微笑收尾 | 双手下移出画，面部与妆容完整揭示，对镜头微笑、眼神看向镜头、结尾头部轻倾 | 画面重心切到中景面部；同一机位与光线 | `<Video 1>` 参考视频 | 人物参考图 + 场景参考图 | m001 目标台词缺失（neutralize_allowed） | ready_with_assumptions |

**状态时间线**

| state_id | visible_state | active_segments | transition_segment_id |
| --- | --- | --- | --- |
| face_hidden | 双手举在面部前方，面部被手部遮挡 | seg_001, seg_002 | - |
| face_revealed | 双手下移出画，面部完全可见并微笑 | seg_003 | seg_003 |

**审计说明**：`[Shot N]` 为下游 prompt 级段落标签，来自 `temporal_segments` 的信息节拍，不是新增、拆分或重排参考镜头（`prompt_shots_from_temporal_segments`）。参考镜头始终为单一 shot `SC001_SH001`。

## 6. 文字 / logo 与叠加策略

- 目标侧无字幕、标题、结尾提示、画内可读文字或 logo；`post_overlay_plan[]` 与 `in_scene_text_logo_plan[]` 均为空。
- 默认 `post_overlay_default=true`，`render_post_overlay_in_video_model=false`，后期叠加渲染方式 `ffmpeg_or_opencv`。
- 不生成未经确认的可读文字；参考视频口播文本与项链吊坠不可读图案仅作源侧审计。

## 7. 参考帧摘要

- plan_required: `true`
- person_entity_count: `1`（ent_person_1 目标女性人物）
- scene_entity_count: `1`（ent_scene_1 目标室内梳妆空间）
- planned_frame_count: `2`
- plan_path: `07_reference_frame_plan/reference_frame_plan.json`
- triggered_rules: `person_reference_entity_present`, `scene_reference_entity_present`

## 8. 缺失项 / 假设 / 审计

- m001 `dialogue_or_on_screen_text`：`neutralize_allowed`，目标侧无台词，仅保留正向可见表情。
- m002 `actor_presence`：`missing_generate_fallback`，使用不可识别中性人物。
- m003 `scene`：`missing_generate_fallback`，继承参考场景结构并改写具体内容。
- ga_001（user_confirmed）：静态穿戴甲转写为佩戴状态。
- ga_002（fallback_policy, risk=medium）：非身份化中性人物，装扮改为暗色哥特华丽风。
- 阻塞项: 无。

## 9. 校验标记

`target_actor_not_provided_using_non_identifiable_performer`、`static_asset_requires_worn_state_assumption`、`script_profile_directory_empty_knowledge_skipped`、`prompt_shots_from_temporal_segments`、`reference_frame_plan_required`、`explicit_replacement_propagated_to_segments`
