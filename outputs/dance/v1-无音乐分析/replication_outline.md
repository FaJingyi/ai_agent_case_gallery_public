# 复刻大纲审阅稿（replication_outline.md）

- 状态：`ready_with_assumptions`
- 生成范围：`single_generation_task`
- 时间精度：`one_decimal` / `truncate`（不四舍五入）
- timeline_unit 数量：**1**
- temporal_segment 数量：**4**
- 总时长：0.0-10.1s（参考视频 10.125s，截断到一位小数）
- 参考帧：`plan_required=true`（1 人物 + 1 场景，纯参考帧）
- H3 打包状态：本文件之后进入步骤 9；H3 视频生成在本 dry-run 中不执行

## 目标视频
- 需求：参考视频生成一条新视频，一位欧美女性在户外篮球场上跳舞
- 目标主体：一位欧美女性舞者（ENT_PERSON_1）
- 目标场景：户外篮球场（ENT_SCENE_1）
- 参考视频输入：`REF_VIDEO_1`（10.125s ≤ 15s，full_video_reference，仅参考运动结构/镜头语言/节拍/单镜节奏）

## 时间轴总览

| 单元 | 时间范围 | 类型 | 参考功能 | 目标功能 | 状态 |
| --- | --- | --- | --- | --- | --- |
| SEG001 | 0.0-0.5s | visual_display | visual_display | target_person_and_scene_reveal | `ready_with_assumptions` |
| SEG002 | 0.5-4.5s | action_or_interaction | action_or_interaction | target_dance_action_phase_1 | `ready_with_assumptions` |
| SEG003 | 4.5-8.0s | action_or_interaction | action_or_interaction | target_dance_action_phase_2 | `ready_with_assumptions` |
| SEG004 | 8.0-10.1s | closing_or_prompt | closing_or_prompt | target_pose_hold_ending | `ready_with_assumptions` |

> 参考视频为**单一连续镜头**（shot1, 0.0-10.1s, 无剪辑无转场）。上表 4 个 segment 是同一镜头内部的**信息节拍/动作阶段**，不是新增或拆分的参考镜头。downstream prompt 若渲染为 `[Shot N]`，须标注为 `prompt_shots_from_temporal_segments`。

## 分段明细

### SEG001  0.0-0.5s  （0.5s）
- 参考功能 / 目标功能：`visual_display` → `target_person_and_scene_reveal`
- 生成画面：舞者在场地中央站立起势，双臂微张，完整全身入画，场地与主体关系立刻成立。
- 生成动作/运镜：站立起势，无位移；运镜：static_locked_off，无推拉摇移、无变焦、无焦点变化（开场即完整镜头，无入场转场；本段内部无剪辑）
- 构图/景别：9:16 竖屏、全景全身取景（Full/Long Shot）、中心构图（Centered Composition）、平视机位
- 场景迁移摘要（no_target_assets_used）：户外标准篮球场，蓝绿色丙烯地坪配白色球场标线，中景可见篮球架立柱、篮板与篮筐，背景为链网围栏与树冠轮廓；白昼阴天漫射光，低饱和冷调，真实纪实质感。
- 主体/动作迁移摘要：一位欧美女性舞者，及肩浅棕/金色波浪长发，灰蓝色修身运动上衣配高腰黑色紧身运动裤、白色运动鞋，居中全身入画。
- 画面内实体文字/logo 状态：无（in_scene_text_logo_plan 为空）
- 后期叠加状态：无（post_overlay_plan 为空，H3 生成 clean plate）
- 参考帧决策：使用 `RF_PERSON_1, RF_SCENE_1`（实体：ENT_PERSON_1, ENT_SCENE_1）
- 特殊机制迁移：['SMT001']
- 缺失输入：无
- 生成假设：['GA001', 'GA002']
- 状态：`ready_with_assumptions`

