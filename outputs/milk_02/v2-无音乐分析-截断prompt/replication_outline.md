# 复刻大纲审阅稿：milk_02（shot_structure / 竖屏 9:16 / 15.0s）

- schema_version: `common_replication_outline.v2`
- status: `ready_with_assumptions`
- generation_scope: `single_generation_task`
- 参考视频: `01_reference_video_analysis/reference_video_analysis.json`（1080x1936，15.0s，10 个参考镜头）
- 目标视频: 15.0s，9:16，主体=anonymous Asian young woman generated from the user description (person_entity_1)，场景=seven world-famous landmarks used as rotating backgrounds
- 声音: `unsupported_skipped`（music/bgm/sfx 不参与复刻）

## 目标侧设定

| 项 | 内容 |
| --- | --- |
| 主体 | 匿名亚洲年轻女性：肩长微卷深棕发、自然淡妆、浅色牛仔短外套内搭白色罗纹背心、米色直筒裤、白色低帮鞋 |
| 场景 | 七个世界著名地标轮换背景 |
| 动作 | 抬手比出各种拍照姿势，无手持物 |
| 文字 | 不生成任何可读文字或 logo |

## 参考元素处理决策

| treatment_id | source_ref | decision | target_binding |
| --- | --- | --- | --- |
| `rtp_001` | single-person montage across ten consecutive shots | `inherit` | target_video.structure |
| `rtp_002` | centered front-facing subject who squarely faces the lens | `inherit` | person_entity_1 |
| `rtp_003` | locked-off small-tripod camera | `inherit` | target_video.camera |
| `rtp_004` | fisheye / 360 ultra-wide barrel distortion with foreground magnification | `adapt` | target_video.camera |
| `rtp_005` | pose and composition match cuts between adjacent shots | `inherit` | target_video.editing |
| `rtp_006` | holding an object with both hands and pushing it toward the camera | `adapt` | timeline_units[].temporal_segments[].structured_segment.action_progression |
| `rtp_007` | outfit change on almost every shot | `discard` | person_entity_1.appearance_states |
| `rtp_008` | original props: milk cartons, cake plate, red crab, smiley straw hat, green dumbbell | `discard` | prop_transfer |
| `rtp_009` | bottom-center subtitles and the closing heart graphic | `discard` | post_overlay_plan |
| `rtp_010` | package surface text and brand wording | `discard` | in_scene_text_logo_plan |
| `rtp_011` | staged micro action of opening the package and drinking | `discard` | unit_10.temporal_segments |
| `rtp_012` | revisiting a location across non-adjacent shots (greenhouse twice, gym twice) | `inherit` | scene_entity_3 / scene_entity_5 |
| `rtp_013` | longest sustained beat reserved for the final shot | `inherit` | unit_10 |
| `rtp_014` | near-symmetric background composition with reserved bottom-center space | `inherit` | target_video.composition |
| `rtp_015` | scene rotation across enclosed interior rooms and small venues | `adapt` | scene_appearance |

## 时间轴

### unit_1 · 0.0-3.0s（3.0s）· 参考 shot1
- 目标场景：Eiffel Tower plaza, Paris（`scene_entity_1`）
- 目标姿势：站在画面正中，双手抬到肩膀高度、掌心朝镜头张开，身体正对镜头，嘴角微微上扬
- **seg_1_1** 0.0-0.5s（0.5s）· reference_function=`visual_display` · target_function=`opening_framing_establish` · status=`ready_with_assumptions`
  - 映射：参考视频开场 0.0-0.5s 取景由中景收紧为中近景；目标侧保留同一收紧过程，人物尺度变大，地标背景同步纳入画面
  - 场景：Eiffel Tower plaza, Paris: open stone plaza with the Eiffel Tower rising behind the subject on the visual axis; clipped low hedges and a pale gravel path in the midground; even overcast daylight, pale grey sky, soft even light on the subject; deep background depth with the tower lattice readable far behind her
  - 素材引用：['person_entity_1', 'scene_entity_1']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['To the whole world']
  - 画内实体文字（源侧审计）：['package brand and product text on the carton']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot1', 'source_brand_leak']
