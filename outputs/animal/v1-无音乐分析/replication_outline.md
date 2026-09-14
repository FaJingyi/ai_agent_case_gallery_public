# 复刻大纲审阅稿

- schema_version: `common_replication_outline.v2`
- replication_mode: `shot_structure`
- status: `ready_with_assumptions`
- generation_scope: `single_generation_task`
- 时间精度: `precision=one_decimal`, `method=truncate`（5.875 -> 5.8）
- 参考视频: `test_data/animal/2_2_case4-H3-original.mp4`（5.8s，1344x768，24fps，单镜头）
- 目标视频: 三只哈士奇在户外草坪上表演（时长 5.8s，16:9）

## 1. 目标视频概述

单一连续横屏镜头：略高于主体的固定机位以宽景建立户外草坪与三只并排哈士奇，主体居中、前景草叶作为底部占位、背景浅景深虚化；三只同步下压趴伏贴地后撑起起身，朝镜头方向缓慢走近；镜头在 2.5-4.0s 连续推近，画面由宽景收紧为哈士奇近景；两只并排站定作底座，第三只以前爪搭上其背部攀爬，四足站稳形成下二上一叠站造型，并在结尾稳定保持约 2 秒。

## 2. 素材与事实来源

- 目标主体外观来源: `04_target_asset_analysis/target_asset_analysis.json#asset_level_analysis[ASSET_DOG_001]`（dog.jpeg：灰白黑毛色、异瞳、竖立三角耳、黑鼻、粉舌、蓬松卷尾）
- 目标场景来源: 用户文本 `三只哈士奇在户外草坪上表演`（GA002）
- 参考视频来源: `01_reference_video_analysis/reference_video_analysis.json#video_prompt_source`
- H3 素材白名单: `03_asset_inventory/h3_input_asset_inventory.json.eligible_h3_input_assets[]`

## 3. 参考元素处理计划摘要

| element_id | 类型 | 参考元素 | decision |
| --- | --- | --- | --- |
| RET001 | time_structure | 单一连续镜头 0.0-5.875s，无切镜 | inherit |
| RET002 | shot_structure | 建立镜头收紧为主体近景、主体居中、前景底部占位 | inherit |
| RET003 | camera | 2.5-4.0s 连续推近（snap-zoom/push-in），无切镜 | inherit |
| RET004 | action_structure | 0.5-2.5s 趴伏-起身动作链 | inherit |
| RET005 | interaction_relation | 3.5-5.875s 攀爬叠站与承重保持 | inherit |
| RET006 | action_structure | 站立→趴伏→起身→走动→攀爬→保持 动作顺序 | inherit |
| RET007 | composition | 16:9 宽画幅、主体居中、略高平视、前中后景层次 | inherit |
| RET008 | visual_style | 暖色吊灯、木色/暖黄基调、木地板反光 | adapt |
| RET009 | scene_content | 室内休闲空间与全部室内陈设 | adapt |
| RET010 | subject_content | 三只棕色水豚（圆钝体型、短耳、棕色短毛） | adapt |
| RET011 | person_or_body | 左侧白衣女性旁观者 | discard |
| RET012 | text_or_ui | 售货机面板图案文字、墙面白色线条图形（不可读） | discard |
| RET013 | incidental_detail | 天花板管道、灰色扶手椅、小木桌 | discard |
| RET014 | transition | not_applicable_single_shot（无切镜、无转场） | inherit |
| RET015 | unsupported_audio | ASR 无语音、音频分析 skipped | discard |

显式替换绑定: RET009（室内休闲空间 → 户外草坪）、RET010（三只棕色水豚 → 三只哈士奇，target_asset=`ASSET_DOG_001`），影响 `VS001_SEG001`-`VS001_SEG004`。

## 4. 全局外观元素库（第二层 pass）

| entity_id | entity_type | entity_name | merge_status |
| --- | --- | --- | --- |
| GE001 | main_subject_appearance | 三只哈士奇（同一外观） | merged_same_appearance_three_instances |
| GE002 | scene_appearance | 户外草坪（自然日光，开阔草地） | single_entity |
| GE003 | style_atmosphere | 户外日光写实明亮氛围 | single_entity |

- GE001 visible_difference_anchor: 以灰白黑毛色、竖立三角耳、异瞳的犬类替换参考视频的水豚外观。
- GE002 visible_difference_anchor: 户外空间类型、草绿主色、自然日光替换室内空间、木色暖黄与室内吊灯。
- person_appearance 无实体（目标视频无人物）。