### SEG002  0.5-4.5s  （4.0s）
- 参考功能 / 目标功能：`action_or_interaction` → `target_dance_action_phase_1`
- 生成画面：舞者以交替抬腿/踢腿配合手臂张开与屈肘握拳的往复动作进入连续律动。
- 生成动作/运镜：交替抬腿/踢腿 + 手臂张合往复；运镜：static_locked_off（段内无剪辑，动作连续）
- 构图/景别：9:16 竖屏全景全身、中心构图、平视固定机位
- 场景迁移摘要（no_target_assets_used）：户外标准篮球场，蓝绿色丙烯地坪配白色球场标线，中景可见篮球架立柱、篮板与篮筐，背景为链网围栏与树冠轮廓；白昼阴天漫射光，低饱和冷调，真实纪实质感。
- 主体/动作迁移摘要：一位欧美女性舞者，及肩浅棕/金色波浪长发，灰蓝色修身运动上衣配高腰黑色紧身运动裤、白色运动鞋，居中全身入画。
- 画面内实体文字/logo 状态：无（in_scene_text_logo_plan 为空）
- 后期叠加状态：无（post_overlay_plan 为空，H3 生成 clean plate）
- 参考帧决策：使用 `RF_PERSON_1, RF_SCENE_1`（实体：ENT_PERSON_1, ENT_SCENE_1）
- 特殊机制迁移：['SMT002']
- 缺失输入：无
- 生成假设：['GA001', 'GA002']
- 状态：`ready_with_assumptions`

### SEG003  4.5-8.0s  （3.5s）
- 参考功能 / 目标功能：`action_or_interaction` → `target_dance_action_phase_2`
- 生成画面：舞者加入双腿交叉步与点地动作，配合手臂摆动与躯干摇摆，动作幅度与连续性提升。
- 生成动作/运镜：交叉步与点地，躯干摇摆；运镜：static_locked_off（段内无剪辑）
- 构图/景别：9:16 竖屏全景全身、中心构图、平视固定机位
- 场景迁移摘要（no_target_assets_used）：户外标准篮球场，蓝绿色丙烯地坪配白色球场标线，中景可见篮球架立柱、篮板与篮筐，背景为链网围栏与树冠轮廓；白昼阴天漫射光，低饱和冷调，真实纪实质感。
- 主体/动作迁移摘要：一位欧美女性舞者，及肩浅棕/金色波浪长发，灰蓝色修身运动上衣配高腰黑色紧身运动裤、白色运动鞋，居中全身入画。
- 画面内实体文字/logo 状态：无（in_scene_text_logo_plan 为空）
- 后期叠加状态：无（post_overlay_plan 为空，H3 生成 clean plate）
- 参考帧决策：使用 `RF_PERSON_1, RF_SCENE_1`（实体：ENT_PERSON_1, ENT_SCENE_1）
- 特殊机制迁移：['SMT003']
- 缺失输入：无
- 生成假设：['GA001', 'GA002']
- 状态：`ready_with_assumptions`

### SEG004  8.0-10.1s  （2.1s）
- 参考功能 / 目标功能：`closing_or_prompt` → `target_pose_hold_ending`
- 生成画面：舞者以单腿抬起、双臂屈肘的姿态定格式收尾，画面短暂保持后结束。
- 生成动作/运镜：动作收束为定格式姿态并保持；运镜：static_locked_off（结尾无转场，画面保持到结束）
- 构图/景别：9:16 竖屏全景全身、中心构图、平视固定机位
- 场景迁移摘要（no_target_assets_used）：户外标准篮球场，蓝绿色丙烯地坪配白色球场标线，中景可见篮球架立柱、篮板与篮筐，背景为链网围栏与树冠轮廓；白昼阴天漫射光，低饱和冷调，真实纪实质感。
- 主体/动作迁移摘要：一位欧美女性舞者，及肩浅棕/金色波浪长发，灰蓝色修身运动上衣配高腰黑色紧身运动裤、白色运动鞋，居中全身入画。
- 画面内实体文字/logo 状态：无（in_scene_text_logo_plan 为空）
- 后期叠加状态：无（post_overlay_plan 为空，H3 生成 clean plate）
- 参考帧决策：使用 `RF_PERSON_1, RF_SCENE_1`（实体：ENT_PERSON_1, ENT_SCENE_1）
- 特殊机制迁移：['SMT004']
- 缺失输入：无
- 生成假设：['GA001', 'GA002']
- 状态：`ready_with_assumptions`

