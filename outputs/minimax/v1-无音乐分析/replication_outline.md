# 复刻大纲 (replication outline)

- schema_version: `common_replication_outline.v2`
- status: **ready_with_assumptions**
- generation_scope: `single_generation_task`
- 时间精度: `one_decimal` / `truncate`（全部时间字段截断到 0.1s，不四舍五入）
- 参考视频: `minimax.mp4`（2560×1440, 24.0 fps, 15.0s 窗口）
- 目标: 同一结构下的品牌蒙太奇；画面文字统一为 **MetaX**，人物模特替换为**猫**

## 全局元素库 (global_appearance_dedup_pass)

| entity_id | entity_type | entity_name | merge_status |
| --- | --- | --- | --- |
| ent_001 | style_atmosphere | 双圆取景框 + 红色字段带 + 暖调氛围 | single_source_no_merge |
| ent_002 | scene_appearance | 街边亭廊（场景一） | kept_separate_visually_distinct |
| ent_003 | scene_appearance | 暖陶土色建筑立面（场景二） | kept_separate_visually_distinct |
| ent_004 | scene_appearance | 浅灰屋顶露台（场景三） | kept_separate_visually_distinct |
| ent_005 | main_subject_appearance | 猫（目标主体） | merged_same_entity |
| ent_006 | key_prop_appearance | MetaX 字标与多载体文字 | single_source_no_merge |
| ent_007 | key_prop_appearance | 品牌光影投影 | kept_separate_visually_distinct |

## 参考元素处理计划

| element_id | element_type | decision | summary |
| --- | --- | --- | --- |
| el_001 | shot_structure | inherit | 四镜蒙太奇结构：0.0-4.3 / 4.3-8.3 / 8.3-11.8 / 11.8-15.0，由城市空镜递进到主体近 |
| el_002 | time_structure | inherit | 源时长 15.1s，分析窗口截断到前 15.0s，转场均发生在镜尾约 0.2s。 |
| el_003 | camera | inherit | shot1 0.0-1.1s 由整体失焦到合焦的移焦揭示。 |
| el_004 | camera | inherit | shot1 约 3.1-4.3s 主体画面占比缓慢变大的轻微推近。 |
| el_005 | composition | inherit | 全片黑色底上两个相交圆形视口形成的双圆（心形/双筒望远镜式）框中框版式。 |
| el_006 | visual_style | inherit | 暖米色调、柔和侧向日光、长投影、实拍写实质感、浅景深与叠加层和场景深度分离。 |
| el_007 | transition | inherit | 三次切镜都以横向运动模糊叠加红色水平故障线遮挡收尾后硬切。 |
| el_008 | action_structure | adapt | shot2 全程悬挂织物旗帜随风飘动、下摆翻卷露出红色内衬。 |
| el_009 | action_structure | adapt | shot3 约 11.1s 主体头部向侧方转动后停住。 |
| el_010 | interaction_relation | adapt | shot4 约 12.6s 手部抬起触碰墨镜上缘做一次调整后放下。 |
| el_011 | person_or_body | adapt | shot3 与 shot4 出现同一人物模特，承担站立、持物、转头与触碰墨镜的动作；shot1 与 shot2 无人物。 |
| el_012 | prop | adapt | shot3 的红色单肩包与黑色咖啡杯，shot4 的红框墨镜、圆形大耳环与红色衣领。 |
| el_013 | scene_content | adapt | shot1 深色顶棚公交候车亭与米色混凝土建筑立面；shot2 米色高层竖排窗格立面；shot3 混凝土屋顶天台与城市天 |
| el_014 | text_or_ui | adapt | 源品牌文字以实体字标、墙面光影投影、悬挂旗帜竖排字、建筑立面竖排大字与镜片反射小字五种物理载体出现。 |
| el_015 | text_or_ui | adapt | 全部 shot 左右两侧各三行红色等宽字体字段注释叠加层，位置固定且不参与场景深度。 |
| el_016 | dialogue_or_voiceover | discard | 末镜约 12.2-15.0s 出现一句稀疏英文口语，跨出分析窗口被截断，画面无对应口型证据。 |
| el_017 | unsupported_audio | discard | 全片音乐/BGM/音效/疑似唱歌/声音情绪/卡点节奏未纳入分析产物。 |

## 显式替换绑定

