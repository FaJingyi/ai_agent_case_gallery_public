# 复刻大纲审阅稿：户外草坪机器狗遥控动作复刻

- schema_version: `common_replication_outline.v2`
- status: `ready_with_assumptions`
- generation_scope: `single_generation_task`
- 目标时长/画幅: `5.8s` / `16:9` (`1344x768`)
- 时间精度: `one_decimal` / `truncate`
- timeline_unit_count: 1；temporal_segment_count: 6
- 下游 H3 prompt 的 prompt-level shot 与参考视频的 reference-level shot 可能不一致，最终交付会分别说明。

## 目标世界摘要

- 主体：三只外观一致的机器狗（浅灰哑光机壳、银色金属关节、背部圆柱激光雷达、黑色传感器面板、四足细腿黑色脚垫）
- 人物：一名中性、不可识别的操作者，深色短袖上衣与深色长裤，手持小型手持遥控器
- 场景：outdoor park lawn: trimmed green grass, low hedges and trees in the mid background, bright natural daylight, open sky, soft natural shadows; a plain neutral ground with no painted markings

## 参考元素处理计划

| element_id | 类型 | 处理 | 保留 / 改编 / 丢弃 |
| --- | --- | --- | --- |
| el_001_time_structure | time_structure | `inherit` | 保留: 完整时长与单一连续镜头结构；由动作阶段决定节奏 · 改编: - · 丢弃: - |
| el_002_shot_structure | shot_structure | `inherit` | 保留: 全景开场到中近景的取景变化；正面偏侧略高的机位关系；主体横向排列的画面重心 · 改编: - · 丢弃: - |
| el_003_camera_slow_push_in | camera | `inherit` | 保留: 推近起止时间（约 2.8s 起）与方向（向主体推进）；主体尺度连续增大；前景人物随推近逐步出画 · 改编: - · 丢弃: - |
| el_004_composition_row_and_person | composition | `adapt` | 保留: 三主体横向一排在画面中央的整体布置；左侧留出操作者的构图位置 · 改编: 主体改为三只外观一致的机器狗；左侧人物改为中性不可识别操作者并手持遥控器 · 丢弃: 参考视频人物的具体外观与身份 |
| el_005_action_structure_chain | action_structure | `adapt` | 保留: 分阶段动作先后顺序；跃起后攀爬并叠站的接触与支撑关系；叠站形成后的稳定保持 · 改编: 动作主体改为三只机器狗，动作写为机械腿折叠、机身压低与四足攀爬；地面改为草坪 · 丢弃: 源侧动物身份与动物动作细节 |
| el_006_interaction_stack | interaction_relation | `adapt` | 保留: 接触点（前肢踩在同伴背部/机壳）与支撑关系；组合结果出现后的稳定保持约 2 秒 · 改编: 接触对象改为机器狗机壳背部；结果形态改为两层机器狗叠站 · 丢弃: - |
| el_007_visual_style_lighting | visual_style | `adapt` | 保留: 均匀柔和的光质与中低对比；写实风格与稳定机位 · 改编: 改为明亮自然日光与户外天空光；地面反光改为草地哑光质感 · 丢弃: 暖色室内灯具与木地板反光 |
| el_008_scene_content_indoor_lounge | scene_content | `discard` | 保留: 空间深度与前中后景层次；背景密度与景深关系 · 改编: 用户明确要求户外草坪，目标场景改为草坪、低矮绿篱与树木、明亮自然日光 · 丢弃: 售货机；沙发；黄色桌椅；卡通立牌；天花板管道与吊灯；墙面音箱/屏幕 |
| el_009_subject_content_capybara | subject_content | `adapt` | 保留: 三主体数量与横向队列关系；三主体共同完成一次组合动作的展示机制 · 改编: 替换为三只外观一致的机器狗（来自用户素材 asset_001）；外观差异锚点：浅灰哑光机壳、银色金属关节、背部圆柱激光雷达、黑色传感器面板、四足细腿黑色脚垫 · 丢弃: 棕色短毛；啮齿类动物外形与动物身份 |
| el_010_person_or_body_reference_person | person_or_body | `adapt` | 保留: 人物作为左侧前景承担点题与操作者功能；随推近逐步出画的构图行为 · 改编: 改为中性、不可识别的操作者（深色短袖上衣与深色长裤，无高跟鞋）；双手改为持握小型手持遥控器并朝向机器狗 · 丢弃: 长发白衣人物身份；米色高跟鞋等源侧专属外观 |
| el_011_prop_floor_circles | prop | `discard` | 保留: - · 改编: - · 丢弃: 白色手绘圆圈；抛光木地板 |
| el_012_transition_single_take | transition | `inherit` | 保留: 单镜头连续、无转场特效；同一场景同一机位同一光线的状态延续 · 改编: - · 丢弃: - |
| el_013_uncertain_person_handheld_object | interaction_relation | `adapt` | 保留: 人物站在主体身旁并对动作过程施加影响的角色关系 · 改编: 用户明确说明“一个人在遥控三只机器狗”，据此把控制关系具体化为操作者手持小型遥控器指向机器狗群 · 丢弃: 源侧未观察到的具体控制方式 |
| el_014_incidental_details | incidental_detail | `discard` | 保留: - · 改编: - · 丢弃: 天花板管道与吊灯；墙面音箱/屏幕；地板反光 |
| el_015_unsupported_audio | unsupported_audio | `discard` | 保留: - · 改编: - · 丢弃: BGM/音乐结构与情绪；音效事件；疑似唱歌检测；卡点节奏与音频情绪曲线 |

