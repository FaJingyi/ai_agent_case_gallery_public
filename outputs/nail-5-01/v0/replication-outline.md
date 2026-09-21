# 复刻大纲审阅稿（Step 6）

- 目标视频：竖屏 9:16，约 15.0s，单次生成任务
- 参考视频：720x1280，15.6s（分析范围 0-15.0s），4 镜硬切
- 目标主体：`ent_nail_design`（素材 shangpin-3 的暗黑哥特长尖甲设计，戴在人物双手上）
- 承载人物：`ent_person_performer`（不可识别身份的成年女性，装扮统一为与美甲一致的暗黑哥特风格）
- 场景：`ent_scene_indoor_mirror`、`ent_scene_outdoor_highland`、`ent_scene_tower`
- 声音：`speech_status=no_confirmed_speech`，无台词/旁白/口型；音频整体 `unsupported_skipped`

## 强继承项（必须进入分镜）

| item_id | 类型 | 目标执行 |
| --- | --- | --- |
| si_time_structure | time_structure | 4 镜硬切，时长 4.0/5.0/2.0/4.0 秒 |
| si_shot_order | shot_structure | 室内镜前 → 户外高原 → 金属塔前 → 收尾 |
| si_shot1_frame_within_frame | composition | 镜面边缘 + 左侧门框形成框中框，主体居中 |
| si_shot2_picture_in_picture | composition | 左上角固定画中画小窗，主区域保持手部展示 |
| si_shot2_foreground_frame | composition | 前景手指与小花轻微失焦遮挡，中景手部清晰 |
| si_hard_cut_transitions | transition | 动作完成处直接硬切，无叠化 |
| si_camera_static | camera | 平视、基本静止、轻微跟随手部 |
| si_focus_depth | camera | 手部对焦、浅景深、背景柔化 |
| si_shot_size_rhythm | shot_structure | 人物中景/中近景与手部特写交替 |

## 参考继承项（改写后迁移）

| item_id | 类型 | 目标改写 |
| --- | --- | --- |
| ri_performer | person_or_body | 改为不可识别成年女性，装扮统一暗黑哥特 |
| ri_nail_design | prop | 换为素材中的暗黑哥特眼球+珍珠长尖甲 |
| ri_hand_display_motion | subject_motion_pattern | 动作类型一致，接近迁移 |
| ri_pinch_flower | interaction_relation | 保留接触点/转动/停顿，花改为深色小花 |
| ri_outdoor_scene | scene_content | 保留场景风格与空间结构，置景适配目标 |
| ri_screen_text | text_or_ui | 无目标文案，移除文字保留安全留白 |
| ri_audio | unsupported_audio | 审计跳过 |

## 时间轴与分镜

| Unit | 时间 | 参考 shot | Segment | 时间 | 目标内容摘要 | 特殊机制 |
| --- | --- | --- | --- | --- | --- | --- |
| U1 | 0.0-4.0 | shot1 | S1_1 | 0.0-2.3 | 室内镜前，人物居中于框中框内，双手叉腰，暗黑哥特装扮，顶部干净留白 | 框中框 |
| U1 | 0.0-4.0 | shot1 | S1_2 | 2.3-4.0 | 双手抬向镜头、掌心朝前、手指张开，前伸出现运动模糊，末端极近并部分遮挡面部 | 框中框持续 |
| U2 | 4.0-9.0 | shot2 | S2_1 | 4.0-6.0 | 硬切到户外高原草地湖泊，暗黑哥特户外装扮，双手抬到脸侧完整揭示目标美甲 | — |
| U2 | 4.0-9.0 | shot2 | S2_2 | 6.0-8.0 | 手移到下颌轻触，特写中手指捏住深色小花轻转并二次调整 | 前景遮挡框架 |
| U2 | 4.0-9.0 | shot2 | S2_3 | 8.0-9.0 | 左上角出现固定画中画小窗，第二视角确认同一套美甲 | 画中画 |
| U3 | 9.0-11.0 | shot3 | S3_1 | 9.0-11.0 | 硬切到金属塔前，换暗黑哥特长外套，双手掌心朝前展示同一套美甲 | — |
| U4 | 11.0-15.0 | shot4 | S4_1 | 11.0-15.0 | 收尾节拍：延续户外展示并加入深色宽檐帽，仅继承节拍结构（参考观察截断） | — |

