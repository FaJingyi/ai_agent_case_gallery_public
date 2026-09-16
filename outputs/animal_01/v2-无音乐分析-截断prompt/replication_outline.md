# 复刻大纲（镜头结构复刻）

- run_id: `animal-replication-outline-dry-run`
- replication_mode: `shot_structure`
- status: `ready_with_assumptions`
- schema_version: `common_replication_outline.v2`
- generation_scope: `single_generation_task`
- 时间精度: 小数点后一位，直接截断，不四舍五入

## 1. 参考视频与目标

| 项 | 参考视频 | 目标视频 |
| --- | --- | --- |
| 时长 | 5.8s（0.0-5.8s，原始 5.875s 截断） | 5.8s（0.0-5.8s） |
| 画幅 | 横向 1344x768，24fps | 16:9 |
| 镜头数 | 1（单镜头无剪辑） | 1（单镜头连续拍摄） |
| 主体 | 三只棕色水豚 | 三只灰白毛色哈士奇 |
| 场景 | 室内商业空间（咖啡馆/办公风） | 户外草坪 |
| 前景 | 背对镜头的女性（白色上衣、白色九分裤、米色高跟鞋） | 左前景野草丛 |
| 文字 | 无可读文字/logo/水印/UI | 无文字需求 |

目标场景与主体来自用户文本与用户素材；参考视频只用于结构、时间、镜头语言、动作机制、构图关系与信息节拍。

## 2. 参考元素处理计划摘要

| element_id | 元素 | 判定 | 说明 |
| --- | --- | --- | --- |
| el_001 | 线性时间结构 | inherit | 单场景单镜头线性结构保留 |
| el_002 | 单镜头结构 | inherit | 无剪辑、结尾保持的时长比例保留 |
| el_003 | 运镜 | inherit | 缓慢推近、深焦、略低机位保留 |
| el_004 | 构图 | adapt | 主体群像居中保留；左前景元素改为野草丛承接出画机制 |
| el_005 | 动作结构 | adapt | 动作链顺序保留，动作内容改为哈士奇行为 |
| el_006 | 交互关系 | adapt | 单体攀爬至另两只背部的承托关系保留 |
| el_007 | 视觉风格 | adapt | 室内暖光改为户外自然日光；可见差异锚点已记录 |
| el_008 | 场景内容 | adapt | 室内商业空间改为户外草坪；室内陈设 discard |
| el_009 | 主体内容 | adapt | 水豚改为哈士奇；可见差异锚点已记录 |
| el_010 | 前景人物 | discard | 人物身份与衣着外观不进入目标视频 |
| el_011 | 源侧道具 | discard | 立牌、黄椅木桌、售货机等不进入目标视频 |
| el_012 | 文字/UI | discard | 参考视频无可读文字，无源侧文字进入目标视频 |
| el_013 | 音频 | discard | 音乐/BGM/音效/卡点保持 unsupported_skipped |

## 3. 时间轴

### U001 — 单镜头 0.0-5.8s

参考镜头 `shot1` / 场景 `SC001`，unit_level=`shot`。

| segment | 时间 | 时长 | 功能 | 目标画面 |
| --- | --- | --- | --- | --- |
| S001 | 0.0-0.7s | 0.7s | 建立主体与空间（opening hook） | 三只哈士奇并排站立面向镜头，开始下蹲；左前景野草丛完整可见；全景起幅，略低机位近水平，深焦 |
| S002 | 0.7-2.3s | 1.6s | 集体服从动作（reveal） | 三只全部趴伏贴近草地、前腿收拢；镜头持续缓慢推近 |
| S003 | 2.3-3.3s | 1.0s | 单体动作峰值 | 最左侧一只哈士奇跃起离地，另两只保持趴伏；动作峰值段节奏略快 |
| S004 | 3.3-4.4s | 1.1s | 转折（turn） | 三只恢复站立，随后一只攀爬至另两只背部开始叠立；左前景野草丛基本出画，构图收拢到主体群像居中 |
| S005 | 4.4-5.8s | 1.4s | 结果保持（closing） | 三层叠立造型形成并稳定保持至结束；中近景，主体群像居中占主导 |