## 5. 记忆点迁移计划

| memory_id | source_type | 保留机制 | 目标绑定 |
| --- | --- | --- | --- |
| vm_001 | visual | 单一连续镜头内连续推近、主体保持视觉中心 | VS001_SEG003, VS001_SEG004 |
| vm_002 | visual | 下压贴地再撑起的完整动作阶段与地面接触点 | VS001_SEG002 |
| vm_003 | visual | 下二上一承重叠站关系、前爪接触点、成型保持 | VS001_SEG004 |
| sm_001 | script | 连续演示链的动作先后顺序与片尾保持展示 | TARGET_VIDEO_001, VS001 |
| sm_002 | script | 铺垫（环境+主体并排）到 payoff（叠站造型）的信息释放顺序 | VS001_SEG001, VS001_SEG004 |

## 6. 时间轴

| 时间范围 | unit | segment | 参考功能 | 目标功能 |
| --- | --- | --- | --- | --- |
| 0.0-0.5s | VS001 | VS001_SEG001 | visual_display | 建立镜头：交代户外草坪与三只哈士奇并排站立（B001） |
| 0.5-2.5s | VS001 | VS001_SEG002 | action_or_interaction | 动作蓄势：同步下压趴伏贴地后撑起起身（B002） |
| 2.5-3.5s | VS001 | VS001_SEG003 | action_or_interaction | 动作执行：朝镜头走近，镜头同步连续推近（B003） |
| 3.5-5.8s | VS001 | VS001_SEG004 | closing | 结果造型：第三只攀爬叠站成型并稳定保持（B004） |

`h3_prompt_shot` 说明: reference-level shot 只有 1 个（VS001）；若 downstream prompt 使用 `[Shot N]` 标签，其数量来自 4 个 temporal segments（`prompt_shots_from_temporal_segments`），不代表新增、拆分或重排参考镜头。

## 7. 分镜级生成信息

### VS001_SEG001 0.0-0.5s

- 生成画面: 户外草坪宽景，三只同外观哈士奇并排站立，主体居中，前景草叶作为底部占位。
- 生成动作/运镜: 静止站立；机位基本固定，本段无推近。
- 场景迁移: 室内休闲空间 → 户外草坪（前景草地、中景主体、远景简化虚化）。
- 台词/画面文字: 无。
- 画面内文字/logo: 无。
- 后期叠加: 无。
- 使用素材: `REF_VIDEO_001`（机制）、`ASSET_DOG_001`（主体外观）。
- 参考帧决策: GE002 → `GEN_SCENE_001`（scene_reference）。
- 缺失项/假设: GA001、GA002。

### VS001_SEG002 0.5-2.5s

- 生成画面: 三只哈士奇同步下压身体、四肢收折贴地，短暂停留后撑起恢复站立。
- 生成动作/运镜: 动作链 下压 → 贴地 → 停顿 → 撑起；接触点为草坪地面；机位固定。
- 场景迁移: 地面接触关系保留，接触面改为草坪。
- 台词/画面文字: 无。
- 画面内文字/logo: 无。后期叠加: 无。
- 使用素材: `REF_VIDEO_001`、`ASSET_DOG_001`。
- 参考帧决策: GE002 → `GEN_SCENE_001`（scene_reference）。
- 特殊机制: SM002 趴伏-起身动作链（micro_action）。
- 缺失项/假设: GA003。

### VS001_SEG003 2.5-3.5s

- 生成画面: 三只哈士奇朝镜头方向走近，主体尺度增大，镜头开始连续推近。
- 生成动作/运镜: 由后景向近处缓慢走动；连续推近幅度中等、速度缓慢到中等；无切镜。
- 场景迁移: 背景随推近减少，空间仍为户外草坪。
- 台词/画面文字: 无。
- 画面内文字/logo: 无。后期叠加: 无。
- 使用素材: `REF_VIDEO_001`、`ASSET_DOG_001`。
- 参考帧决策: GE002 → `GEN_SCENE_001`（scene_reference）。
- 特殊机制: SM001 连续推近（special_camera_or_focus）。
- 缺失项/假设: GA003。

### VS001_SEG004 3.5-5.8s