## 全局外观元素库

| entity_id | 名称 | 类型 | 参考帧需求 | merge_status |
| --- | --- | --- | --- | --- |
| entity_robot_dog | robot dog (three identical quadruped robot units) | main_subject_appearance | 否 | merged |
| entity_person_operator | neutral operator | person_appearance | 是 | merged |
| entity_scene_lawn | outdoor lawn | scene_appearance | 是 | merged |
| entity_prop_remote | handheld remote controller | key_prop_appearance | 否 | merged |
| entity_style_daylight | bright natural daylight | style_atmosphere | 否 | merged |

## 记忆点迁移

| memory_id | 类型 | 保留机制 | 目标绑定 | 状态 |
| --- | --- | --- | --- | --- |
| vm_001 | visual | 缓慢推近/变焦的起止与方向；推近过程中主体尺度连续增大；前景人物随推近逐步出画 | SC001, SC001_SEG004, SC001_SEG005, SC001_SEG006 | ready |
| vm_002 | visual | 三主体分阶段的动作先后顺序；单个体跃起后攀爬并叠站的接触与支撑关系；叠站形成后的稳定保持 | SC001_SEG001, SC001_SEG002, SC001_SEG003, SC001_SEG004, SC001_SEG005, SC001_SEG006 | ready |
| vm_003 | visual | 开场横向一排的整体布置；随推近逐步收敛到结果主体的注意力路径 | SC001, SC001_SEG001, SC001_SEG006 | ready |
| sm_001 | script | 从整体队列到组合结果的信息释放顺序；动作准备→推进→结果揭示→保持的节拍；单一连续镜头的设置-发展-结果结构 | SC001 | ready |
| sm_002 | script | setup→payoff 的因果铺垫；结果出现后的稳定保持 | SC001_SEG006 | ready |

## 时间轴与内部节拍

### SC001_SEG001  0.0-0.7s  (0.7s)

- 参考功能 / 目标功能: `visual_display` / `visual_display`
- 生成画面: 开场全景中三只机器狗横向排成一排面向镜头，操作者站在画面左侧手持遥控器
- 生成动作: three robot dogs hold a static horizontal line facing the camera; the operator stands at the left frame edge, both hands holding the handheld remote controller at chest height
- 运镜: locked wide establishing framing, no movement yet；构图变化: three subjects spread evenly across the frame centre with the operator at frame left
- 场景迁移: outdoor park lawn: trimmed green grass, low hedges and trees in the mid background, bright natural daylight, open sky, soft natural shadows
- 主体迁移: 源 `three capybaras (brown short fur, stocky rodent shape)` → 目标 `robot dog (three identical quadruped robot units)`（可见差异锚点：浅灰哑光机壳与银色金属关节取代棕色短毛、四足机械腿取代动物四肢、背部激光雷达取代动物背部轮廓）
- 台词/口播/旁白或画面文字: 无（参考视频无对白、无旁白、无可读文字）
- 画面内实体文字/logo 状态: ready（来源 user_asset，附着于 product）
- 后期叠加状态: 无
- 参考帧决策: `subject_reference` / `needed` → 实体 entity_robot_dog, entity_person_operator, entity_scene_lawn
- 缺失输入: 无；生成假设: ga_001, ga_002, ga_003
- 状态: `ready`

### SC001_SEG002  0.7-1.7s  (1.0s)