## 特殊机制迁移

| mechanism_id | 类型 | 目标执行 | 必须可见 |
| --- | --- | --- | --- |
| sm_s1_frame_within_frame | special_composition | 左门框 + 镜面边缘形成内层画框，人物居中于框内 | 是（critical） |
| sm_s1_frame_within_frame_motion | special_composition | 手部在框内前伸时内层画框持续可见 | 是（critical） |
| sm_s2_picture_in_picture | special_composition | 左上角固定小窗，约占画面宽度四分之一，叠加在主画面之上 | 是（critical） |
| sm_s2_foreground_frame | special_composition | 前景手指与深色小花轻微失焦，部分框住中景手部 | 是（high） |

## 主体运动迁移

| segment | 参考动作 | 目标动作 | transfer_mode |
| --- | --- | --- | --- |
| S1_1 | 静止叉腰展示姿态 | 静止叉腰 | close_motion_reference |
| S1_2 | 双手抬向镜头掌心朝前 | 双手抬向镜头掌心朝前 | close_motion_reference |
| S2_1 | 双手抬到脸侧展示 | 双手抬到脸侧展示 | close_motion_reference |
| S2_2 | 捏花轻转 + 二次调整 | 捏深色小花轻转 + 二次调整 | close_motion_reference |
| S2_3 | 主展示 + 第二视角 | 主展示 + 画中画第二视角 | close_motion_reference |
| S3_1 | 掌心朝前展示 | 掌心朝前展示 | close_motion_reference |
| S4_1 | 未观察到（截断） | 收尾持握展示 | beat_structure_only |

## 全局外观库（去重后）

| entity_id | 类型 | 关键外观 | 状态 |
| --- | --- | --- | --- |
| ent_nail_design | main_subject | 长尖甲、黑亮面+灰褐光面、金属银色滴体、立体眼球、珍珠、白点、光泽树脂 | state_nail_design_dark_gothic（单态，复用用户素材） |
| ent_person_performer | person | 不可识别成年女性、短深发、暗黑哥特装扮、深色金属饰品 | state_performer_core（室内/户外主造型）；state_performer_outerwear（塔前+收尾：暗黑哥特长外套，收尾加宽檐帽） |
| ent_scene_indoor_mirror | scene | 暖光室内、镜面+门框内框、简洁背景 | state_scene_indoor_mirror |
| ent_scene_outdoor_highland | scene | 蓝天白云、草地、远处湖泊、自然光高饱和 | state_scene_outdoor_highland |
| ent_scene_tower | scene | 金属塔结构、蓝天、草坡、冷调自然光 | state_scene_tower |
| ent_style_atmosphere | style_atmosphere | 暗黑哥特 editorial、高对比克制、光泽树脂与金属质感 | — |

## 文字与叠加

- 参考画面文字 3 条：`POV: 当你第一次做美甲...`、`做了个 新疆猫甲!`、`和蓝天白云草地好搭!`
- 目标侧无对应文案，全部记录为 `missing_required_input`，H3 生成 clean plate 并保留安全留白。
- `target_text_items=[]`；不生成字幕、标题卡或 post overlay 文案。

## 参考帧摘要

- `frame_requirement_level=required_visual_anchors`，`plan_required=true`
- 计划参考帧 5 张：`rf_nail_design`（复用用户素材）、`rf_person_performer`、`rf_scene_indoor_mirror`、`rf_scene_outdoor_highland`、`rf_scene_tower`
- H3 图片输入 5 张，预算 8，无需合并

## 状态与审计

- 大纲状态：`ready_with_assumptions`
- 阻塞项：无
- 缺失项：`mi_performer`（生成假设补齐）、`mi_target_overlay_text`（清除处理）
- 音频：`unsupported_skipped`