- **seg_1_2** 0.5-3.0s（2.5s）· reference_function=`visual_display` · target_function=`pose_hold_and_smile` · status=`ready_with_assumptions`
  - 映射：参考视频在该段保持人物正面手臂稳定、嘴角上扬并叠加字幕；目标侧保留稳定的举手定格与轻微笑意，字幕槽位改为纯画面留白
  - 场景：Eiffel Tower plaza, Paris: open stone plaza with the Eiffel Tower rising behind the subject on the visual axis; clipped low hedges and a pale gravel path in the midground; even overcast daylight, pale grey sky, soft even light on the subject; deep background depth with the tower lattice readable far behind her
  - 素材引用：['person_entity_1', 'scene_entity_1']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['To the whole world']
  - 画内实体文字（源侧审计）：['package brand and product text on the carton']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot1', 'source_brand_leak']

### unit_2 · 3.0-4.0s（1.0s）· 参考 shot2
- 目标场景：Eiffel Tower plaza, Paris（`scene_entity_1`）
- 目标姿势：双臂高举过头顶，向镜头方向张开成一个大框，身体略向前倾
- **seg_2_1** 3.0-4.0s（1.0s）· reference_function=`action_or_interaction` · target_function=`wide_pose_push_toward_lens` · status=`ready_with_assumptions`
  - 映射：参考视频该镜头把物体推到镜头前形成前景放大；目标侧没有手持物，改为双臂高举向镜头张开，让双手成为前景放大主体，保留超广角前景放大的观感
  - 场景：Eiffel Tower plaza, Paris: open stone plaza with the Eiffel Tower rising behind the subject on the visual axis; clipped low hedges and a pale gravel path in the midground; even overcast daylight, pale grey sky, soft even light on the subject; deep background depth with the tower lattice readable far behind her
  - 素材引用：['person_entity_1', 'scene_entity_1']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：["Amway's delicious Gold Classic Fresh"]
  - 画内实体文字（源侧审计）：['package brand and product text on the carton']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot2', 'source_brand_leak']

### unit_3 · 4.0-5.0s（1.0s）· 参考 shot3
- 目标场景：Great Wall of China ridge, Beijing（`scene_entity_2`）
- 目标姿势：单手叉腰，另一只手在脸侧抬起做小幅挥手
- **seg_3_1** 4.0-5.0s（1.0s）· reference_function=`action_or_interaction` · target_function=`pose_change_on_match_cut` · status=`ready_with_assumptions`
  - 映射：参考视频在同姿势下更换服装与道具并切换咖啡馆场景；目标侧保留姿势匹配切与超广角形态，服装保持不变，场景换成长城
  - 场景：Great Wall of China ridge, Beijing: stone rampart and crenellated parapet running diagonally into the distance; mountain ridges layered behind the wall with atmospheric haze; clear late-afternoon daylight with warm low sun and long soft shadows; rough grey stone masonry texture in the foreground wall
  - 素材引用：['person_entity_1', 'scene_entity_2']（usage_role=`merged_reference`）
  - 画内实体文字（源侧审计）：['unreadable yellow signboard lettering on the left']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot3', 'source_brand_leak']