- 参考功能 / 目标功能: `action_or_interaction` / `action_or_interaction`
- 生成画面: 三只机器狗同步压低机身进入伏地姿态并保持约一秒，操作者手指按下遥控器按钮
- 生成动作: all three robot dogs lower their bodies into a low crouched stance and hold it; the operator's thumb presses a button on the handheld remote controller
- 运镜: locked camera, no movement；构图变化: unchanged from the previous beat
- 场景迁移: outdoor park lawn: trimmed green grass, low hedges and trees in the mid background, bright natural daylight, open sky, soft natural shadows
- 主体迁移: 源 `three capybaras (brown short fur, stocky rodent shape)` → 目标 `robot dog (three identical quadruped robot units)`（可见差异锚点：浅灰哑光机壳与银色金属关节取代棕色短毛、四足机械腿取代动物四肢、背部激光雷达取代动物背部轮廓）
- 台词/口播/旁白或画面文字: 无（参考视频无对白、无旁白、无可读文字）
- 画面内实体文字/logo 状态: ready（来源 user_asset，附着于 product）
- 后期叠加状态: 无
- 参考帧决策: `subject_reference` / `needed` → 实体 entity_robot_dog, entity_person_operator, entity_scene_lawn
- 缺失输入: 无；生成假设: ga_001, ga_002, ga_003
- 状态: `ready`

### SC001_SEG003  1.7-2.3s  (0.6s)

- 参考功能 / 目标功能: `action_or_interaction` / `action_or_interaction`
- 生成画面: 队列最左侧的机器狗先直立起身，另外两只保持伏地
- 生成动作: the leftmost robot dog straightens its legs and rises first while the other two stay crouched
- 运镜: locked camera, no movement；构图变化: attention begins to shift to the leftmost unit
- 场景迁移: outdoor park lawn: trimmed green grass, low hedges and trees in the mid background, bright natural daylight, open sky, soft natural shadows
- 主体迁移: 源 `three capybaras (brown short fur, stocky rodent shape)` → 目标 `robot dog (three identical quadruped robot units)`（可见差异锚点：浅灰哑光机壳与银色金属关节取代棕色短毛、四足机械腿取代动物四肢、背部激光雷达取代动物背部轮廓）
- 台词/口播/旁白或画面文字: 无（参考视频无对白、无旁白、无可读文字）
- 画面内实体文字/logo 状态: ready（来源 user_asset，附着于 product）
- 后期叠加状态: 无
- 参考帧决策: `subject_reference` / `needed` → 实体 entity_robot_dog, entity_person_operator, entity_scene_lawn
- 缺失输入: 无；生成假设: ga_001, ga_002, ga_003
- 状态: `ready`

### SC001_SEG004  2.3-3.3s  (1.0s)

- 参考功能 / 目标功能: `action_or_interaction` / `action_or_interaction`
- 生成画面: 三只机器狗起身向前行走，居中的一只腾空跃起；镜头自约 2.8s 起缓慢推近
- 生成动作: all three robot dogs rise and walk forward toward the operator; the centre robot dog springs off the ground in a short airborne leap
- 运镜: slow push-in begins at about 2.8s；构图变化: subjects grow larger in frame as the camera tightens
- 场景迁移: outdoor park lawn: trimmed green grass, low hedges and trees in the mid background, bright natural daylight, open sky, soft natural shadows
- 主体迁移: 源 `three capybaras (brown short fur, stocky rodent shape)` → 目标 `robot dog (three identical quadruped robot units)`（可见差异锚点：浅灰哑光机壳与银色金属关节取代棕色短毛、四足机械腿取代动物四肢、背部激光雷达取代动物背部轮廓）
- 台词/口播/旁白或画面文字: 无（参考视频无对白、无旁白、无可读文字）
- 画面内实体文字/logo 状态: ready（来源 user_asset，附着于 product）
- 后期叠加状态: 无
- 参考帧决策: `subject_reference` / `needed` → 实体 entity_robot_dog, entity_person_operator, entity_scene_lawn
- 缺失输入: 无；生成假设: ga_001, ga_002, ga_003
- 状态: `ready`

### SC001_SEG005  3.3-3.8s  (0.5s)

- 参考功能 / 目标功能: `action_or_interaction` / `action_or_interaction`
- 生成画面: 腾空的机器狗落在右侧同伴背部并完成攀爬，前腿踩实形成接触支撑
- 生成动作: the centre robot dog lands on the back of the right-hand companion and settles its front legs onto the upper shell
- 运镜: push-in continues slowly；构图变化: the two-unit contact area becomes the visual centre
- 场景迁移: outdoor park lawn: trimmed green grass, low hedges and trees in the mid background, bright natural daylight, open sky, soft natural shadows
- 主体迁移: 源 `three capybaras (brown short fur, stocky rodent shape)` → 目标 `robot dog (three identical quadruped robot units)`（可见差异锚点：浅灰哑光机壳与银色金属关节取代棕色短毛、四足机械腿取代动物四肢、背部激光雷达取代动物背部轮廓）
- 台词/口播/旁白或画面文字: 无（参考视频无对白、无旁白、无可读文字）
- 画面内实体文字/logo 状态: ready（来源 user_asset，附着于 product）
- 后期叠加状态: 无
- 参考帧决策: `subject_reference` / `needed` → 实体 entity_robot_dog, entity_person_operator, entity_scene_lawn
- 缺失输入: 无；生成假设: ga_001, ga_002, ga_003
- 状态: `ready`

