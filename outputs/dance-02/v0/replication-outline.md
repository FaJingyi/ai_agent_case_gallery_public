# 复刻大纲审阅稿

- schema_version: `common_replication_outline.v2`  |  status: `ready_with_assumptions`
- generation_scope: `single_generation_task`  |  时间精度: 截断到 1 位小数
- 参考视频: 2_2_case2-H3-original.mp4 (768x1344, 10.1s)
- 目标视频: 10.1 秒竖屏 9:16 单镜头连续镜头：一只穿蓝色牛仔背带裤的大卡通公鸡在画面中央持续跳舞，摄影机完全锁定，全景居中构图；背景在节奏点原地切换为三个 2D 漫画城市场景（篮球场、街头、公园）。
- 目标风格来源: `user_explicit` / `2D comic`

## 两层继承摘要

**强继承项**
- `si_time_structure` (time_structure): 单个连续镜头，时长约 10.1 秒，无剪辑、无空镜铺垫，直接从表演开始。 -> 目标视频保持 10.1 秒单镜头结构与直接开场。
- `si_shot_order` (shot_structure): 仅一个 shot，无镜头顺序变化。 -> 目标视频仍为一个 continuous shot，不拆成多镜头。
- `si_shot_size` (composition): 全景（Full Shot），主体从头到脚可见，保留周围环境。 -> 保持全景，公鸡完整入画且地面与背景同时可读。
- `si_centered_composition` (composition): 中心构图，主体位于画面中央竖直条带，左右留白适中。 -> 公鸡始终位于画面中央竖直条带，左右保留适度负空间。
- `si_camera_angle` (camera): 平视、略微偏低的机位角度，正面朝向主体。 -> 保持平视略低的正面机位。
- `si_static_camera` (camera): 完全静止的锁定机位，无横摇、无变焦、无焦点变化。 -> 摄影机全程锁定，不移动、不变焦、不移焦。
- `si_focus_behavior` (camera): 固定焦点对准主体，主体与背景都保持可读。 -> 保持固定焦点与深焦可读性，主体与背景都清晰。
- `si_beat_structure` (time_structure): 连续不间断的动作链，约每秒一个动作单元，无停顿，3.0s 与 6.0s 附近有换脚/转身强调点。 -> 保持连续不间断、无停顿的舞蹈节拍结构，并在 3.0s、6.0s 的节奏强调点发生背景切换。
- `si_form_memory_point` (shot_structure): 形式型记忆点：无铺垫直接进入表演，并以单一长镜头完整保留动作链。 -> 目标视频同样以单一连续长镜头直接进入公鸡舞蹈，不添加开场镜头或结尾卡。

**参考继承项**
- `ri_subject_motion_pattern` (subject_motion_pattern): 参考主体为人物，动作是持续交替的舞步链。 -> 改写为公鸡舞蹈语汇，只迁移抽象节拍结构。
- `ri_subject_identity_and_costume` (subject_content): 参考主体是连帽衫、短裤、白鞋的人物。 -> 替换为用户指定的穿背带裤的大公鸡。
- `ri_scene_content` (scene_content): 参考场景是室外水泥球场，米色墙、红色看台、灯杆、阴天。 -> 按用户要求替换为三个 2D 漫画城市场景：篮球场、街头、公园。
- `ri_visual_style` (visual_style): 参考画面是写实实拍，柔和的阴天自然光。 -> 按用户要求切换为 2D 漫画风格；保留均匀、明亮、无硬阴影的光线关系。
- `ri_script_memory_point` (dialogue_or_voiceover): 参考视频有 ASR 识别到的英文歌词式人声（voiceover），属疑似唱歌。 -> 不迁移声音文本与唱歌内容；目标视频无台词、无旁白、无口型。

**降级项**
- 无

## 参考元素处理计划

