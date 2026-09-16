# 复刻大纲审阅稿

- 状态: `ready_with_assumptions`
- 生成范围: `single_generation_task`
- 时间精度: `one_decimal` / `truncate`
- 参考视频: `test_data/minimax/minimax.mp4`（15.0s，2560x1440，24fps，引用前 15 秒截断版本）
- 目标视频: 15.0s / 2560x1440 / 16:9 / 4 镜 / 6 个 temporal segment
- 复刻模式: `shot_structure`，scene_threshold = 0.5

## 时间轴总览

| 镜 | 时间 | 参考功能 | 目标功能 | 主体 | 场景迁移 | 画内实体文字 | 后期叠加 | 参考帧 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | 0.0-4.5s | visual_display | action_or_interaction | 青蓝滨水广场玻璃亭上的 MetaX 字标（rb_brand 目标实体） | ent_scene_pavilion | 已确认 MetaX | 标注待补/安全区 | rf_scene_01 | mi_annotation_text | ready |
| 2 | 4.5-8.5s | visual_display | visual_display | 建筑立面悬挂布旗上的竖排 MetaX 字标 | ent_scene_facade | 已确认 MetaX | 标注待补/安全区 | rf_scene_02 | mi_annotation_text | ready |
| 3 | 8.5-11.9s | action_or_interaction | action_or_interaction | 猫咪 猫咪（rb_model 目标实体） | ent_scene_rooftop | 已确认 MetaX | 标注待补/安全区 | rf_person_01,rf_scene_03 | mi_annotation_text,mi_cat_reference | ready |
| 4 | 11.9-15.0s | action_or_interaction | action_or_interaction | 猫咪 猫咪面部与红色太阳镜 | ent_scene_rooftop | 已确认 MetaX | 标注待补/安全区 | rf_person_01,rf_scene_03 | mi_cat_reference,mi_dialogue_text | ready |

## 分镜明细

### 镜1  0.0-4.5s  (`unit_001` / `shot1`)

- 参考功能: `opening_hook_reveal`；目标功能: `opening_hook_reveal`
- 生成画面: 移焦揭示公共空间中出现的品牌字标
- 主体/动作迁移: 模糊->清晰合焦->保持
- 场景迁移: 青蓝黄昏滨水广场，玻璃亭与金属栏杆，主色青蓝
- 运镜/构图: 中景建立镜头；双圆遮罩聚焦；缓慢推近；移焦合焦
- 转场: 无切换，开场移焦

| 内部节拍 | 时间 | 参考功能 | 目标功能 | 生成画面 | 动作/运镜 | 文字/叠加 | 参考帧 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `seg_001A` | 0.0-2.0s | visual_display | action_or_interaction | 开场失焦到合焦，MetaX 字标由虚转实 | 画面由整体失焦快速合焦，玻璃亭顶棚字标由虚转实 | 画内文字: ready / 叠加: missing_required_input | rf_scene_01 | mi_annotation_text | ready |
| `seg_001B` | 2.0-4.5s | visual_display | visual_display | 字标保持清晰，投影呈现 | 焦点保持清晰，亭顶字标稳定可见，幕墙上字标投影随之清晰 | 画内文字: ready / 叠加: missing_required_input | rf_scene_01 | mi_annotation_text | ready |

**特殊机制**

- `sm_mask` (special_composition, whole_video): The entire frame is viewed through a black heart-shaped mask made of two overlapping circular apertures, with a narrow notch at the top center and the subject centered inside the circles.
- `sm_rack` (special_camera_or_focus, shot1 0.0-2.0s): The shot starts fully out of focus and quickly racks into sharp focus on the MetaX wordmark on the pavilion canopy.

### 镜2  4.5-8.5s  (`unit_002` / `shot2`)

