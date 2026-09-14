# 复刻大纲人工审阅稿 (`replication_outline.md`)

- `schema_version`: `common_replication_outline.v2`
- `status`: `ready_with_assumptions`
- `replication_mode`: `shot_structure`
- `generation_scope`: `single_generation_task`
- `time_precision_policy`: `precision=one_decimal`, `method=truncate`
- 参考视频: `test_data/nail-6/nail-6.mp4` (12.6s, 1080x1920, 30fps, 单一连续镜头)
- 目标视频: 自拍近景单镜头，人物双手完成“交叉-张开-多角度”动作链展示**目标美甲图案**，随后放下双手揭示面部；暗调室内低调光，造型与暗黑美甲风格一致。
- 结构口径: 1 个 `timeline_unit` (`VS001`) / 4 个 `temporal_segments`（`VS001_SEG1`-`VS001_SEG4`）。4 个 segment 是同一参考镜头内部的信息/动作节拍，**不是**参考级多镜头；若 downstream prompt 出现 `[Shot N]`，属于 `prompt_shots_from_temporal_segments`。

## 复刻两层 pass 结论

- `reference_element_treatment_plan[]`: 14 项 (`RET_001`-`RET_014`)，其中 `inherit` 6 项（时间结构、shot 结构、构图、运镜、动作链、无转场）、`adapt` 7 项（人物、美甲图案、饰品、场景、光线、脚本节奏）、`discard` 1 项（音乐/音效类，`unsupported_skipped`）。
- `explicit_replacement_coverage`: 参考美甲图案 → `ASSET_001` 目标美甲图案，覆盖 `VS001` 全部 4 个 segment，`status=passed`、`missing_segments=[]`。
- `reference_mapping_and_self_check_pass`: `memory_point_check` 与 `dynamic_detail_check` 均 `passed`；`replacement_binding_check` `passed`。
- `global_appearance_dedup_pass.global_appearance`: 5 个实体 —— `ENT_SUBJECT_NAIL_001`(目标美甲图案)、`ENT_PERSON_001`(非特定身份表演者)、`ENT_SCENE_001`(暗调室内场景)、`ENT_PROP_001`(中性金属与珍珠饰品)、`ENT_ATMOS_001`(暗黑低调氛围)。
- `memory_transfer_plan`: 视觉 2 条 (`vm_001` 手部动作链 / `vm_002` 遮挡揭示)、脚本 2 条 (`sm_001` 信息释放顺序 / `sm_002` 结尾互动收束)、音频 0 条。
- `scene_transfer[]`: `ST_001`，`preserve_scene_style` 保留自拍视距/三层空间/写实质感，`adapt_scene_content` 把车内明亮绿背景迁移为暗调室内（空间类型、主色调、背景结构均不同）。

## 全局素材与参考帧摘要

| 实体 | 类型 | 用途 | 参考帧候选 |
| --- | --- | --- | --- |
| `ENT_SUBJECT_NAIL_001` | `main_subject_appearance` | 目标美甲图案（`ASSET_001` 显式替换） | 否（用用户素材） |
| `ENT_PERSON_001` | `person_appearance` | 非特定身份表演者（造型贴合暗黑美甲） | `RF_PERSON_001` |
| `ENT_SCENE_001` | `scene_appearance` | 暗调室内场景 | `RF_SCENE_001` |
| `ENT_PROP_001` | `key_prop_appearance` | 中性金属/珍珠饰品 | 否 |
| `ENT_ATMOS_001` | `style_atmosphere` | 暗黑低调氛围 | 否 |

- `reference_frame_summary`: `plan_required=true`，`person_entity_count=1`，`scene_entity_count=1`，`planned_frame_count=2`，`plan_path=07_reference_frame_plan/reference_frame_plan.json`，`summary_status=ready`。

## 时间轴与分镜

### `VS001_SEG1` — 0.0-3.5s

- 参考功能 / 目标功能: 开场细节展示/注意力钩子 / 以目标美甲与手部动作开场
- 生成画面: 非特定身份表演者的双手举至面庞前方，十指交叉扣紧，佩戴 `ASSET_001` 目标美甲图案（黑/深褐/灰褐底色、高光泽凝胶、立体眼球与珍珠/银珠/金饰），前景部分遮挡面部。
- 生成动作/运镜: 双手由下方/画外举入画面中央 → 十指交叉扣紧 → 小幅晃动调整角度；自拍近景中心构图、紧凑特写；手持轻微晃动，无位移。
- 场景迁移摘要: 暗调室内（深色绒面/木质背景、单一暖色实用光源、低调光），与参考车内绿树场景明显不同。
- 台词/口播/旁白/画面文字: 本段无台词、无画面文字。
- 画面内实体文字/logo: 无（`in_scene_text_logo_plan=[]`）。
- 后期叠加: 无（`post_overlay_plan=[]`）。
- 使用素材: `ASSET_REF_VIDEO`（参考动作/运镜/节奏）、`ASSET_001`（目标美甲图案）、`RF_PERSON_001`、`RF_SCENE_001`。
- 参考帧决策: `used_reference_frame_ids=[RF_PERSON_001, RF_SCENE_001]`，`usage_role=person_reference+scene_reference`。
- 禁止项/缺失项: 禁止残留参考视频蓝白渐变美甲图案（`asset_fidelity_risk`/`compact_guardrail`）；本段无缺失项。
- 特殊机制: `SM_001`（`special_composition`，前景双手遮挡面部），prompt_sentence 见 `segment_generation_notes`。
- 状态: `ready_with_assumptions`

### `VS001_SEG2` — 3.5-7.5s