### 分镜内容（下游 H3 视角）

下游 H3 prompt 的分镜段落由以上 5 个 temporal_segments 呈现；这 **不代表新增、拆分或重排参考镜头**，参考镜头仍为单镜头 `shot1`（audit: `prompt_shots_from_temporal_segments`）。

## 4. 动作 / 运镜 / 场景 / 文本

- 动作链：并排站立 -> 集体下蹲趴伏 -> 单体跃起 -> 恢复站立 -> 攀爬叠立 -> 三层造型稳定保持。
- 接触关系：上方哈士奇前爪接触下方两只背部，形成上一下二的三层承托。
- 运镜：略低机位近水平视角全景起幅，沿光轴缓慢推近至中近景，深焦，无切镜。
- 构图变化：左前景野草丛随推近逐步出画，构图收拢到三只哈士奇群像居中。
- 场景：户外草坪，绿色短草，背景远处树线与开阔天空，自然日光；无室内陈设。
- 文本：无台词、口播、旁白与画面文字。
- 音频：`unsupported_skipped`（music / bgm / sfx / singing / beat_alignment / audio_mood_curve）。

## 5. 使用素材

| 素材 | 角色 | 说明 |
| --- | --- | --- |
| `h3_ref_video_1`（参考视频） | `motion_camera_timing_reference` | 只参考构图/运镜/转场/动作机制/镜头顺序/时间节奏/空间关系/连续性/信息揭示结构 |
| `h3_user_dog_jpeg`（dog.jpeg） | `primary_subject_appearance_reference` | 提供单只哈士奇外观；三只数量由用户文本确定，其余两只一致性外推 |

## 6. 参考帧决策

- 触发规则：`scene_reference_entity_present`（场景实体 `ge_scene_lawn`）。
- `person_entity_count=0`：目标主体为动物，`entity_type=main_subject_appearance`，不触发 person_reference。
- `scene_entity_count=1`：户外草坪场景实体触发 1 个 scene_reference。
- `plan_required=true`，计划路径 `07_reference_frame_plan/reference_frame_plan.json`。
- 主体外观参考由用户素材 `dog.jpeg` 提供，不需生成。

## 7. 审计项

- 源侧替换内容（只进入审计与 checklist，不进入 H3 prompt）：室内商业空间、抛光木地板与白色圆线标记、灰色隔断墙、黄木框黑色沙发、售货机、红披风卡通立牌、黄色木椅木桌、夜景玻璃窗、暖色吊灯；左前景女性及其白色上衣/白色九分裤/米色高跟鞋外观。
- 缺失项：无阻塞项。`mi_001` 前景人物（neutralize_allowed）、`mi_002` 三只主体数量（missing_generate_fallback / ga_001）、`mi_003` 动作状态（missing_generate_fallback / ga_003）、`mi_004` 后期叠加文字（neutralize_allowed）。
- 生成假设：`ga_001`（其余两只外观一致性外推，medium）、`ga_002`（户外草坪场景，low）、`ga_003`（动作链按哈士奇行为改写，medium）。
- 校验标记：`target_subject_count_conflict_user_declared_three_asset_shows_one`、`profile_not_loaded:backend/profiles/脚本/叙事结构与镜头功能`、`reference_video_no_readable_text_present`。

## 8. 状态

- 准备度：`ready_with_assumptions`（`05_replication_readiness/replication_readiness_check.json`），无 `blocking_items[]`。
- 大纲状态：`ready_with_assumptions`。
- 专业知识整合：`partial`（`backend/profiles/脚本/叙事结构与镜头功能` 为空目录，未加载；视觉类 profile 已加载 6 个）。