### unit_4 · 5.0-6.0s（1.0s）· 参考 shot4
- 目标场景：Sydney Opera House and Harbour Bridge, Sydney（`scene_entity_3`）
- 目标姿势：双臂高举过头顶张开成大 V 字
- **seg_4_1** 5.0-6.0s（1.0s）· reference_function=`action_or_interaction` · target_function=`wide_open_pose` · status=`ready_with_assumptions`
  - 映射：参考视频该镜头在玻璃顶展厅把纸盒推向镜头；目标侧改为双臂高举成大 V，背景换成悉尼歌剧院与海港大桥
  - 场景：Sydney Opera House and Harbour Bridge, Sydney: white shell roofs of the opera house on one side and the steel arch of the harbour bridge on the other; harbour water with a bright specular sheen in the midground; clear bright blue-sky daylight with crisp contrast; wide open background depth across the water
  - 素材引用：['person_entity_1', 'scene_entity_3']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['INF0.09s ultra-instant sterilization locks in fresh sweetness']
  - 画内实体文字（源侧审计）：['package text on the carton']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot4', 'source_brand_leak']

### unit_5 · 6.0-7.0s（1.0s）· 参考 shot5
- 目标场景：Statue of Liberty and Lower Manhattan skyline, New York（`scene_entity_4`）
- 目标姿势：双手抬到脸前，用双手比出一个取景框
- **seg_5_1** 6.0-7.0s（1.0s）· reference_function=`action_or_interaction` · target_function=`photographer_framing_pose` · status=`ready_with_assumptions`
  - 映射：参考视频该镜头在室外街边把道具推向镜头；目标侧改为在自由女神像与曼哈顿天际线前用双手比出取景框，保留取景手势的前景放大
  - 场景：Statue of Liberty and Lower Manhattan skyline, New York: green copper statue on its stone pedestal behind the subject with the skyline further back; harbour water and a pale stone promenade in the foreground; bright clear daylight with a pale blue sky; strong vertical depth from the promenade to the skyline towers
  - 素材引用：['person_entity_1', 'scene_entity_4']（usage_role=`merged_reference`）
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot5', 'source_brand_leak']

### unit_6 · 7.0-7.5s（0.5s）· 参考 shot6
- 目标场景：Taj Mahal gardens, Agra（`scene_entity_5`）
- 目标姿势：右手抬起在肩侧快速挥动
- **seg_6_1** 7.0-7.5s（0.5s）· reference_function=`visual_display` · target_function=`fast_insert_pose` · status=`ready_with_assumptions`
  - 映射：参考视频该镜头是约 0.5 秒的健身房快速插入；目标侧保留同样时长的快速插入，场景换成泰姬陵，动作改为肩侧快速挥手
  - 场景：Taj Mahal gardens, Agra: white marble mausoleum with its dome and minarets centred behind the subject; long reflecting pool and trimmed garden hedges in the midground; warm golden-hour daylight with soft haze; symmetrical background layout with a mirrored pool reflection
  - 素材引用：['person_entity_1', 'scene_entity_5']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['Jindian Xianhuo pure milk']
  - 画内实体文字（源侧审计）：['orange wall lettering and package text']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot6', 'source_brand_leak']

### unit_7 · 7.5-8.5s（1.0s）· 参考 shot7
- 目标场景：Sydney Opera House and Harbour Bridge, Sydney（`scene_entity_3`）
- 目标姿势：手抬到脸颊旁做飞吻手势
- **seg_7_1** 7.5-8.0s（0.5s）· reference_function=`action_or_interaction` · target_function=`repeat_location_pose_beat` · status=`ready_with_assumptions`
  - 映射：参考视频回到温室并更换道具；目标侧回到悉尼歌剧院，保留回访同一地点的重复机制，改为脸颊旁飞吻手势
  - 场景：Sydney Opera House and Harbour Bridge, Sydney: white shell roofs of the opera house on one side and the steel arch of the harbour bridge on the other; harbour water with a bright specular sheen in the midground; clear bright blue-sky daylight with crisp contrast; wide open background depth across the water
  - 素材引用：['person_entity_1', 'scene_entity_3']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['Tastes so good you want to have it every moment']
  - 画内实体文字（源侧审计）：['smiley-face graphic printed on the straw hat']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot7', 'source_brand_leak']