- 参考功能 / 目标功能: 产品/图案细节展示 / 清晰展示目标美甲图案细节
- 生成画面: 手指松开、张开交错，占据画面中心，缓慢旋转开合展示目标美甲正反面；图案为黑灰底 + 立体眼球 + 珍珠/银珠/金饰。
- 生成动作/运镜: 手指松开 → 张开交错 → 缓慢旋转开合展示正反面；自拍近景紧凑特写；手持轻微晃动。
- 场景迁移摘要: 同 `VS001_SEG1` 暗调室内，场景与光线保持不变。
- 台词/口播/旁白/画面文字: 无。
- 画面内实体文字/logo: 无。
- 后期叠加: 无。
- 使用素材: `ASSET_REF_VIDEO`、`ASSET_001`、`RF_PERSON_001`、`RF_SCENE_001`。
- 参考帧决策: `used_reference_frame_ids=[RF_PERSON_001, RF_SCENE_001]`。
- 禁止项/缺失项: 图案必须匹配素材（不得出现参考蓝白渐变，`compact_guardrail`）；本段无缺失项。
- 状态: `ready_with_assumptions`

### `VS001_SEG3` — 7.5-8.0s

- 参考功能 / 目标功能: 动作转场/注意力转移 / 双手放下，为面部揭示做准备
- 生成画面: 双手快速下移出画面下方，前景遮挡消失，面部逐渐居中。
- 生成动作/运镜: 双手快速下移出画；近景；镜头保持轻微手持晃动；单一连续镜头内的揭示过渡（非剪辑转场）。
- 场景迁移摘要: 同暗调室内；画面结构由“手部主体”切换为“面部主体”。
- 台词/口播/旁白/画面文字: 无。
- 画面内实体文字/logo: 无。
- 后期叠加: 无。
- 使用素材: `ASSET_REF_VIDEO`、`ASSET_001`（延续可见/回置）、`RF_PERSON_001`、`RF_SCENE_001`。
- 参考帧决策: `used_reference_frame_ids=[RF_PERSON_001, RF_SCENE_001]`。
- 禁止项/缺失项: 双手下移需干净利落、不遮挡面部揭示（`composition_conflict`/`audit_only`，不进 prompt）；本段无缺失项。
- 状态: `ready_with_assumptions`

### `VS001_SEG4` — 8.0-12.6s

- 参考功能 / 目标功能: 主体揭示与互动收束 / 揭示与目标风格一致的人物形象并收束
- 生成画面: 非特定身份表演者面部揭示，造型与目标暗黑美甲风格一致（深色长发、冷调妆容、深色系服装、金属耳饰与细项链），微笑并嘴唇微动，面向镜头收束。
- 生成动作/运镜: 面部揭示 → 微笑 → 嘴唇微动 → 头部轻微晃动；中近景/近景中心构图，背景简化，手持轻微晃动。
- 场景迁移摘要: 同暗调室内，人物与场景保持连续；信息由细节转为形象。
- 台词/口播/旁白/画面文字: 参考台词 `Do you think I'm strange?` 的具体文案**不迁移**；保留结尾面向镜头互动/提问的结构位置，目标文案缺失时仅保留口型与互动（`target_dialogue_status=missing_optional_input`）。
- 画面内实体文字/logo: 无。
- 后期叠加: 无。
- 使用素材: `ASSET_REF_VIDEO`、`ASSET_001`（延续绑定）、`RF_PERSON_001`、`RF_SCENE_001`。
- 参考帧决策: `used_reference_frame_ids=[RF_PERSON_001, RF_SCENE_001]`。
- 禁止项/缺失项: 不得复现参考视频人物身份（`source_identity_leak`/`compact_guardrail`）；不生成未确认可读文字（`audit_only`）；`missing_inputs` 关联 `MI_001`(actor_identity)/`MI_002`(scene)，均为 `generate_with_confirmed_assumption`，不阻塞。
- 状态: `ready_with_assumptions`

## 文字 / logo / 音频策略

- `text_logo_policy`: `post_overlay_default=true`，`render_post_overlay_in_video_model=false`，`post_overlay_render_method=ffmpeg_or_opencv`，`do_not_generate_unconfirmed_readable_text=true`。
- 参考视频无画面内实体文字/logo、无后期叠加项；目标侧未提供文字/logo 素材，记录为缺失/可中性化，不阻塞 H3 clean plate 生成。
- `script_copy`: 保留脚本信息节奏与结尾互动结构，不迁移原文案。
- `unsupported_audio`: 音乐/BGM/音效/疑似唱歌/声音情绪/卡点节奏固定 `unsupported_skipped`，仅保留状态占位。

## 缺失项与假设

- `missing_inputs[]`: `MI_001` `actor_identity`、`MI_002` `scene`，均 `missing_generate_fallback` + `generate_with_confirmed_assumption`，不阻塞 H3 打包。
- `generation_assumptions[]`: `GA_001` 平铺美甲→佩戴展示（用户确认）、`GA_002` 非特定身份表演者造型贴合暗黑美甲（用户确认）、`GA_003` 场景迁移暗调室内（fallback policy，proposed）。
- `readiness_check`: `overall_status=ready_with_assumptions`，`blocking_item_ids=[]`。

## packaging 状态

- `packaging_notes`: `single_continuous_shot`（4 个 temporal_segments 为单镜头内部节拍）；`prompt_shots_from_temporal_segments`（downstream `[Shot N]` 为 prompt-level shots）；参考无画面文字、无后期叠加。
- `validation_flags`: `explicit_replacement_applied_across_all_segments`、`scene_adapted_with_visible_difference`、`person_identity_neutralized`。
- `H3 打包状态`: 待步骤 9 生成 `09_h3_package/h3_packager_input.md` 及可提交 H3 request。
- `H3 视频生成状态`: dry-run，未提交（不上传、不运行 H3 视频生成）。