- 参考功能: `information_progression`；目标功能: `information_progression`
- 生成画面: 字标以布质旗帜出现在建筑立面
- 主体/动作迁移: 交叉淡化进入->旗帜摆动保持
- 场景迁移: 青蓝黄昏高楼立面，冷调天空
- 运镜/构图: 远景仰拍；旗帜居中偏左；轻微位移；深景深
- 转场: 由 shot1 交叉淡化进入

| 内部节拍 | 时间 | 参考功能 | 目标功能 | 生成画面 | 动作/运镜 | 文字/叠加 | 参考帧 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `seg_002A` | 4.5-8.5s | visual_display | visual_display | 交叉淡化进入建筑旗帜镜头，MetaX 竖排字标 | 布质长旗随风摆动，旗面竖排字标随之起伏 | 画内文字: ready / 叠加: missing_required_input | rf_scene_02 | mi_annotation_text | ready |

**特殊机制**

- `sm_mask` (special_composition, whole_video): The entire frame is viewed through a black heart-shaped mask made of two overlapping circular apertures, with a narrow notch at the top center and the subject centered inside the circles.
- `sm_cross` (special_transition, shot1->shot2 ~4.5s): The pavilion shot crossfades over about half a second into the building facade with the hanging banner.

### 镜3  8.5-11.9s  (`unit_003` / `shot3`)

- 参考功能: `human_anchor`；目标功能: `human_anchor`
- 生成画面: 猫咪出现并与品牌字标同框
- 主体/动作迁移: 站立->缓慢行走并低头
- 场景迁移: 青蓝滨水广场，身后石墙上巨大 MetaX 字标
- 运镜/构图: 中景低角度；主体左侧三分之一；基本静止；中景清晰背景略虚
- 转场: 硬切进入

| 内部节拍 | 时间 | 参考功能 | 目标功能 | 生成画面 | 动作/运镜 | 文字/叠加 | 参考帧 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `seg_003A` | 8.5-11.9s | action_or_interaction | action_or_interaction | 猫咪在墙面 MetaX 字标前缓慢行走并低头看向项圈相机 | 猫咪在矮墙前缓慢行走并低头看向胸前的项圈相机 | 画内文字: ready / 叠加: missing_required_input | rf_person_01,rf_scene_03 | mi_cat_reference,mi_annotation_text | ready |

**特殊机制**

- `sm_mask` (special_composition, whole_video): The entire frame is viewed through a black heart-shaped mask made of two overlapping circular apertures, with a narrow notch at the top center and the subject centered inside the circles.

### 镜4  11.9-15.0s  (`unit_004` / `shot4`)

- 参考功能: `closing_reveal`；目标功能: `closing_reveal`
- 生成画面: 猫咪面部大特写，抬起前爪扶红色太阳镜后放下，镜片反射 MetaX 字标
- 主体/动作迁移: 抬爪->扶镜停留->放下
- 场景迁移: 青蓝黄昏虚化背景
- 运镜/构图: 面部大特写；紧凑特写；基本静止；浅景深，镜片反射清晰
- 转场: 硬切进入，片尾

| 内部节拍 | 时间 | 参考功能 | 目标功能 | 生成画面 | 动作/运镜 | 文字/叠加 | 参考帧 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `seg_004A` | 11.9-13.5s | action_or_interaction | action_or_interaction | 猫咪抬前爪扶红色太阳镜并停留 | 猫咪抬起前爪扶一下红色太阳镜，随后放下 | 画内文字: 无 / 叠加: missing_required_input | rf_person_01,rf_scene_03 | mi_cat_reference,mi_dialogue_text | ready |
| `seg_004B` | 13.5-15.0s | visual_display | visual_display | 前爪放下，镜片内反射 MetaX 字标揭示 | 镜片表面显现建筑字标的倒影，完成收尾信息揭示 | 画内文字: ready / 叠加: missing_required_input | rf_person_01,rf_scene_03 | mi_dialogue_text | ready |

**特殊机制**

