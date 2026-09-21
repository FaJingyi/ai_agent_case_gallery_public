# 复刻大纲人工审阅稿（replication_outline.md）

- `schema_version`: `common_replication_outline.v2`
- `status`: `ready_with_assumptions`
- `generation_scope`: `single_generation_task`
- `time_precision_policy`: `precision=one_decimal`，`method=truncate`
- `timeline_unit_count`: 1
- `temporal_segment_count`: 4
- `h3_prompt_shot_count`: 1（单个连续镜头内部 4 个节拍，不新增分镜编号）
- 对应机器产物：`06_replication_outline/replication_outline.json`

## 1. 参考视频事实

- 参考视频：`nail-6.mp4`，12.6s，1080×1920，9:16 竖屏，单镜头连续拍摄（`VS001_SH001`）。
- 结构：一个 12.6s 连续镜头，内部四个节拍——0.0-3.0s 双手交扣缓慢转动；3.0-6.5s 摊开手掌展示甲面；6.5-7.5s 双手下移出画；7.5-12.6s 面部显露并微笑直视镜头。
- 镜头语言：第一人称 POV、眼平自拍机位、紧凑特写、中心构图、主体占幅大留白少、手持微动、无推拉摇移、深焦、无剪辑点。
- 场景：轿车前排座舱，黑色皮座椅，开启天窗透入柔和自然日光，窗外绿色树叶，左下可见方向盘边缘。
- 原片美甲：白色/奶白底色、浅蓝指尖、蓝色花卉图案。
- 原片台词：ASR 识别到画内人声 `Do you think I'm strange?`（6.4-10.2s，`speech_source=on_screen_speech`）。

## 2. 目标视频

- 目标时长/画幅：12.6s，9:16 竖屏，单镜头单次生成（`single_generation_task`）。
- 目标主体：生成目标女性，暗黑哥特编辑风造型；双手承载目标美甲图案。
- 目标美甲：来自用户素材 `shangpin-3`——长尖形/杏仁形甲片，哑光灰褐 + 黑色金属箔并带银白细纹，立体白珍珠与少量金边珍珠，棕色/橄榄色虹膜眼睛图案，高光泽表面。
- 目标场景：沿用参考视频的轿车前排座舱空间、光线与氛围（用户明确要求“场景风格和参考视频一致”）。
- 目标台词：用户未提供目标文本 → 原片台词按 `discard` 处理，结尾改写为无声温暖微笑与直视镜头（`speech_status=on_screen_speech`，`target_text_items=[]`）。

## 3. 两层继承计划

强继承项（`inherit`，必须可见）：时间结构、单镜头顺序、镜头语言（视角/构图/运镜/焦点）、画面节奏结构、空间层次、手部展示节拍与双手下移揭示机制。

参考继承项（`adapt`）：主体运动模式、身体姿态与动作语汇、人物外观、美甲图案、场景具体材质、原片台词功能、原片记忆点内容。

丢弃项（`discard`）：原片画内台词文本、原片音频/音乐分析（`unsupported_skipped`）。

## 4. 参考元素处理结论

| source_ref | decision | 目标侧处理 |
| --- | --- | --- |
| `shot_timeline[0].time_range_sec` | inherit | 完整保留 12.6s 单镜头与四节拍时间点 |
| `video_generation_context.camera` | inherit | 第一人称 POV / 眼平自拍 / 紧凑特写 / 手持微动 |
| `video_generation_context.spatial_framing` | inherit | 中心构图、主体占幅大、前中后景三层 |
| `memory_points.visual[0]`（手部展示choreography） | adapt | 保留节拍，替换为暗黑哥特甲面 |
| `memory_points.visual[1]`（下移揭示面部） | inherit | 同一手法保留 |
| `video_generation_context.subject.distinctive_features` | adapt | 替换为暗黑哥特造型女性 |
| `global_subject_identity_tracks[0]` | adapt | 目标人物身份锚点，去识别化 |
| `scenes[0].video_generation.scene` | adapt | 车厢空间结构保留，内容适配目标 |
| `video_generation_context.scene.common_props` | adapt | 座椅/天窗/绿植作为普通场景上下文 |
| `script_generation.text_slots[0]` | discard | 无可确认目标文本，改无声直视 |
| `audio_analysis` | discard | 音频迁移 `unsupported_skipped` |