- `rb_001` 参考视频中的源品牌字标文字（实体字标 / 墙面投影 / 悬挂旗帜 / 建筑立面大字 / 镜片反射等多载体） -> **MetaX**｜受影响: VS001:shot1,VS001:shot2,VS001:shot3,VS001:shot4｜时间: 0.0-4.3s,4.3-8.3s,8.3-11.8s,11.8-15.0s
- `rb_002` 参考视频中的人物模特 -> **cat**｜受影响: VS001:shot3,VS001:shot4｜时间: 8.3-11.8s,11.8-15.0s

## 分镜时间线 (timeline_units / temporal_segments)

### U1  0.0-4.3s（4.3s）  source=VS001:shot1
- content_subject_type: `environment`｜target: 开场揭示主体场所与品牌字标
- 失焦到合焦揭示城市街边亭廊与 MetaX 字标，稳定展示后小幅推近，结尾以故障线转场。
  - **S1a** 0.0-1.1s｜`visual_display` -> `attention_hook_reveal`
    - 双圆取景框内，失焦的街边亭廊逐渐合焦，画面主体位置出现 MetaX 字标。
    - 机制: mch_frame_within_frame,mch_side_field_bars,mch_rack_focus
    - 画内文字: 亭廊顶棚正面的白色 MetaX 字标，随后在后墙出现同字样的光影投影
    - overlays: 4 项（后期渲染）
  - **S1b** 1.1-3.1s｜`visual_display` -> `subject_display`
    - 合焦后稳定展示街边亭廊与 MetaX 字标，后墙投影随光线缓慢移动。
    - 机制: mch_frame_within_frame,mch_side_field_bars
    - 画内文字: 顶棚正面 MetaX 字标与后墙同字样投影持续可见
    - overlays: 4 项（后期渲染）
  - **S1c** 3.1-4.1s｜`visual_display` -> `subject_display_push_in`
    - 镜头结尾以小幅推近让亭廊与字标在画面中占比缓慢增大。
    - 机制: mch_frame_within_frame,mch_side_field_bars,mch_slight_zoom
    - 画内文字: 推近过程中顶棚正面 MetaX 字标保持清晰可见
    - overlays: 4 项（后期渲染）
  - **S1d** 4.1-4.3s｜`transition` -> `transition_out`
    - 画面横向运动模糊并出现红色水平故障线条带，随后硬切到下一镜。
    - 机制: mch_frame_within_frame,mch_side_field_bars,mch_glitch_wipe_u1
    - overlays: 4 项（后期渲染）
### U2  4.3-8.3s（4.0s）  source=VS001:shot2
- content_subject_type: `environment`｜target: 以第二载体再次呈现品牌字标
- 暖陶土色建筑立面上的悬挂织物竖旗持续飘动，旗面竖排 MetaX，结尾以故障线转场。
  - **S2a** 4.3-8.1s｜`visual_display` -> `second_carrier_reveal`
    - 暖陶土色建筑立面上悬挂的窄幅织物竖旗持续飘动，下摆翻卷露出红色内衬，旗面为竖排 MetaX。
    - 机制: mch_frame_within_frame,mch_side_field_bars,mch_banner_flutter
    - 画内文字: 悬挂织物竖旗旗面为竖排 MetaX 字标，随旗帜飘动
    - overlays: 4 项（后期渲染）
  - **S2b** 8.1-8.3s｜`transition` -> `transition_out`
    - 画面横向运动模糊并出现红色水平故障线条带，随后硬切到主体所在场景。
    - 机制: mch_frame_within_frame,mch_side_field_bars,mch_glitch_wipe_u2
    - overlays: 4 项（后期渲染）
### U3  8.3-11.8s（3.5s）  source=VS001:shot3
- content_subject_type: `mixed`｜target: 引入目标主体并与建筑立面字标同框
- 浅灰屋顶露台上，橘白双色短毛猫（红项圈、红框墨镜）停留并转头，与建筑立面竖排 MetaX 大字同框，结尾以故障线转场。
  - **S3a** 8.3-11.1s｜`visual_display` -> `subject_introduction`
    - 浅灰屋顶露台上，一只橘白双色短毛猫（红项圈、红框墨镜）停留，身后建筑立面有竖排 MetaX 大字。
    - 机制: mch_frame_within_frame,mch_side_field_bars
    - 画内文字: 身后建筑立面为竖排 MetaX 大字
    - overlays: 4 项（后期渲染）
  - **S3b** 11.1-11.6s｜`action_or_interaction` -> `micro_action_head_turn`
    - 猫在镜头后半段自然把头转向画面一侧，带轻微停顿后稳定。
    - 机制: mch_frame_within_frame,mch_side_field_bars,mch_subject_head_turn
    - overlays: 4 项（后期渲染）
  - **S3c** 11.6-11.8s｜`transition` -> `transition_out`
    - 画面横向运动模糊并出现红色水平故障线条带，随后硬切到面部特写。
    - 机制: mch_frame_within_frame,mch_side_field_bars,mch_glitch_wipe_u3
    - overlays: 4 项（后期渲染）