- `sm_mask` (special_composition, whole_video): The entire frame is viewed through a black heart-shaped mask made of two overlapping circular apertures, with a narrow notch at the top center and the subject centered inside the circles.
- `sm_refl` (special_composition, shot4 13.0-15.0s): Inside the left sunglass lens, the MetaX wordmark on the building is reflected as a small mirrored sign as the cat adjusts the glasses.

## 全局外观库

| 实体 | 类型 | 关键外观 | 绑定单元/节拍 | 合并状态 |
| --- | --- | --- | --- | --- |
| 猫咪演员 (`ent_actor_cat`) | `person_appearance` | 短毛家猫，体态修长轻盈，站立时肩高约到中景画面下部三分之一；银灰色虎斑短毛，胸口与口鼻处为浅色，耳内淡粉，鼻头浅粉 | unit_003,unit_004 | `single_entity_merged_across_units` |
| 滨水广场玻璃亭 (`ent_scene_pavilion`) | `scene_appearance` | 白色金属框架玻璃亭（候车廊），亭顶前沿为银白色立体字标载体；亭侧为整片玻璃幕墙，幕墙上落有字标投影 | unit_001 | `single_entity_merged_across_segments` |
| 建筑立面布旗 (`ent_scene_facade`) | `scene_appearance` | 米白色高层建筑外立面，外挑一排白色布质长旗；旗面竖排目标品牌字标，旗内侧为暗红色 | unit_002 | `separate_entity_distinct_space` |
| 滨水建筑屋顶矮墙 (`ent_scene_rooftop`) | `scene_appearance` | 滨水建筑屋顶平台，主体身后是一段低矮混凝土矮墙；矮墙表面有大型目标品牌字标，字标被主体与遮罩缺口部分遮挡 | unit_003,unit_004 | `separate_entity_distinct_space` |
| MetaX 字标 (`ent_brand_metax`) | `main_subject_appearance` | 可读文字为精确字符串 MetaX，来源为用户文本；无衬线几何字形，字重偏粗，字间距略宽 | unit_001,unit_002,unit_003,unit_004 | `single_entity_merged_across_units` |
| 红色镜框太阳镜 (`ent_prop_sunglasses`) | `key_prop_appearance` | 红色细边镜框，猫脸尺寸，镜腿贴合猫头两侧；镜片为浅茶色半反射镜面，可映出环境高光与建筑字标倒影 | unit_004 | `single_entity_merged_across_segments` |
| 项圈迷你相机 (`ent_prop_collar_camera`) | `key_prop_appearance` | 暗红色细项圈，宽度窄，贴合猫颈；项圈侧固定一枚哑光黑迷你相机，体积小、圆形镜头朝前 | unit_003 | `single_entity_single_segment` |
| 冷青黄昏氛围 (`ent_style_bluehour`) | `style_atmosphere` | 青蓝黄昏自然侧光，低角度长阴影，湿润地面与水面形成反光；冷青主色，少量暖橙高光对比，饱和度克制 | unit_001,unit_002,unit_003,unit_004 | `single_atmosphere_entity` |

## 审计与缺口

- 目标主体: 猫咪为生成假设（用户未提供猫咪素材），已写入可见差异锚点
- 目标品牌文字: `MetaX`，来源用户文本，作为画内实体文字进入分镜描述
- 画外红色观察标注: 目标文案缺失，仅保留位置与安全区，由后期叠加
- 台词/口播: 源侧仅一句低置信度英文台词，目标侧未提供台词，按可见表情与动作处理
- 音乐/BGM/音效/唱歌/声音情绪/卡点: `unsupported_skipped`
- 源侧审计项: 源品牌名、源字标文字、源标注文案、源地标身份、源人物身份只保留在审计层

## 参考帧摘要

- `frame_requirement_level`: `required_person_scene_anchors`
- 人物实体数: 1；场景实体数: 3；计划参考帧数: 4
- 计划路径: `07_reference_frame_plan/reference_frame_plan.json`