### SC001_SEG006  3.8-5.8s  (2.0s)

- 参考功能 / 目标功能: `visual_display` / `visual_display`
- 生成画面: 两只机器狗形成上下两层叠站并稳定保持约两秒，第三只在旁站立，操作者随推近逐渐出画
- 生成动作: two stacked robot dogs hold a stable two-level pose for about two seconds while the third stands beside them; the operator gradually leaves the frame as the camera tightens
- 运镜: slow push-in completes, settling into a tighter medium framing；构图变化: frame centre locks onto the stacked result; the operator and the left foreground drop out of frame
- 场景迁移: outdoor park lawn: trimmed green grass, low hedges and trees in the mid background, bright natural daylight, open sky, soft natural shadows
- 主体迁移: 源 `three capybaras (brown short fur, stocky rodent shape)` → 目标 `robot dog (three identical quadruped robot units)`（可见差异锚点：浅灰哑光机壳与银色金属关节取代棕色短毛、四足机械腿取代动物四肢、背部激光雷达取代动物背部轮廓）
- 台词/口播/旁白或画面文字: 无（参考视频无对白、无旁白、无可读文字）
- 画面内实体文字/logo 状态: ready（来源 user_asset，附着于 product）
- 后期叠加状态: 无
- 参考帧决策: `subject_reference` / `needed` → 实体 entity_robot_dog, entity_person_operator, entity_scene_lawn
- 缺失输入: 无；生成假设: ga_001, ga_002, ga_003
- 状态: `ready`

## 参考帧摘要

- plan_required: `True`；summary_status: `ready`；plan_path: `07_reference_frame_plan/reference_frame_plan.json`
- 人物实体 1 / 主体实体 1 / 场景实体 1 / 状态参考帧 0
- 计划参考帧 3（合并 0），H3 图片预算 8，进入 H3 图片数 3
- ready_frame_ids: rf_subject_robot_dog, rf_person_operator, rf_scene_lawn

## 未支持音频

- status: `unsupported_skipped`；items: bgm_structure, music_detection, beat_alignment, sfx_events, singing_or_suspected_singing_detection, voice_timing_as_audio, audio_mood_curve

## 缺失项与生成假设

- `mi_001` actor_presence：`missing_generate_fallback` / `generate_with_confirmed_assumption`
- `mi_002` remote_control_operation：`ready_with_text_instruction` / `use_text_instruction`
- `mi_003` target_dialogue_or_on_screen_text：`ready_with_text_instruction` / `omit_or_neutralize`
- `ga_001` actor：遥控者为一名中性、不可识别身份的表演者，仅以背影/侧身/手部操作入镜，外观与参考视频人物明显不同（深色短袖上衣与深色长裤，无高跟鞋）（proposed）
- `ga_002` scene：户外草坪场景：修剪整齐的绿色草地、远处低矮绿篱与树木、明亮自然日光（user_confirmed）
- `ga_003` subject_count：三只外观一致的机器狗（来自 asset_001 的机器狗外观）（user_confirmed）

## 专业知识整合

- professional_prompt_context.status: `partial`
- 采用术语: 全景（Full / Long Shot）, 中近景（Medium Close-Up）, 推近（Dolly In）, 静止镜头（Static）, 时间顺序描述（Temporal Order）, 主体揭示（Subject Revealing）, 揭示后保持, 标准电影节奏
- 生成摘要: 用 5.8 秒单一连续镜头完成一次户外动作演示：开场以全景建立三只机器狗的横向队列与草坪环境，机位正面偏侧略高；约 2.8s 起缓慢推近至中近景，主体尺度连续增大，左侧操作者逐步出画。动作按时间顺序书写：集体下压→依次起身→向前行走→中间个体腾空跃起→爬上右侧同伴背部→两层叠站保持约 2 秒。光线为明亮自然日光，中低对比，写实质感；不使用切镜、甩镜或焦点切换。

## 校验标记

- single_reference_shot_degraded_to_six_temporal_segments
- actor_appearance_from_confirmed_assumption_ga_001
- scene_content_from_user_text_override
- script_narrative_profiles_unavailable_professional_context_partial