## 全局素材（global_appearance）

| 实体 | 类型 | 用途 | 引用分镜 |
| --- | --- | --- | --- |
| ENT_PERSON_1 目标女性舞者 | `person_appearance` | 欧美女性，年轻成年（约 20-30 岁观感），运动型纤细体态；浅肤色，自然淡妆，五官清晰 | SEG001, SEG002, SEG003, SEG004 |
| ENT_SUBJECT_1 居中全身主体 | `main_subject_appearance` | 人物从头到脚完整入画（Full/Long Shot），垂直占据画面高度约七成；主体位于画面水平与垂直中心，左右视觉重量均衡 | SEG001, SEG002, SEG003, SEG004 |
| ENT_SCENE_1 户外篮球场 | `scene_appearance` | 标准户外篮球场，无屋顶、空旷开阔；蓝绿色（teal-green）丙烯球场地坪，表面细腻、略有使用痕迹 | SEG001, SEG002, SEG003, SEG004 |
| ENT_PROP_1 篮球架与球场标线 | `key_prop_appearance` | 篮球架：金属立柱、白色矩形篮板、橙色/金属色篮筐与白色球网，位于中景，不进前景；球场标线：白色平直直线段，绘于蓝绿色地坪上，为画面下部提供引导线 | SEG001, SEG002, SEG003, SEG004 |
| ENT_ATMOS_1 阴天漫射纪实氛围 | `style_atmosphere` | 阴天漫射自然光，阴影柔和、无明显方向性主光；低饱和中性偏冷调，低对比 | SEG001, SEG002, SEG003, SEG004 |

## 记忆点迁移

| memory_id | 类型 | 保留机制 | 目标绑定 | 状态 |
| --- | --- | --- | --- | --- |
| vm_001 | visual | 动作链条的时间顺序与节拍；抬腿-支撑的重心关系与接触点 | target_video, UNIT001, SEG001, SEG002, SEG003, SEG004 | `ready_with_assumptions` |
| vm_002 | visual | 阴天漫射柔光与浅阴影；低饱和中性色调与低对比 | target_video, UNIT001, SEG001, SEG002, SEG003, SEG004 | `ready_with_assumptions` |
| sm_001 | script | 第一秒直接呈现主体完整入画与环境关系；无前置文字/标题的冷开场 | UNIT001, SEG001 | `ready_with_assumptions` |
| sm_002 | script | 单镜头连续动作展示结构；阶段化动作推进与结尾定格式姿态停留 | UNIT001, SEG002, SEG003, SEG004 | `ready_with_assumptions` |
| audio | audio | 不迁移（unsupported_skipped：音乐/BGM/音效/疑似唱歌/声音情绪/卡点节奏） | - | `unsupported_skipped` |

## 参考元素处理计划