- **seg_7_2** 8.0-8.5s（0.5s）· reference_function=`action_or_interaction` · target_function=`gesture_hold` · status=`ready_with_assumptions`
  - 映射：参考视频在该段轻微左右调整物体角度；目标侧保留小幅手势调整并保持定格
  - 场景：Sydney Opera House and Harbour Bridge, Sydney: white shell roofs of the opera house on one side and the steel arch of the harbour bridge on the other; harbour water with a bright specular sheen in the midground; clear bright blue-sky daylight with crisp contrast; wide open background depth across the water
  - 素材引用：['person_entity_1', 'scene_entity_3']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['Tastes so good you want to have it every moment']
  - 画内实体文字（源侧审计）：['smiley-face graphic printed on the straw hat']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot7', 'source_brand_leak']

### unit_8 · 8.5-9.5s（1.0s）· 参考 shot8
- 目标场景：Taj Mahal gardens, Agra（`scene_entity_5`）
- 目标姿势：双臂上举过头、十指交叉做伸展动作
- **seg_8_1** 8.5-9.5s（1.0s）· reference_function=`action_or_interaction` · target_function=`overhead_stretch_pose` · status=`ready_with_assumptions`
  - 映射：参考视频在健身房把哑铃举过头顶；目标侧改为双臂上举十指交叉伸展，保留头顶上方放大的构图机制，场景换成泰姬陵回访
  - 场景：Taj Mahal gardens, Agra: white marble mausoleum with its dome and minarets centred behind the subject; long reflecting pool and trimmed garden hedges in the midground; warm golden-hour daylight with soft haze; symmetrical background layout with a mirrored pool reflection
  - 素材引用：['person_entity_1', 'scene_entity_5']（usage_role=`merged_reference`）
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot8', 'source_brand_leak']

### unit_9 · 9.5-11.0s（1.5s）· 参考 shot9
- 目标场景：Colosseum exterior, Rome（`scene_entity_6`）
- 目标姿势：双臂向身体两侧完全张开做展示姿势
- **seg_9_1** 9.5-10.5s（1.0s）· reference_function=`visual_display` · target_function=`wide_presentation_pose` · status=`ready_with_assumptions`
  - 映射：参考视频在广场把产品推向镜头；目标侧改为双臂侧向张开的展示姿势，背景换成罗马斗兽场，保留超广角对建筑弧线的拉伸
  - 场景：Colosseum exterior, Rome: curved tiers of the stone amphitheatre arches filling the background; warm travertine paving and scattered stone blocks in the foreground; warm late-afternoon daylight with golden tone and soft shadow; strong curved architectural depth wrapping around the frame
  - 素材引用：['person_entity_1', 'scene_entity_6']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['Jindian Xianhuo pure milk']
  - 画内实体文字（源侧审计）：['package text on the carton']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot9', 'source_brand_leak']
- **seg_9_2** 10.5-11.0s（0.5s）· reference_function=`visual_display` · target_function=`pose_hold` · status=`ready_with_assumptions`
  - 映射：参考视频在该段保持推向镜头的定格；目标侧保持双臂张开的定格并轻微抬眼
  - 场景：Colosseum exterior, Rome: curved tiers of the stone amphitheatre arches filling the background; warm travertine paving and scattered stone blocks in the foreground; warm late-afternoon daylight with golden tone and soft shadow; strong curved architectural depth wrapping around the frame
  - 素材引用：['person_entity_1', 'scene_entity_6']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['Jindian Xianhuo pure milk']
  - 画内实体文字（源侧审计）：['package text on the carton']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot9', 'source_brand_leak']

