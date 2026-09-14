# 复刻大纲审阅稿 (replication_outline.md)

- 模式: shot_structure; 状态: ready_with_assumptions
- 参考视频: test_data/nail-5/nail-5.mp4 (前 15.0s, 8 shots)
- 目标主体: 深色哥特眼球图案美甲 (来自 shangpin-3.png)
- timeline_unit_count: 8; temporal_segment_count: 15; h3_prompt_shot_count: 15
- 说明: [Shot N] 为 prompt-level shots (来自 temporal_segments)，非 reference-level shots。
- 参考帧: plan_required=true, planned_frame_count=3 (1 人物 + 2 场景)

## 参考元素处理计划

| element_id | element_type | decision | 目标绑定 |
| --- | --- | --- | --- |
| ret_001 | time_structure | inherit | target_video, timeline_units[] |
| ret_002 | shot_structure | inherit | timeline_units[].unit_id |
| ret_003 | composition | inherit | timeline_units[].reference_mapping.camera_and_composition, target_video |
| ret_004 | camera | inherit | timeline_units[].reference_mapping.camera_motion, target_video |
| ret_005 | action_structure | inherit | timeline_units[].reference_mapping.action_progression, temporal_segments[].motion_state |
| ret_006 | transition | inherit | temporal_segments[].editing_and_transition, target_video |
| ret_007 | visual_style | adapt | target_video, global_appearance_dedup_pass.global_appearance |
| ret_008 | scene_content | adapt | scene_transfer[].scene_description_for_generation, global_appearance_dedup_pass.global_appearance |
| ret_009 | subject_content | adapt | explicit_replacement_coverage, timeline_units[].temporal_segments[].reference_mapping.primary_visual_subject, h3_asset_user_001 |
| ret_010 | person_or_body | adapt | global_appearance_dedup_pass.global_appearance, generation_assumptions.ga_003 |
| ret_011 | prop | adapt | global_appearance_dedup_pass.global_appearance, timeline_units[].temporal_segments[].prop_transfer |
| ret_012 | composition | inherit | timeline_units[4].temporal_segments[], special_mechanism_transfer[] |
| ret_013 | action_structure | inherit | timeline_units[0].temporal_segments[1], memory_transfer_plan.visual[vm_002] |
| ret_014 | text_or_ui | discard | post_overlay_plan[], text_logo_policy |
| ret_015 | unsupported_audio | discard | unsupported_audio |
| ret_016 | incidental_detail | inherit | timeline_units[].temporal_segments[].motion_state |
| ret_017 | subject_content | adapt | explicit_replacement_coverage, timeline_units[].temporal_segments[] |

## 全局外观实体

| entity_id | entity_name | entity_type | merge_status |
| --- | --- | --- | --- |
| ge_subject_001 | 目标美甲图案 | main_subject_appearance | merged_same_entity |
| ge_person_001 | 非可识别女性表演者 | person_appearance | merged_same_entity |
| ge_scene_001 | 深色哥特室内化妆间 | scene_appearance | single_entity |
| ge_scene_002 | 月夜哥特石庭/花园 | scene_appearance | merged_same_entity |
| ge_prop_001 | 哥特配饰与画中画道具 | key_prop_appearance | merged_same_category |
| ge_atmosphere_001 | 暗黑哥特低调影调 | style_atmosphere | single_entity |

## 时间轴 / 分镜