| element_id | 类型 | 决策 | 观测元素 |
| --- | --- | --- | --- |
| RET001 | `time_structure` | `inherit` | 单一连续镜头，总时长 0.0-10.1s，无剪辑、无转场。 |
| RET002 | `shot_structure` | `inherit` | 单一 shot1，镜头顺序为一次性完整展示，无切镜。 |
| RET003 | `camera` | `inherit` | 单一固定机位（locked-off），平视视角，无推拉摇移、无变焦、无焦点变化、无手持晃动。 |
| RET004 | `composition` | `inherit` | 9:16 竖屏、全景全身取景（Full/Long Shot）、中心构图、主体上下保留四肢活动空间。 |
| RET005 | `action_structure` | `inherit` | 连续节拍舞蹈动作链：起势 → 交替抬腿/踢腿与手臂张合 → 交叉步与点地 → 单腿抬起的定格式收尾。 |
| RET006 | `interaction_relation` | `inherit` | 支撑脚脚掌与地面持续接触，形成抬腿/落脚的重心支撑关系。 |
| RET007 | `visual_style` | `inherit` | 阴天漫射自然光、柔和浅阴影、低饱和中性调、低对比、真实材质质感、日常纪实感。 |
| RET008 | `scene_content` | `adapt` | 户外水泥/混凝土地面场地，米色长墙 + 竖向金属立柱 + 墙顶栏杆 + 高杆体育场灯 + 左右红色长椅，阴天天空。 |
| RET009 | `person_or_body` | `adapt` | 年轻男性舞者，米白连帽卫衣（兜帽戴起、白色抽绳）、棕色运动短裤、白袜白鞋，居中全身入画。 |
| RET010 | `prop` | `adapt` | 白色场地划线（灰色混凝土地面上的白线）与左右两侧红色长椅。 |
| RET011 | `other` | `inherit` | micro_action 机制：手部握拳与手臂摆动、交替抬腿/踢腿、腿部交叉步。 |
| RET012 | `unsupported_audio` | `discard` | ASR 检测到带节拍的英文歌词式短句，判定为疑似音乐人声；参考视频含音轨。 |

## 缺失项与假设

- `MI001` actor_identity：`missing_generate_fallback` → `generate_with_confirmed_assumption`
- `MI002` scene：`ready_with_text_instruction` → `use_text_instruction`
- `MI003` post_overlay_text：`ready_with_text_instruction` → `omit_or_neutralize`
- `GA001` actor_identity：目标主体为一位欧美女性舞者；外观由假设生成并带可见区分锚点。 可见区分：女性取代男性舞者；及肩浅棕/金色波浪长发且不戴兜帽；灰蓝运动上衣+黑色紧身运动裤+白鞋取代米白连帽卫衣+棕色短裤
- `GA002` scene：目标场景为户外篮球场；内容由假设生成并带可见区分锚点。 可见区分：蓝绿色丙烯地坪+白色标线取代灰色混凝土地面；可见篮球架取代无篮球架的广场；链网围栏+树冠取代米色长墙+红色长椅+高杆体育场灯
- `GA003` props：补充篮球场普通道具（篮球架、球场标线、场边护栏/围网），不含品牌或声明性内容。 可见区分：-

## 禁止项 / 负向约束策略

- 策略：`prompt_weight=low`、默认 `prompt_visibility=audit_only`、最多 2 句 compact guardrail。
- 全局禁止项（audit）：不得迁移参考男性舞者身份/服装、米色长墙/高杆灯/红椅/水泥地、未确认可读文字/品牌/logo/水印/UI、音乐与唱歌类声音结论、参考中不存在的切镜/转场/特殊呈现机制。

## 参考帧摘要

- `frame_requirement_level=required_person_scene_anchors`，`plan_required=True`，人物实体 1 个、场景实体 1 个，计划参考帧 2 张。
- `plan_path=07_reference_frame_plan/reference_frame_plan.json`，`ready_frame_ids=[]`，`summary_status=ready`。
- 触发规则：person_reference_entity_present, scene_reference_entity_present

## 步骤衔接

- 步骤 7：按 `global_appearance_dedup_pass.global_appearance` 规划 `RF_PERSON_1`（人物）与 `RF_SCENE_1`（场景）两张纯参考帧。
- 步骤 8：调用 `tool-sensenova-image-generation-skill` 生成；通过质检与可用输出的帧追加到 H3 白名单。
- 步骤 9：输出 `09_h3_package/h3_packager_input.md`（参考视频 / 音乐 / 全局素材 / 分镜内容）。
- 步骤 10：本 dry-run 只产出 H3 request/package，不提交、不生成视频。