### unit_10 · 11.0-15.0s（4.0s）· 参考 shot10
- 目标场景：Mount Fuji with Chureito Pagoda, Fujiyoshida（`scene_entity_7`）
- 目标姿势：分三段推进：双手在胸前比取景框、双手在胸前比心、最后双臂高举做大挥手
- **seg_10_1** 11.0-12.0s（1.0s）· reference_function=`action_or_interaction` · target_function=`closing_stage_one_framing` · status=`ready_with_assumptions`
  - 映射：参考视频该段双手举两盒产品面向镜头；目标侧改为双手在胸前比出取景框，保留双手向镜头举起的起势
  - 场景：Mount Fuji with Chureito Pagoda, Fujiyoshida: snow-capped Mount Fuji centred in the far background; red multi-tiered pagoda and cherry-tree branches framing the background; clear crisp daylight with a deep blue sky and clean colour separation; layered depth from foreground branches to the mountain
  - 素材引用：['person_entity_1', 'scene_entity_7']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['Tastes so good you want to have it every moment', 'red heart emoji at the end of the subtitle line']
  - 画内实体文字（源侧审计）：['package text on the cartons']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot10', 'source_brand_leak']
- **seg_10_2** 12.0-13.0s（1.0s）· reference_function=`action_or_interaction` · target_function=`closing_stage_two_heart_gesture` · status=`ready_with_assumptions`
  - 映射：参考视频该段打开盒口并开始出现字幕与爱心图形；目标侧改为双手比心手势，保留该段的手势停顿节奏，不生成任何图形叠加
  - 场景：Mount Fuji with Chureito Pagoda, Fujiyoshida: snow-capped Mount Fuji centred in the far background; red multi-tiered pagoda and cherry-tree branches framing the background; clear crisp daylight with a deep blue sky and clean colour separation; layered depth from foreground branches to the mountain
  - 素材引用：['person_entity_1', 'scene_entity_7']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['Tastes so good you want to have it every moment', 'red heart emoji at the end of the subtitle line']
  - 画内实体文字（源侧审计）：['package text on the cartons']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot10', 'source_brand_leak']
- **seg_10_3** 13.0-15.0s（2.0s）· reference_function=`closing_or_prompt` · target_function=`closing_final_wave_hold` · status=`ready_with_assumptions`
  - 映射：参考视频以仰头饮用并保持数秒收尾；目标侧改为双臂高举的大挥手并保持定格作为收尾，保留结尾最长停留节拍
  - 场景：Mount Fuji with Chureito Pagoda, Fujiyoshida: snow-capped Mount Fuji centred in the far background; red multi-tiered pagoda and cherry-tree branches framing the background; clear crisp daylight with a deep blue sky and clean colour separation; layered depth from foreground branches to the mountain
  - 素材引用：['person_entity_1', 'scene_entity_7']（usage_role=`merged_reference`）
  - 后期叠加（不生成）：['Tastes so good you want to have it every moment', 'red heart emoji at the end of the subtitle line']
  - 画内实体文字（源侧审计）：['package text on the cartons']
  - 机制：['special_camera_or_focus', 'special_composition', 'special_transition']
  - 审计项：['source_prop_shot10', 'source_brand_leak']

## 记忆点迁移

| memory_id | 保留机制 | 目标绑定 |
| --- | --- | --- |
| `vm_001` | extreme foreground framing；subject centered behind the foreground element | unit_2, unit_3, unit_4, unit_5, unit_6, unit_7, unit_8, unit_9 |
| `vm_002` | locked-off camera；ultra-wide distorted perspective；foreground magnification | unit_2, unit_3, unit_4, unit_5, unit_6, unit_7, unit_8, unit_9, unit_10 |
| `vm_003` | pose match cut；composition match cut；location change on the cut | unit_2, unit_3, unit_4, unit_5, unit_6, unit_7, unit_8 |
| `vm_004` | staged multi-step closing micro action；sustained final beat；hand path toward a target point | unit_10 |
| `vm_005` | centered near-symmetric hero framing；reserved bottom-center text safe area | unit_1, unit_9, unit_10 |
| `sm_001` | single-person opening；held gesture display；bottom information slot | unit_1 |
| `sm_002` | one location per shot；repeated pose；per-shot bottom information slot | unit_2, unit_3, unit_4, unit_5, unit_6, unit_7, unit_8, unit_9 |
| `sm_003` | display-to-payoff transition；staged closing action | unit_10 |
| `sm_004` | closing benefit slot；held final beat；warm graphic accent | unit_10 |