### tu_001 0.0-3.5s ref=VS001:shot1
- story_function: opening_hook; content_subject_type: mixed
- 生成画面: 室内开场，人物双手抬起向镜头展示目标美甲，随后前伸使指尖接近镜头。
- 参考功能→目标功能 | 运镜: 镜头基本静止，仅轻微手持晃动。 | 编辑/转场: 开场直接进入，无前一镜；镜内为连续动作，无剪切。
- must_be_visible: 深色哥特眼球图案美甲, 双手, 深色哥特装扮, 深色哥特室内空间
- 使用素材: h3_asset_user_001, h3_asset_reference_video
  - **seg_001_01** 0.0-3.0s (visual_display→visual_display)
    - 生成画面: 前臂上抬，手掌打开。
    - 动作/运镜: 双手抬起正对镜头展示美甲。 | 采用紧凑手部特写，主体居中，上下留字幕安全区。
    - 场景迁移: 深色哥特室内化妆间，人物双手在暗色背景前展示美甲。
    - 文字/叠加: subtitle:missing_required_input | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: mi_002; 状态: ready_with_assumptions
  - **seg_001_02** 3.0-3.5s (action_or_interaction→action_or_interaction)
    - 生成画面: 前臂前推，指尖接近镜头平面。
    - 动作/运镜: 双手前伸使指尖逼近镜头。 | 紧凑特写随指尖前伸略微加强前景占比。
    - 场景迁移: 暗色背景中双手前伸逼近镜头。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions

### tu_002 3.5-6.0s ref=VS001:shot2
- story_function: reveal; content_subject_type: mixed
- 生成画面: 对比硬切进入月夜哥特石庭，人物换深色装扮，双手举过面部、手指张开，展示目标美甲。
- 参考功能→目标功能 | 运镜: 镜头基本静止，轻微手持晃动。 | 编辑/转场: 由 shot1 对比硬切进入。
- must_be_visible: 深色哥特眼球图案美甲, 双手手指张开, 非可识别女性表演者（深色长发、暗色哥特装扮、双手入画）, 月夜哥特石庭/花园
- 使用素材: h3_asset_user_001, h3_asset_reference_video
  - **seg_002_01** 3.5-4.5s (transition→transition)
    - 生成画面: 月夜石庭中，人物深色装扮双手举起。
    - 动作/运镜: 双手举起至面部前方。 | 半身中景，主体居中，上下留字幕安全区。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 特殊机制[special_transition]: Hard cut from the dark indoor dressing room to the moonlit gothic stone garden, with the whole scene, outfit and lighting changing at the cut, landing exactly as the hands rise into frame.
    - 缺失输入: 无; 状态: ready_with_assumptions
  - **seg_002_02** 4.5-6.0s (visual_display→visual_display)
    - 生成画面: 月夜石庭中十指张开的双手，深色装扮。
    - 动作/运镜: 十指张开并停留。 | 半身中景，双手位于画面中心，背景简化。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions

### tu_003 6.0-7.5s ref=VS001:shot3
- story_function: emotional_reaction; content_subject_type: human
- 生成画面: 人物面部特写：双手捂住嘴巴后放下，头部微侧，展示目标美甲与情绪反应。
- 参考功能→目标功能 | 运镜: 静止镜头，轻微手持晃动。 | 编辑/转场: 由 shot2 硬切收紧景别，情绪从展示转向反应。
- must_be_visible: 深色哥特眼球图案美甲, 局部面部, 双手, 非可识别女性表演者（深色长发、暗色哥特装扮、双手入画）
- 使用素材: h3_asset_user_001, h3_asset_reference_video
  - **seg_003_01** 6.0-7.5s (action_or_interaction→action_or_interaction)
    - 生成画面: 月夜石庭背景下人物面部特写，深色装扮，指尖掠过面部时可见目标美甲。
    - 动作/运镜: 双手抬起捂住嘴巴后放下，头部微侧。 | 面部特写，主体居中，背景简化。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions

### tu_004 7.5-9.0s ref=VS001:shot4
- story_function: proof; content_subject_type: mixed
- 生成画面: 半身中景：人物双手举起、手指交叉展示目标美甲，随后双手分开、指尖指向镜头。
- 参考功能→目标功能 | 运镜: 静止镜头，轻微手持晃动。 | 编辑/转场: 由 shot3 硬切拉回半身景别。
- must_be_visible: 深色哥特眼球图案美甲, 手指交叉, 指尖, 非可识别女性表演者（深色长发、暗色哥特装扮、双手入画）, 月夜哥特石庭/花园
- 使用素材: h3_asset_user_001, h3_asset_reference_video
  - **seg_004_01** 7.5-8.5s (visual_display→visual_display)
    - 生成画面: 月夜石庭半身中景，双手交叉展示深色哥特美甲。
    - 动作/运镜: 双手举起交叉手指。 | 半身中景，双手位于画面中心。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions
  - **seg_004_02** 8.5-9.0s (action_or_interaction→action_or_interaction)
    - 生成画面: 双手分开指向镜头的展示姿态。
    - 动作/运镜: 双手分开，指尖指向镜头。 | 中景，指尖朝向镜头，形成前伸感。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions

### tu_005 9.0-10.5s ref=VS001:shot5
- story_function: proof; content_subject_type: mixed
- 生成画面: 硬切到手部特写，前景手部静止展示目标美甲细节，左上角画中画小窗显示另一只手持暗色道具并轻微移动。
- 参考功能→目标功能 | 运镜: 静止镜头，轻微手持晃动。 | 编辑/转场: 由 shot4 硬切收拢到手部特写并叠加画中画图形层。
- must_be_visible: 深色哥特眼球图案美甲, 手部特写, 左上角画中画, 暗色道具, 非可识别女性表演者（深色长发、暗色哥特装扮、双手入画）
- 使用素材: h3_asset_user_001, h3_asset_reference_video
  - **seg_005_01** 9.0-9.5s (transition→transition)
    - 生成画面: 手部特写展示深色哥特美甲，左上角有画中画小窗。
    - 动作/运镜: 前景手部静止；画中画出现。 | 手部特写，主体居中，左上角预留画中画小窗位置，底部预留字幕安全区。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: subtitle:missing_required_input | in_scene=0
    - 参考帧: none entities=
    - 特殊机制[special_composition]: Keep a picture-in-picture inset in the top-left corner of the frame throughout this shot: the main frame is a macro close-up of the dark gothic nail art on one hand, while the smaller inset window in the top-left shows another hand of the same performer lightly holding a dark dried flower; the main image stays larger and sharper, the inset stays clearly smaller and layered above it.
    - 缺失输入: 无; 状态: ready_with_assumptions
  - **seg_005_02** 9.5-10.5s (visual_display→visual_display)
    - 生成画面: 手部特写持续展示目标美甲，左上角画中画持暗色干花。
    - 动作/运镜: 前景静止，画中画内手部轻微移动。 | 手部特写持续，画中画稳定在左上角。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: subtitle:missing_required_input | in_scene=0
    - 参考帧: none entities=
    - 特殊机制[special_composition]: Keep a picture-in-picture inset in the top-left corner of the frame throughout this shot: the main frame is a macro close-up of the dark gothic nail art on one hand, while the smaller inset window in the top-left shows another hand of the same performer lightly holding a dark dried flower; the main image stays larger and sharper, the inset stays clearly smaller and layered above it.
    - 缺失输入: 无; 状态: ready_with_assumptions

### tu_006 10.5-12.0s ref=VS001:shot6
- story_function: outfit_change_display; content_subject_type: mixed
- 生成画面: 半身中景：人物换深色长外套，在月夜石庭中双手举起展示目标美甲，随后放下整理衣领。
- 参考功能→目标功能 | 运镜: 静止镜头，轻微手持晃动。 | 编辑/转场: 由 shot5 硬切进入，画中画与底部文字消失。
- must_be_visible: 深色哥特眼球图案美甲, 双手, 非可识别女性表演者（深色长发、暗色哥特装扮、双手入画）, 深色长外套, 月夜哥特石庭/花园
- 使用素材: h3_asset_user_001, h3_asset_reference_video
  - **seg_006_01** 10.5-11.5s (visual_display→visual_display)
    - 生成画面: 月夜石庭半身中景，人物深色长外套，双手举起展示深色哥特美甲。
    - 动作/运镜: 双手举起展示指甲。 | 半身中景，主体居中。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions
  - **seg_006_02** 11.5-12.0s (action_or_interaction→action_or_interaction)
    - 生成画面: 人物双手放下整理深色长外套衣领。
    - 动作/运镜: 双手放下整理衣领。 | 半身中景。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions

### tu_007 12.0-13.5s ref=VS001:shot7
- story_function: accessory_display; content_subject_type: mixed
- 生成画面: 面部特写：人物头戴深色宽檐帽，双手抬起、手指轻触帽檐展示目标美甲，随后双手放下、头部微低。
- 参考功能→目标功能 | 运镜: 静止镜头，轻微手持晃动。 | 编辑/转场: 由 shot6 硬切收紧到面部特写，并新增深色宽檐帽。
- must_be_visible: 深色哥特眼球图案美甲, 深色宽檐帽, 指尖, 非可识别女性表演者（深色长发、暗色哥特装扮、双手入画）, 月夜哥特石庭/花园
- 使用素材: h3_asset_user_001, h3_asset_reference_video
  - **seg_007_01** 12.0-12.8s (visual_display→visual_display)
    - 生成画面: 面部特写，深色宽檐帽下人物手指轻触帽檐，指尖可见深色哥特美甲。
    - 动作/运镜: 双手抬起至帽檐。 | 面部特写，手部进入画面前景。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions
  - **seg_007_02** 12.8-13.5s (action_or_interaction→action_or_interaction)
    - 生成画面: 人物放下双手，深色宽檐帽下头部微低。
    - 动作/运镜: 双手放下，头部微低。 | 面部特写。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions

### tu_008 13.5-15.0s ref=VS001:shot8
- story_function: closing; content_subject_type: mixed
- 生成画面: 中全景收尾：人物蹲在月夜石庭中，深色长外套，双手举起展示目标美甲后放下并保持蹲姿。
- 参考功能→目标功能 | 运镜: 静止镜头，轻微手持晃动。 | 编辑/转场: 由 shot7 硬切拉宽到蹲姿中全景。
- must_be_visible: 深色哥特眼球图案美甲, 蹲姿, 深色长外套, 深色宽檐帽, 非可识别女性表演者（深色长发、暗色哥特装扮、双手入画）, 月夜哥特石庭/花园
- 使用素材: h3_asset_user_001, h3_asset_reference_video
  - **seg_008_01** 13.5-14.5s (visual_display→visual_display)
    - 生成画面: 月夜石庭中人物蹲姿，深色长外套与宽檐帽，双手举起展示深色哥特美甲。
    - 动作/运镜: 蹲下并举起双手展示指甲。 | 中全景，人物居中，环境与人物同框。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: 无 | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: 无; 状态: ready_with_assumptions
  - **seg_008_02** 14.5-15.0s (closing_or_prompt→closing_or_prompt)
    - 生成画面: 人物蹲在月夜石庭中，双手放下，整体造型与环境收束。
    - 动作/运镜: 双手放下并保持蹲姿。 | 中全景保持。
    - 场景迁移: 月夜哥特石庭/花园：月夜下的哥特石庭，深色石墙、铁艺门、常春藤与湿石地面，暗色反射水池，冷月光＋暖色灯盏点缀。
    - 文字/叠加: closing_or_prompt_text:missing_required_input | in_scene=0
    - 参考帧: none entities=
    - 缺失输入: mi_002; 状态: ready_with_assumptions

## 缺失输入
- mi_001 nail_art_worn_on_hands: missing_generate_fallback -> generate_with_confirmed_assumption
- mi_002 on_screen_subtitle: missing_required_input -> omit_or_neutralize

## 生成假设
- ga_001 usage_state: 将静态平铺的穿戴甲素材呈现为佩戴在人物手部/指甲上的使用状态，并保持图案、装饰与配色一致 [user_confirmed]
- ga_002 scene: 按用户要求把场景与人物理念装扮调整为与暗黑/哥特风美甲一致的氛围（低饱和暗色调、深色/质感背景、神秘精致氛围） [user_confirmed]
- ga_003 actor_identity: 人物身份未提供，按非可识别表演者处理，不复用参考视频人物身份 [user_confirmed]

## H3 打包 / 视频状态
- H3 打包: pending (step 9)
- H3 视频生成: skipped (dry-run boundary)