- 生成画面: 两只哈士奇并排站定作底座，第三只以前爪搭上其背部攀爬上升，四足站稳形成下二上一叠站造型并稳定保持至片尾。
- 生成动作/运镜: 攀爬约 0.5s，前爪接触点位于下方两只背部；推近在 3.5-4.0s 收尾后机位稳定；结尾保持约 1.8s。
- 场景迁移: 推近完成后背景进一步简化虚化，场景为户外草坪。
- 台词/画面文字: 无。
- 画面内文字/logo: 无。后期叠加: 无。
- 使用素材: `REF_VIDEO_001`、`ASSET_DOG_001`。
- 参考帧决策: GE002 → `GEN_SCENE_001`（scene_reference）。
- 特殊机制: SM001C 推近收尾、SM003 攀爬叠站动作链、SM004 叠站造型保持。
- 禁止项: 叠站造型不得出现失稳跌落或受伤表现。
- 缺失项/假设: GA003。

## 8. 场景迁移

- preserve_scene_style: 光照模式、空间深度层次、构图关系、机位角度关系、背景密度、写实明亮艺术方向、稳定拍摄质感、轻松明亮氛围。
- adapt_scene_content: 以用户文本指定的户外草坪（GA002）替换室内休闲空间；前景草叶、中景主体、远景简化虚化；自然日光、草绿主色、中低反差。
- 丢弃: 抛光木地板、白色圆圈地面标线、盆栽绿植、自动售货机、黄色木椅木桌、深色落地窗、白色卡通立牌、吊灯、灰色布艺扶手椅、天花板管道。
- dog.jpeg 背景中的体育场看台、黄色座椅、绿色设施与栏杆线条为素材偶然背景，不作为目标场景参考。

## 9. 文字/logo 与后期叠加

- `post_overlay_plan[]`: 空。H3 只生成 clean plate，无需后期文字层。
- `in_scene_text_logo_plan[]`: 空。无已确认的画面内实体文字/logo。
- 不生成任何未确认的可读文字、品牌、logo、水印或角标。

## 10. 负向约束策略

- `prompt_weight=low`，`default_prompt_visibility=audit_only`，最多 1-2 句 compact guardrail。
- compact guardrails: 哈士奇外观与参考图一致；生成 clean plate 且无可读文字/logo/水印/角标。
- audit_only 项: 不出现参考视频女性身份、不生成未确认文字、叠站造型稳定承重。

## 11. 缺失项与生成假设

| id | slot | 状态 | 解析策略 |
| --- | --- | --- | --- |
| MI001 | second_and_third_subject_assets | missing_generate_fallback | generate_with_confirmed_assumption（GA001） |
| MI002 | subject_motion_state_assets | missing_generate_fallback | generate_with_confirmed_assumption（GA003） |
| GA001 | target_subject_instances | proposed | 以 dog.jpeg 外观补全为三只 |
| GA002 | target_scene_content | proposed | 户外草坪（用户文本指定） |
| GA003 | target_motion_states | proposed | AI 补齐趴伏/起身/走位/叠站动作状态 |

blocking_items: 无。

## 12. 参考帧决策

- `frame_requirement_level=required_person_scene_anchors`，`plan_required=true`。
- person_entity_count=0（主体为动物，不产生 person_reference）。
- scene_entity_count=1（GE002 户外草坪 → `GEN_SCENE_001`，scene_reference）。
- plan_path: `07_reference_frame_plan/reference_frame_plan.json`。

## 13. 专业知识上下文

- 已加载 profile: `VK-COMP-003`（构图）、`VK-CAM-001`（运镜）、`VK-ACT-001`（动作连续性）、`VK-EDIT-003`（剪辑节奏）、`VK-LIGHT-002`（光线色彩）。
- 采用术语: 建立镜头、中近景、推近（Dolly In）、时间顺序描述、主体揭示、揭示后保持、冷色温/自然日光、统一调色。
- `backend/profiles/脚本/叙事结构与镜头功能/` 为空目录，脚本侧专业术语跳过（validation flag: `script_narrative_profiles_directory_empty_script_terms_skipped`）。

## 14. 状态与交付

- H3 打包状态: 待执行（步骤 9 生成 `09_h3_package/h3_packager_input.md`）。
- H3 视频生成状态: `not_run`（dry-run 边界，不提交 H3 视频生成）。
- validation_flags: `target_subject_count_conflict_one_asset_vs_three_requested`、`static_asset_used_for_motion_requires_generation_assumption`、`prompt_shots_from_temporal_segments`、`scene_appearance_from_user_text_requires_generated_scene_reference`、`source_incidental_background_not_migrated`。
