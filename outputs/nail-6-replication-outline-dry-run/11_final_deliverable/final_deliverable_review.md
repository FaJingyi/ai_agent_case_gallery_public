# 最终交付审阅稿

- skill: `common-video-replication-outline`
- `replication_mode`: `shot_structure`
- `run_type`: `dry_run`（工作流执行到 H3 request/package 为止，**不提交、不运行 H3 视频生成**）
- `status`: `completed`
- 主产物: `06_replication_outline/replication_outline.json`（`schema_version=common_replication_outline.v2`，`status=ready_with_assumptions`）
- 计数: `timeline_unit_count=1`、`temporal_segment_count=4`、`h3_prompt_shot_count=4`

> 说明: 4 个 Beat/分镜句来自单一参考镜头的内部节拍（`prompt_shots_from_temporal_segments`），不是参考级多镜头；参考视频为无剪辑单一连续镜头。

## 时间轴

### 分镜1 / Beat 1 — 0.0-3.5s
- 参考功能 / 目标功能: 开场细节展示/注意力钩子 / 以目标美甲与手部动作开场
- 场景迁移: 车内明亮绿背景 → 暗调室内低调光（空间类型/主色调/背景结构均不同）
- 主体/动作迁移: 非特定身份表演者举双手至面庞前方、十指交叉扣紧，展示 `ASSET_001` 目标美甲与中性金属/珍珠戒指；前景部分遮挡面部
- 生成画面/运镜: 自拍近景中心构图、紧凑特写；手持轻微晃动、无位移
- 台词/口播/旁白/画面文字: 无
- 画面内实体文字/logo 状态: 无
- 后期叠加状态: 无
- 使用素材: `<参考视频>`, `<人物1>`=RF_PERSON_001, `<场景1>`=RF_SCENE_001, `<全局素材1>`=ASSET_001
- 参考帧决策: 使用 RF_PERSON_001 + RF_SCENE_001
- 禁止项/缺失项: 禁止残留参考蓝白渐变美甲图案；无缺失项
- 状态: `ready_with_assumptions`

### 分镜2 / Beat 2 — 3.5-7.5s
- 参考功能 / 目标功能: 产品/图案细节展示 / 清晰展示目标美甲图案细节
- 场景迁移: 同暗调室内，场景与光线不变
- 主体/动作迁移: 手指松开、张开交错、缓慢旋转开合，多角度展示目标美甲正反面；保留黑灰底+立体眼球+珍珠/银珠/金饰
- 生成画面/运镜: 自拍近景紧凑特写；手持轻微晃动
- 台词/口播/旁白/画面文字: 无
- 画面内实体文字/logo 状态: 无
- 后期叠加状态: 无
- 使用素材: `<参考视频>`, `<人物1>`, `<场景1>`, `<全局素材1>`
- 参考帧决策: 使用 RF_PERSON_001 + RF_SCENE_001
- 禁止项/缺失项: 图案必须匹配素材、不得出现参考蓝白渐变；无缺失项
- 状态: `ready_with_assumptions`

### 分镜3 / Beat 3 — 7.5-8.0s
- 参考功能 / 目标功能: 动作转场/注意力转移 / 双手放下，为面部揭示做准备
- 场景迁移: 同暗调室内；画面结构由“手部主体”切换为“面部主体”
- 主体/动作迁移: 双手快速下移出画面下方，前景遮挡消失、面部逐渐居中；同一连续镜头内的揭示过渡（非剪辑转场）
- 生成画面/运镜: 近景；手持轻微晃动
- 台词/口播/旁白/画面文字: 无
- 画面内实体文字/logo 状态: 无
- 后期叠加状态: 无
- 使用素材: `<参考视频>`, `<人物1>`, `<场景1>`, `<全局素材1>`（延续/回置绑定）
- 参考帧决策: 使用 RF_PERSON_001 + RF_SCENE_001
- 禁止项/缺失项: 双手下移需干净利落、不遮挡面部揭示（audit-only）；无缺失项
- 状态: `ready_with_assumptions`

### 分镜4 / Beat 4 — 8.0-12.6s
- 参考功能 / 目标功能: 主体揭示与互动收束 / 揭示与目标风格一致的人物形象并收束
- 场景迁移: 同暗调室内，人物与场景保持连续
- 主体/动作迁移: 面部揭示 → 微笑 → 嘴唇微动 → 头部轻微晃动，面向镜头收束；人物非特定身份，造型与目标暗黑美甲风格一致
- 生成画面/运镜: 中近景/近景中心构图，背景简化；手持轻微晃动
- 台词/口播/旁白/画面文字: 参考台词 `Do you think I'm strange?` 不迁移；保留结尾互动结构，目标文案缺失（`missing_optional_input`），仅保留口型/互动
- 画面内实体文字/logo 状态: 不生成未确认可读文字；无
- 后期叠加状态: 无
- 使用素材: `<参考视频>`, `<人物1>`, `<场景1>`, `<全局素材1>`（延续绑定）
- 参考帧决策: 使用 RF_PERSON_001 + RF_SCENE_001
- 禁止项/缺失项: 不得复现参考人物身份（compact guardrail）；`MI_001`(actor_identity)/`MI_002`(scene) 以生成假设处理，不阻塞
- 状态: `ready_with_assumptions`

## 参考帧摘要

| frame_id | 类型 | 来源实体 | 生成策略 | 状态 | 输出 |
| --- | --- | --- | --- | --- | --- |
| `RF_PERSON_001` | `person_reference` | `ENT_PERSON_001` | `text_to_image` | `succeeded` / 质检 `passed` | `08_reference_frames/RF_PERSON_001.png` |
| `RF_SCENE_001` | `scene_reference` | `ENT_SCENE_001` | `text_to_image` | `succeeded` / 质检 `passed` | `08_reference_frames/RF_SCENE_001.png` |

`consistency_review.status=passed`；`global_missing_inputs=[]`、`blocking_items=[]`。

## H3 状态

- H3 打包: `completed`；`09_h3_package/h3_packager_input.md`、`09_h3_package/minimax_h3_prompt.md`（Ref2VA 六段式）、`reference_mapping.md`、`pre_generation_checklist.md`、`assets/`。
- 可提交 H3 request: `09_h3_package/h3_request.json`（`model=MiniMax-H3`，3 张图片 + 1 段参考视频，`ratio=9:16`，`resolution=480P`）。
- H3 视频生成: `not_submitted`（dry-run 边界，未上传、未提交、未轮询、无成片）。
- `10_h3_video_output/` 未创建（符合 dry-run 规则）。

## 缺失项与假设

- `missing_inputs[]`: `MI_001` `actor_identity`、`MI_002` `scene`，均为 `missing_generate_fallback` + `generate_with_confirmed_assumption`。
- `generation_assumptions[]`: `GA_001` 平铺美甲→佩戴展示（用户确认）；`GA_002` 非特定身份表演者造型贴合暗黑美甲（用户确认）；`GA_003` 场景迁移暗调室内（fallback，proposed）。
- `readiness_check.overall_status=ready_with_assumptions`，`blocking_item_ids=[]`。