## 5. 时间轴（唯一 unit：`VS001_shot1`，0.0-12.6s，`human`）

### 节拍 1 `seg_01`｜0.0-3.0s｜开场钩子：甲面与戒指展示

- 参考功能 → 目标功能：`opening_hook_detail_display` → `opening_hook_target_nail_and_jewellery_display`
- 画面：双手交扣于下半脸前，缓慢外旋，暗黑哥特甲面与暗色金属戒指逐渐可读。
- 动作：双手交扣、指间相扣后缓慢外旋；起点（交扣稳定）→ 过程（匀速外旋）→ 终点（短暂停留）。
- 镜头：第一人称 POV、眼平自拍角度；紧凑特写、中心构图，双手占画面下部约三分之二；静止手持微动，无摇移推拉；双手/面部深焦。
- 空间：前景双手 → 中景人物 → 背景车厢三层，留白极少。
- 文本：无画面文字；台词按丢弃策略处理，本段无说话。
- 使用素材：`<video_1>`（参考视频）、`<picture_1>`（用户美甲素材）、`<picture_2>`（目标人物参考帧）、`<picture_3>`（车厢场景参考帧）。
- 参考帧决策：需要 `entity_target_woman` / `entity_nail_design`。
- 审计项：禁止泄漏源片人物身份；禁止金色首饰；禁止未确认文字/logo。
- 状态：`ready_with_assumptions`

### 节拍 2 `seg_02`｜3.0-6.5s｜甲面细节展示

- 参考功能 → 目标功能：`nail_art_detail_display` → `target_nail_art_detail_display`
- 画面：双掌完全转向镜头、十指摊开，十枚甲面完整可见，短暂停顿。
- 动作：由交扣转为掌面朝镜头，手指缓慢摊开并在最清晰姿态短暂停留。
- 镜头：第一人称 POV、眼平自拍；紧凑特写、中心构图，双手在画面中部到下部最大占幅；静止手持微动；甲面对焦。
- 空间：前景双手主导、面部被遮挡，车厢为背景层。
- 文本：无。
- 使用素材：同 `seg_01`。
- 参考帧决策：美甲保真是本段首要需求（`subject_reference`）。
- 审计项：全部可见甲面必须替换为目标图案；禁止源片身份泄漏。
- 状态：`ready_with_assumptions`

### 节拍 3 `seg_03`｜6.5-7.5s｜双手下移转场

- 参考功能 → 目标功能：`hands_lowered_transition` → `hands_lowered_transition_to_face_reveal`
- 画面：双手同步下移出画，下半画面清空，面部进入视觉中心。
- 动作：双手同步、匀速下移并离开画面底部，无剪切。
- 镜头：延续第一人称 POV、眼平自拍、紧凑特写、中心构图；静止手持微动；焦点由手自然过渡到面部。
- 空间：前景双手退出，中景人物成为主层，车厢保持背景。
- 文本：无。
- 使用素材：`<video_1>`、`<picture_2>`、`<picture_3>`。
- 参考帧决策：需要 `entity_target_woman` 面部/造型连续性锚点。
- 审计项：禁止剪切；禁止源片身份泄漏。
- 状态：`ready_with_assumptions`

### 节拍 4 `seg_04`｜7.5-12.6s｜面部显露与无声直视

- 参考功能 → 目标功能：`face_reveal_and_direct_address` → `face_reveal_and_non_verbal_direct_address`
- 画面：面部完全显露，温暖闭口微笑直视镜头，略侧头、发丝轻晃，保持到镜头结束。
- 动作：双手不在画面内；人物面部居中、占画面主体；无口型/说话动作。
- 镜头：第一人称 POV、眼平自拍、面部紧凑特写、中心构图；静止手持微动；焦点落在面部。
- 空间：中景人物为主层，发丝与肩部填充其余画面，车厢为背景。
- 文本：无台词、无旁白、无字幕（原片 ASR 台词已丢弃，用户未提供目标文本）。
- 使用素材：`<video_1>`、`<picture_2>`、`<picture_3>`。
- 参考帧决策：`entity_target_woman` 面部/造型连续性锚点。
- 审计项：禁止口型/说话动作；禁止迁移原片台词与音色。
- 状态：`ready_with_assumptions`