## 全局外观库（去重后）

| entity_id | type | 说明 | 引用镜头 |
| --- | --- | --- | --- |
| `person_entity_1` | person | Asian young woman in her mid twenties, slim average build；shoulder-length softly wavy dark brown hair with a side part | unit_1, unit_2, unit_3, unit_4, unit_5, unit_6, unit_7, unit_8, unit_9, unit_10 |
| `scene_entity_1` | scene | open stone plaza with the Eiffel Tower rising behind the subject on the visual axis；clipped low hedges and a pale gravel path in the midground | unit_1, unit_2 |
| `scene_entity_2` | scene | stone rampart and crenellated parapet running diagonally into the distance；mountain ridges layered behind the wall with atmospheric haze | unit_3 |
| `scene_entity_3` | scene | white shell roofs of the opera house on one side and the steel arch of the harbour bridge on the other；harbour water with a bright specular sheen in the midground | unit_4, unit_7 |
| `scene_entity_4` | scene | green copper statue on its stone pedestal behind the subject with the skyline further back；harbour water and a pale stone promenade in the foreground | unit_5 |
| `scene_entity_5` | scene | white marble mausoleum with its dome and minarets centred behind the subject；long reflecting pool and trimmed garden hedges in the midground | unit_6, unit_8 |
| `scene_entity_6` | scene | curved tiers of the stone amphitheatre arches filling the background；warm travertine paving and scattered stone blocks in the foreground | unit_9 |
| `scene_entity_7` | scene | snow-capped Mount Fuji centred in the far background；red multi-tiered pagoda and cherry-tree branches framing the background | unit_10 |
| `style_atmosphere_1` | style_atmosphere | bright clean daylight across all ten locations；medium contrast with saturated sky and stone | unit_1, unit_2, unit_3, unit_4, unit_5, unit_6, unit_7, unit_8, unit_9, unit_10 |

## 参考帧摘要

- plan_required=`True`，人物实体=1，场景实体=7，计划帧数=8，H3 图片预算=8，合并帧=0
- triggered_rules: ['person_reference_entity_present', 'scene_reference_entity_present']
- plan_path: `07_reference_frame_plan/reference_frame_plan.json`

## 文字与 logo 策略

- `post_overlay_default`: True
- `in_scene_allowed_when_physically_attached`: True
- `render_post_overlay_in_video_model`: False
- `post_overlay_render_method`: ffmpeg_or_opencv
- `do_not_generate_unconfirmed_readable_text`: True
- `target_readable_text_status`: missing_required_input
- `resolution`: no readable text or logo is generated in the target video

## 缺失项与假设

- `mi_001` scene：status=`missing_generate_fallback`，resolution_policy=`generate_with_confirmed_assumption`
- `mi_002` actor_identity：status=`missing_generate_fallback`，resolution_policy=`generate_with_confirmed_assumption`
- `mi_003` dialogue_or_on_screen_text：status=`neutralize_allowed`，resolution_policy=`omit_or_neutralize`
- `ga_001` actor_identity：anonymous non-identifiable Asian young woman generated from the user description
- `ga_002` scene：seven world-famous landmarks generated from the user description
- `ga_003` dialogue_or_on_screen_text：no readable target text or logo is generated

## 验证标记

- `reference_analysis_partial_from_truncated_vlm_answer`
- `target_subject_and_scene_are_generation_assumptions`
- `no_target_text_so_all_reference_text_is_audit_only`
- `script_profile_directory_empty_skipped`
- `outfit_rotation_discarded_to_keep_one_consistent_target_look`