### U4  11.8-15.0s（3.2s）  source=VS001:shot4
- content_subject_type: `mixed`｜target: 以近距特写与镜面反射收束全片
- 猫的面部大特写佩戴红框墨镜，前爪触碰镜框后回落，镜片中反射出 MetaX 字样，画面收束。
  - **S4a** 11.8-12.2s｜`visual_display` -> `detail_and_reflection_reveal`
    - 猫的面部大特写，佩戴红框墨镜，镜片中反射出建筑与竖排 MetaX 字样。
    - 机制: mch_frame_within_frame,mch_side_field_bars
    - 画内文字: 墨镜镜片中反射出建筑与竖排 MetaX 字样，随角度变化可见度变化
    - overlays: 4 项（后期渲染）
  - **S4b** 12.2-12.8s｜`action_or_interaction` -> `micro_action_adjust`
    - 猫抬起前爪触碰墨镜上缘并轻推一次后回落，镜片反射角度随之变化。
    - 机制: mch_frame_within_frame,mch_side_field_bars,mch_paw_adjust
    - 画内文字: 墨镜镜框上缘被前爪触碰后轻微移动，镜中 MetaX 字样角度随之变化
    - overlays: 4 项（后期渲染）
  - **S4c** 12.8-15.0s｜`visual_display` -> `closing_detail`
    - 猫面部特写保持稳定，镜片中 MetaX 字样随角度变化可见度变化，画面在双圆取景框中收束。
    - 机制: mch_frame_within_frame,mch_side_field_bars
    - 画内文字: 墨镜镜片中持续可见建筑与竖排 MetaX 字样，可见度随角度变化
    - overlays: 4 项（后期渲染）

## 参考帧计划摘要

- plan_required=True, scene_entity_count=3, person_entity_count=0, planned_frame_count=3
- plan_path: `07_reference_frame_plan/reference_frame_plan.json`
- triggered_rules: scene_reference_entity_present

## 声音

- 台词/口播: `missing_required_input`（源片口语原文不迁移，本版本省略）
- 音乐/BGM/音效/唱歌/声音情绪: `unsupported_skipped`

## 缺失输入与生成假设

- mi_001 `actor_appearance`: missing_generate_fallback / generate_with_confirmed_assumption
- mi_002 `scene_reference`: missing_generate_fallback / generate_with_confirmed_assumption
- mi_003 `descriptive_field_overlay_text`: missing_required_input / omit_or_neutralize
- mi_004 `dialogue_or_voiceover`: missing_required_input / omit_or_neutralize
- ga_001 `actor`: 目标主体为一只猫，替换参考视频中的人物模特；品种/毛色/体型未指定，按低风险默认生成：短毛、橘白双色、绿色眼睛、体型适中。
- ga_002 `prop`: 为保留镜面框架与红色配饰机制，猫佩戴红框墨镜与红色项圈；参考中手部调整墨镜的动作改写为猫爪抬起触碰镜框边缘后回落。
- ga_003 `scene`: 保留参考视频的城市空间结构、暖色日光风格、前中后景层次与浅景深，但目标场景内容按可见差异锚点适配，不逐字复制参考场景。

## 校验标记

- `no_image_or_video_target_assets_provided`
- `target_subject_appearance_from_generation_assumption`
- `target_scene_content_from_generation_assumption_with_visible_difference_anchor`
- `reference_video_source_duration_exceeds_15s_using_first_15s_excerpt`
- `descriptive_field_overlay_text_omitted_missing_target_copy`
- `dialogue_or_voiceover_omitted_missing_target_copy`
- `source_subject_identity_uncertainty_carried_from_reference`
- `prompt_shots_from_temporal_segments`
- `reference_frames_pending_step7_step8`