## 6. 全局外观库（第二层去重结果）

- `entity_target_woman`（`person_appearance`）：年轻女性、去识别化；深棕顺直长发；暗色眼妆与哑光深红/黑唇；黑色挺括无袖上衣；细黑颈链；手部/腕部暗色金属与珍珠首饰；黑/炭灰/锡灰调。可见差异：以暗黑哥特编辑风替代参考女性的金色首饰、自然妆与白色滚边上衣。
- `entity_nail_design`（`main_subject_appearance`）：长尖形甲片；哑光灰褐段 + 黑色金属箔段并带银白细金属纹；立体白珍珠与少量金边珍珠；棕色/橄榄黄虹膜黑色瞳孔的眼睛图案；高光泽。可见差异：以黑金属/哑光灰褐/珍珠/眼睛图案替代参考白蓝花卉。
- `entity_car_interior`（`scene_appearance`）：轿车前排；黑色皮座椅；开启天窗的柔和日光；窗外绿色树叶；左下方向盘边缘；柔和自然光、中等反差。
- `entity_style_atmosphere`（`style_atmosphere`）：真实手持自拍质感、柔和自然日光、竖屏紧凑特写氛围。

## 7. 记忆点迁移

| memory_id | 保留机制 | 目标侧改写 | 绑定 |
| --- | --- | --- | --- |
| `vm_001` | 三阶段手部choreography、时间顺序、朝镜头摊开展示 | 替换甲面图案为暗黑哥特设计 | `seg_01`-`seg_03` |
| `vm_002` | 双手下移揭示面部、同镜头连续 | 面部/妆容/造型改为目标女性 | `seg_03`-`seg_04` |
| `sm_001` | 单镜头“细节 → 揭示 → 直视”信息顺序 | 改写甲面设计、人物造型与结尾直视 | `VS001_shot1` |
| `sm_002` | 细节展示 → 面部揭示 → 温暖表情推进 | 改写目标人物表情与造型 | `seg_04` |
| `sm_003` | 结尾直视互动节拍 | 丢弃台词，改为无声温暖微笑注视 | `seg_04` |

## 8. 参考帧摘要

- `frame_requirement_level`: `required_visual_anchors`
- `plan_required`: `true`，`plan_path`: `07_reference_frame_plan/reference_frame_plan.json`
- 人物实体 1（`entity_target_woman` → `FR_Person_01`，生成）、主体实体 1（`entity_nail_design` → `FR_Nail_01`，复用用户素材）、场景实体 1（`entity_car_interior` → `FR_Scene_01`，生成）
- `planned_frame_count`: 3；`selected_h3_image_count`: 3；`h3_image_budget`: 8；无合并。
- 参考帧生成/复用详情见步骤 7/8 产物。

## 9. 缺口、假设与校验标记

- `missing_inputs`：`mi_target_speech_text`（目标台词缺失，非阻塞，已降级为无声直视）。
- `generation_assumptions`：`asm_nail_worn_on_hand`（甲片按佩戴在手上生成）、`asm_person_styling_gothic`（人物暗黑哥特造型为生成假设，含可见差异锚点）。
- `validation_flags`：
  - `target_dialogue_omitted_without_target_text`
  - `person_appearance_generated_from_assumption_with_visible_difference`
  - `scene_inherited_by_explicit_user_request`
- `readiness_check`：`ready_with_assumptions`，无阻塞项。
- 音频（音乐/BGM/音效/声音情绪/卡点）统一记为 `unsupported_skipped`，不进入生成描述。
- 本步骤未生成 H3 prompt、request 或提交任务；H3 相关产物见 `09_h3_package/`。