| element_id | type | layer | decision | 目标绑定 |
| --- | --- | --- | --- | --- |
| `el_time_structure` | time_structure | strong_inheritance | `inherit` | unit_001, seg_001, seg_002, seg_003 |
| `el_shot_structure` | shot_structure | strong_inheritance | `inherit` | unit_001 |
| `el_viewpoint_and_composition` | composition | strong_inheritance | `inherit` | unit_001, seg_001, seg_002, seg_003 |
| `el_camera_motion_static` | camera | strong_inheritance | `inherit` | unit_001 |
| `el_focus_behavior` | camera | strong_inheritance | `inherit` | unit_001 |
| `el_action_beat_structure` | action_beat_structure | strong_inheritance | `inherit` | unit_001, seg_001, seg_002, seg_003 |
| `el_subject_motion_pattern` | subject_motion_pattern | reference_inheritance | `adapt` | seg_001, seg_002, seg_003 |
| `el_subject_content_person` | subject_content | reference_inheritance | `adapt` | entity_subject_rooster |
| `el_scene_content_court` | scene_content | reference_inheritance | `adapt` | entity_scene_basketball, entity_scene_street, entity_scene_park |
| `el_visual_style_realism` | visual_style | reference_inheritance | `adapt` | entity_style_atmosphere |
| `el_voiceover_lyric` | dialogue_or_voiceover | reference_inheritance | `discard` | unit_001 |
| `el_reference_audio` | unsupported_audio | discard_only | `discard` | unit_001 |
| `el_text_ui_absence` | text_or_ui | strong_inheritance | `inherit` | seg_001, seg_002, seg_003 |
| `el_reference_person_identity` | person_or_body | discard_only | `discard` | unit_001 |

## 全局外观库（第二层去重后）

- `entity_subject_rooster` (main_subject_appearance) 穿蓝色牛仔背带裤的大卡通公鸡；引用段落: seg_001, seg_002, seg_003
  - 2D 漫画风格，粗黑描边，平涂色块，简化图形化阴影
  - 体型偏大的公鸡，直立站姿，比例圆润
  - 红色鸡冠与肉垂，橙黄色尖喙
  - 金棕色身体羽毛，分层块面化排列
  - 深绿黑色拱形尾羽
  - 粗壮的橙黄色腿与爪，脚趾分明
  - 蓝色牛仔背带裤：前胸袋、两条肩带与金属扣、短裤腿口，露出羽毛大腿
- `entity_scene_basketball` (scene_appearance) 2D 漫画城市篮球场；引用段落: seg_001
  - 粗描边、平涂色块的铁丝网围栏与篮板篮筐
  - 地面有清晰的白色球场线
  - 远处简化的城市楼房
  - 明亮均匀的光线，柔和阴影
  - 空间层次简单：地面前景、主体中景、背景平铺
- `entity_scene_street` (scene_appearance) 2D 漫画城市街头；引用段落: seg_002
  - 粗描边、平涂色块的临街店铺与雨棚
  - 路灯、道路与斑马线、人行道
  - 远处城市楼房
  - 明亮均匀的光线，柔和阴影
- `entity_scene_park` (scene_appearance) 2D 漫画城市公园；引用段落: seg_003
  - 粗描边、平涂色块的造型化树木
  - 长椅、铺装步道与草坪
  - 远处城市天际线
  - 明亮均匀的光线，柔和阴影
- `entity_style_atmosphere` (style_atmosphere) 2D 漫画城市日光氛围；引用段落: seg_001, seg_002, seg_003
  - 2D 漫画 / 平面插画方向（用户显式指定）
  - 粗黑描边、平涂色块、简化图形化阴影
  - 明亮均匀的日光、低到中等对比、无硬阴影
  - 明快、有活力的氛围

## 时间轴

### unit `unit_001` (video_shot) 0.0-10.1s / 10.1s

#### `seg_001` 0.0-3.0s (3.0s)  status=`ready_with_assumptions`
- 参考功能 -> 目标功能: `action_or_interaction` -> `action_or_interaction`
- 视角: 平视、略低机位、正面
- 构图: 竖屏 9:16 全景; 中心构图，主体位于中央竖直条带; 篮球场背景平铺于主体正后方; 左右保留适度负空间
- 运镜: 完全静止锁定机位
- 场景迁移: 2D 漫画风格城市篮球场：粗描边、平涂色块的铁丝网围栏与篮板篮筐，地面有清晰的白色球场线，远处是简化的城市楼房；整体明快、阴影柔和。
- 主体/动作迁移: None；None
- 主体运动迁移: mode=`beat_structure_only`
- 画面内实体文字/logo: 无
- 台词/旁白/画面文字迁移: {"kind": "none", "target_text_item_ids": [], "note": "no_confirmed_speech"}
- 后期叠加: 无
- 参考帧决策: entities=entity_subject_rooster, entity_scene_basketball, frame_mode=`entity_single_state`
- 缺失输入: 无
- 状态: `ready_with_assumptions`

#### `seg_002` 3.0-6.0s (3.0s)  status=`ready_with_assumptions`
- 参考功能 -> 目标功能: `action_or_interaction` -> `action_or_interaction`
- 视角: 平视、略低机位、正面
- 构图: 竖屏 9:16 全景; 中心构图不变; 街头背景平铺于主体正后方; 构图在切换前后完全一致
- 运镜: 完全静止锁定机位，切换时仍不移动
- 场景迁移: 2D 漫画风格城市街头：粗描边、平涂色块的临街店铺与雨棚，路灯、道路与斑马线、人行道和远处楼房；色调明快，阴影柔和。
- 主体/动作迁移: None；None
- 主体运动迁移: mode=`beat_structure_only`
- 画面内实体文字/logo: 无
- 台词/旁白/画面文字迁移: {"kind": "none", "target_text_item_ids": [], "note": "no_confirmed_speech"}
- 后期叠加: 无
- 参考帧决策: entities=entity_subject_rooster, entity_scene_street, frame_mode=`entity_single_state`
- 缺失输入: 无
- 状态: `ready_with_assumptions`

#### `seg_003` 6.0-10.1s (4.1s)  status=`ready_with_assumptions`
- 参考功能 -> 目标功能: `action_or_interaction` -> `closing_or_prompt`
- 视角: 平视、略低机位、正面
- 构图: 竖屏 9:16 全景; 中心构图不变; 公园背景平铺于主体正后方; 构图与切换前完全一致
- 运镜: 完全静止锁定机位
- 场景迁移: 2D 漫画风格城市公园：粗描边、平涂色块的造型化树木，长椅、铺装步道、草坪与远处城市天际线；色调明快，阴影柔和。
- 主体/动作迁移: None；None
- 主体运动迁移: mode=`beat_structure_only`
- 画面内实体文字/logo: 无
- 台词/旁白/画面文字迁移: {"kind": "none", "target_text_item_ids": [], "note": "no_confirmed_speech"}
- 后期叠加: 无
- 参考帧决策: entities=entity_subject_rooster, entity_scene_park, frame_mode=`entity_single_state`
- 缺失输入: 无
- 状态: `ready_with_assumptions`

## 记忆点迁移

- `vm_001` (micro_action) 保留: 单一锁定全景镜头内连续不间断的舞蹈动作链, 交替抬腿/换脚/重心转换的节拍结构, 开合手势在收拢与张开之间交替的节奏, 完整保留动作链、主体全程不出的全景取景
- `sm_001` (opening_hook) 保留: 无铺垫、无标题、无上下文镜头，直接进入表演, 以一个连续长镜头完成整段内容，不使用剪辑

## 语音/文本迁移
- speech_status: `no_confirmed_speech`
- target_text_items: 0 项
  - 移除 `removed_voiceover_lyric`: reference_audio_is_suspected_singing_song_lyric_unsupported_and_no_user_target_text
  - 移除 `removed_screen_text`: no_reference_screen_text_and_no_user_text_input

## 参考帧摘要
- plan_required: `True`
- person_entity_count: `0`
- subject_entity_count: `1`
- scene_entity_count: `3`
- state_frame_count: `0`
- planned_frame_count: `4`
- selected_h3_image_count: `4`
- merged_frame_count: `0`
- h3_image_budget: `8`
- plan_path: `07_reference_frame_plan/reference_frame_plan.json`
- summary_status: `ready`
- triggered_rules: `['subject_reference_entity_present', 'scene_reference_entity_present']`

## 缺失项与生成假设
- missing_inputs: ['miss_primary_subject_asset', 'miss_scene_asset']
- generation_assumptions: ['asm_subject_appearance', 'asm_scene_basketball_court', 'asm_scene_street', 'asm_scene_park', 'asm_rooster_dance']
- validation_flags: ['single_reference_shot', 'no_user_assets_provided', 'user_explicit_2d_comic_style', 'user_explicit_scene_override_three_city_scenes', 'subject_motion_transfer_mode=beat_structure_only', 'single_take_with_in_place_background_swaps', 'no_speech_no_text_no_logo', 'reference_frames_required_for_subject_and_scenes']
