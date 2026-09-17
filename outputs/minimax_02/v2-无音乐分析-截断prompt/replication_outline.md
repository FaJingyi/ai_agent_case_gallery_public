# 复刻大纲审阅稿：minimax_02

- `schema_version`: `common_replication_outline.v2`
- `status`: `ready_with_assumptions`
- `replication_mode`: `shot_structure`
- `generation_scope`: `single_generation_task`
- 目标视频：3D 动漫风格的小镇观察短片：以同一个静止的心形双圆取景框观察小镇街景、钟楼广场、屋顶露台和镇上一个卖花的女孩。
- 参考视频：test_data/minimax_02/minimax.mp4（2560x1440 / 24.0fps / 15.0s）
- 时间精度：截断到小数点后一位，不四舍五入
- H3 输入：`<video_1>` = 参考视频 15.0s 片段；目标侧无用户素材

## 计数

- `timeline_unit_count`: 4（reference-level shots）
- `temporal_segment_count`: 10
- `prompt_level_shot_count_expected`: 10（Step 9 作为 prompt-level shots，不是 reference-level shots）

## 处理决策统计

- `reference_element_treatment_plan`: inherit=6 / adapt=12 / discard=6
- `global_appearance` 实体数：7
  - `ent_person_florist_girl`（person_appearance）：卖花女孩；状态 2 个
  - `ent_scene_town_street`（scene_appearance）：小镇石板街与花摊；状态 1 个
  - `ent_scene_town_clocktower`（scene_appearance）：小镇钟楼与广场布幡；状态 1 个
  - `ent_scene_town_rooftop`（scene_appearance）：小镇屋顶露台；状态 1 个
  - `ent_scene_floral_shop_wall`（scene_appearance）：花店外墙特写背景；状态 1 个
  - `ent_prop_flower_stall`（key_prop_appearance）：木制花摊与花桶；状态 1 个
  - `ent_style_anime_pastel_daylight`（style_atmosphere）：全片 3D 动漫粉彩日光风格与观察式取景框；状态 1 个
- 记忆点迁移：visual 6 条 / script 3 条 / audio 0 条（unsupported_skipped）

## 全局生成重点

- P1 全片保持静止的心形双圆交叠取景框与深色框外留白，框内画面被裁切（target_video）
- P2 统一 3D 动漫 toon 渲染与低饱和粉彩日光，色温、曝光与材质在四镜头间不跳变（target_video）
- P3 景别递进 中景→中景→中景/中近景→面部大特写，观察距离逐级贴近（target_video）
- P4 卖花女孩在第三、四镜头保持同一身份锚点：栗棕编辫、白色小花发饰、奶油白衬衫、鼠尾草绿围裙裙（VS001_SH003, VS001_SH004）
- P5 三次镜头边界使用单帧强运动模糊转场，转场前后取景框与注释安全区位置不变（VS001_SH001_S3, VS001_SH002_S2, VS001_SH003_S2）
- P6 首镜的移焦合焦、推近挤出安全区，以及第四镜手部整理发丝的接触点与结束状态（VS001_SH001_S1, VS001_SH001_S3, VS001_SH004_S2）

## VS001_SH001　0.0-4.5s（4.5s）

- 参考单元：`VS001:shot1`；`unit_type=video_shot`；`status=ready_with_assumptions`
- 参考功能：opening_establish
- 目标画面：心形双圆取景框内的小镇石板街清晨空镜从失焦逐渐合焦，落点收在街心的木制花摊上。
- 拍摄继承：static camera with rack focus / 平视观察视角（observer eye-level） / 起始整体失焦，约 1.0s 完成合焦；中景花摊清晰，背景民居浅景深柔和虚化。
- 剪辑与转场：镜头起点，无转场。
- 使用素材：`reference_video_excerpt_VS001` 作为 `<video_1>`（motion/camera/timing reference）
- unit 负向约束：none
- 缺失输入：mi_001

| segment | 时间 | 时长 | 参考功能 | 目标功能 | 场景迁移 | 主体/动作迁移 | 画内文字/logo | 后期叠加 | 参考帧决策 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `VS001_SH001_S1` | 0.0-1.0s | 1.0s | `visual_display` | `opening_establish_and_subject_reveal` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `scene_reference`（st_street_daylight, st_stall_ready） | - | `ready_with_assumptions` |
| `VS001_SH001_S2` | 1.0-3.5s | 2.5s | `text_overlay_or_information_reveal` | `carrier_and_scale_reveal` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `scene_reference`（st_street_daylight, st_stall_ready） | mi_001 | `ready_with_assumptions` |
| `VS001_SH001_S3` | 3.5-4.5s | 1.0s | `transition` | `slow_push_in_and_motion_blur_transition` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `subject_reference`（st_stall_ready） | - | `ready_with_assumptions` |

### VS001_SH001_S1　0.0-1.0s

- 生成画面：心形双圆取景框内的小镇石板街清晨空镜从失焦逐渐合焦，落点收在街心的木制花摊上。
- 生成动作/运镜：0.0s 画面整体失焦模糊 → 约 0.5s 焦点开始收敛 → 约 1.0s 花摊与石板路完全清晰。｜机位：static camera with rack focus｜构图：心形双圆交叠取景框内构图（框中框）；中景；主体居中；前中后景三层空间；左右边缘注释安全区占位
- 焦点/景深：起始整体失焦，约 1.0s 完成合焦；中景花摊清晰，背景民居浅景深柔和虚化。
- 必须可见：心形双圆交叠取景框与框外深色底；木制花摊、条纹遮阳篷与并排镀锌花桶；粉彩抹灰民居墙面与陶土瓦屋顶；清晨偏暖侧光在墙面形成长而柔和的阴影
- 台词/口播/旁白或画面文字：无台词无口播；开场只做观察式环境建立，不出现人物发言。
- 场景迁移：城市街道公交候车亭、玻璃与石材建筑立面、顶棚白色字标 → 小镇石板街、粉彩抹灰民居、街心木制花摊（adapt）
- 主体/道具迁移：候车亭顶棚的白色无衬线字标 → 木制花摊与花桶（ent_prop_flower_stall）（adapt）
- 可见差异锚点：低层瓦顶粉彩小镇替代高层玻璃石材都市；石板路与花摊替代人行道与候车亭；明亮粉彩日光替代暖棕浅调实拍；陶土瓦屋顶与木质百叶窗替代规则窗格立面
- 特殊机制：smt_sh001_s1_frame_in_frame(adapt), smt_sh001_s1_rack_focus(inherit)
- 参考帧决策：`scene_reference` / `needed`；实体 ent_scene_town_street, ent_prop_flower_stall
- 状态绑定：st_street_daylight；st_stall_ready；st_style_single
- 生成假设：ga_002, ga_004
- 审计项：none
- 缺失输入：none
- 状态：`ready_with_assumptions`

### VS001_SH001_S2　1.0-3.5s

- 生成画面：合焦后的花摊完整呈现，遮阳篷与花摊轮廓在民居墙面上投下放大的清晰阴影，形成与参考视频“载体先清晰、同一信息再被放大”等价的揭示节奏。
- 生成动作/运镜：花摊细节完全清晰 → 墙面上的篷布阴影稳定可见 → 花束与悬挂花篮在轻风中轻微摆动。｜机位：static camera with slight drift｜构图：心形双圆交叠取景框内构图（框中框）；中景；主体居中；主体与其放大投影同框
- 焦点/景深：花摊与墙面投影均清晰，背景屋顶浅景深柔化。
- 必须可见：墙上放大的篷布与花摊轮廓阴影；三只镀锌花桶与成束鲜花；悬挂花篮随轻风轻微摆动
- 台词/口播/旁白或画面文字：无台词无口播；本段的“信息揭示”以可见投影与花摊细节完成，不使用任何可读文字。
- 场景迁移：候车亭后墙出现大号字母投影 → 民居墙面出现放大的篷布与花摊轮廓阴影（adapt）
- 主体/道具迁移：候车亭顶棚字标与其墙面投影 → 花摊篷布与其墙面放大阴影（adapt）
- 可见差异锚点：无字投影替代字母投影；粉彩墙面替代玻璃石材立面
- 特殊机制：smt_sh001_s2_frame_in_frame(adapt), smt_sh001_s2_scale_reveal(adapt)
- 参考帧决策：`scene_reference` / `needed`；实体 ent_scene_town_street, ent_prop_flower_stall
- 状态绑定：st_street_daylight；st_stall_ready；st_style_single
- 生成假设：ga_002, ga_004, ga_005
- 审计项：nc_sh001_s2_no_readable_text
- 缺失输入：mi_001
- 状态：`ready_with_assumptions`

### VS001_SH001_S3　3.5-4.5s

- 生成画面：镜头缓慢推近花摊，左右两侧注释安全区被推出画面，结束时以单帧强运动模糊衔接下一镜头。
- 生成动作/运镜：3.5s 开始缓推 → 4.5s 花摊明显放大、边缘安全区被推出画框 → 单帧强运动模糊。｜机位：slow dolly in / push-in｜构图：心形双圆交叠取景框内构图（框中框）；中景向中近景过渡；缓推（Dolly In）；边缘安全区被推出画框
- 焦点/景深：推近过程中花摊保持清晰，背景民居持续浅景深虚化。
- 必须可见：花摊在框内逐步放大；左右注释安全区被缓慢推出画框；末端单帧强运动模糊
- 台词/口播/旁白或画面文字：无台词无口播。
- 场景迁移：城市街道候车亭，注释文字被推出画面 → 小镇石板街花摊，注释安全区被推出画面（adapt）
- 主体/道具迁移：候车亭字标 → 花摊与花桶（adapt）
- 可见差异锚点：粉彩小镇街景替代都市候车亭；无字安全区替代红色注释
- 特殊机制：smt_sh001_s3_slow_push_in(inherit), smt_sh001_s3_motion_blur_transition(inherit)
- 参考帧决策：`subject_reference` / `needed`；实体 ent_prop_flower_stall
- 状态绑定：st_street_daylight；st_stall_ready；st_style_single
- 生成假设：ga_002, ga_004, ga_005
- 审计项：none
- 缺失输入：none
- 状态：`ready_with_assumptions`

## VS001_SH002　4.5-8.5s（4.0s）

- 参考单元：`VS001:shot2`；`unit_type=video_shot`；`status=ready_with_assumptions`
- 参考功能：second_carrier_establish
- 目标画面：取景框内切换到小镇广场：石砌钟楼占据左中景，一条长幅无字布幡从钟楼侧面垂落，广场上方拉有三角彩旗绳，背景是浅蓝天空与松软白云。
- 拍摄继承：static camera with slight drift / 平视略带轻微仰视 / 布幡与钟楼清晰，远处民居轻微空气透视。
- 剪辑与转场：由上一镜头以单帧运动模糊切入（约 4.5s）。
- 使用素材：`reference_video_excerpt_VS001` 作为 `<video_1>`（motion/camera/timing reference）
- unit 负向约束：nc_unit_sh002_banner_text
- 缺失输入：mi_001

| segment | 时间 | 时长 | 参考功能 | 目标功能 | 场景迁移 | 主体/动作迁移 | 画内文字/logo | 后期叠加 | 参考帧决策 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `VS001_SH002_S1` | 4.5-5.6s | 1.1s | `visual_display` | `new_carrier_establish` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `scene_reference`（st_clocktower_daylight） | mi_001 | `ready_with_assumptions` |
| `VS001_SH002_S2` | 5.6-8.5s | 2.9s | `visual_display` | `fabric_motion_reveal_and_transition` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `scene_reference`（st_clocktower_daylight） | - | `ready_with_assumptions` |

### VS001_SH002_S1　4.5-5.6s

- 生成画面：取景框内切换到小镇广场：石砌钟楼占据左中景，一条长幅无字布幡从钟楼侧面垂落，广场上方拉有三角彩旗绳，背景是浅蓝天空与松软白云。
- 生成动作/运镜：4.5s 转场进入 → 布幡初始接近垂直下垂 → 三角彩旗绳小幅摆动。｜机位：static camera with slight drift｜构图：心形双圆交叠取景框内构图（框中框）；中景；楼体偏左占据画面左中；背景大面积天空留白；左右边缘注释安全区占位
- 焦点/景深：布幡与钟楼清晰，远处民居轻微空气透视。
- 必须可见：石砌钟楼与白色圆盘钟面；从钟楼垂下的长幅无字布幡；广场上方的三角彩旗绳；浅蓝天空与白云
- 台词/口播/旁白或画面文字：无台词无口播；本段以空镜继续释放观察信息。
- 场景迁移：米黄色高层楼体立面、规则窗格、悬挂白色竖排字布旗 → 小镇广场石砌钟楼、三角彩旗绳、垂落无字布幡（adapt）
- 主体/道具迁移：白色竖幅品牌字布旗 → 陶土色无字织纹布幡（adapt）
- 可见差异锚点：石砌钟楼与广场替代高层楼体立面；陶土色无字布幡替代白色竖排品牌字布旗；三角彩旗绳替代单一悬挂布旗；明亮蓝天白云替代暖棕颗粒天空
- 特殊机制：smt_sh002_s1_frame_in_frame(adapt), smt_sh002_s1_fabric_motion(adapt)
- 参考帧决策：`scene_reference` / `needed`；实体 ent_scene_town_clocktower
- 状态绑定：st_clocktower_daylight；st_style_single
- 生成假设：ga_002, ga_004, ga_005
- 审计项：nc_sh002_s1_no_banner_text
- 缺失输入：mi_001
- 状态：`ready_with_assumptions`

### VS001_SH002_S2　5.6-8.5s

- 生成画面：布幡在持续风力下反复外翻，交替露出陶土色正面与米白色背面，三角彩旗同步小幅摆动；镜头基本固定并轻微漂移，末端以单帧强运动模糊转场。
- 生成动作/运镜：5.6s 布幡仍接近垂直 → 6.0-8.0s 逐渐外翻并反复露出背面米白色 → 8.5s 单帧强运动模糊。｜机位：static camera with slight drift｜构图：心形双圆交叠取景框内构图（框中框）；中景；楼体偏左；天空留白；左右边缘注释安全区占位
- 焦点/景深：布幡始终清晰，背景天空与远景民居轻微柔化。
- 必须可见：布幡反复外翻并露出另一面色；三角彩旗绳同步小幅摆动；末端单帧强运动模糊
- 台词/口播/旁白或画面文字：无台词无口播；本段以织物动态承担节奏推进。
- 场景迁移：楼体立面与风中布旗 → 钟楼广场与风中无字布幡（adapt）
- 主体/道具迁移：白底黑字竖幅布旗（背面红色） → 陶土色正面 / 米白色背面的无字布幡（adapt）
- 可见差异锚点：石砌钟楼替代高层楼体；陶土色/米白双面布幡替代白色/红色布旗
- 特殊机制：smt_sh002_s2_fabric_turnover(adapt), smt_sh002_s2_motion_blur_transition(inherit)
- 参考帧决策：`scene_reference` / `needed`；实体 ent_scene_town_clocktower
- 状态绑定：st_clocktower_daylight；st_style_single
- 生成假设：ga_002, ga_004
- 审计项：none
- 缺失输入：none
- 状态：`ready_with_assumptions`

## VS001_SH003　8.5-11.5s（3.0s）

- 参考单元：`VS001:shot3`；`unit_type=video_shot`；`status=ready_with_assumptions`
- 参考功能：subject_entry
- 目标画面：取景框内切换到小镇屋顶露台：卖花女孩以站立姿态出现在画面中央中景，左前臂挂草篮，右手持花束；前景是摆着红色天竺葵与白色雏菊的女儿墙，中景是连绵陶土瓦屋顶，远处可见钟楼。
- 拍摄继承：static camera with slight drift / 平视观察视角 / 女孩清晰，前景盆栽轻微失焦，远处屋顶带空气透视。
- 剪辑与转场：由上一镜头以单帧运动模糊切入（约 8.5s）。
- 使用素材：`reference_video_excerpt_VS001` 作为 `<video_1>`（motion/camera/timing reference）
- unit 负向约束：nc_unit_sh003_identity
- 缺失输入：mi_003

| segment | 时间 | 时长 | 参考功能 | 目标功能 | 场景迁移 | 主体/动作迁移 | 画内文字/logo | 后期叠加 | 参考帧决策 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `VS001_SH003_S1` | 8.5-10.0s | 1.5s | `visual_display` | `person_entry_and_scene_establish` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `merged_reference`（st_florist_initial, st_rooftop_afternoon） | mi_003 | `ready_with_assumptions` |
| `VS001_SH003_S2` | 10.0-11.5s | 1.5s | `action_or_interaction` | `pose_hold_and_slow_push_in` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `merged_reference`（st_florist_initial, st_rooftop_afternoon） | - | `ready_with_assumptions` |

### VS001_SH003_S1　8.5-10.0s

- 生成画面：取景框内切换到小镇屋顶露台：卖花女孩以站立姿态出现在画面中央中景，左前臂挂草篮，右手持花束；前景是摆着红色天竺葵与白色雏菊的女儿墙，中景是连绵陶土瓦屋顶，远处可见钟楼。
- 生成动作/运镜：8.5s 转场进入 → 女孩保持站立姿态入画 → 左前臂草篮稳定挂在臂弯，右手持花束自然下垂。｜机位：static camera with slight drift｜构图：心形双圆交叠取景框内构图（框中框）；中景人物；主体居中；前景女儿墙 / 中景人物 / 背景屋顶三层空间；左右边缘注释安全区占位
- 焦点/景深：女孩清晰，前景盆栽轻微失焦，远处屋顶带空气透视。
- 必须可见：卖花女孩全身大部分可见的站立中景；鼠尾草绿围裙裙与奶油白衬衫；左前臂草篮与右手花束；露台女儿墙盆栽与远处陶土瓦屋顶
- 台词/口播/旁白或画面文字：无台词无口播；本段人物不说话也不对口型，只保留站立姿态、朝向与轻微表情。
- 场景迁移：都市天台：混凝土女儿墙、墙面黑色大字、远景城市楼群 → 小镇屋顶露台：陶盆花卉女儿墙、陶土瓦屋顶、远处钟楼（adapt）
- 主体/道具迁移：身份不确定的女性人物（米色西装、白色内搭、红色肩包、深色杯具） → 非特定身份的 3D 动漫卖花女孩（奶油白衬衫、鼠尾草绿围裙裙、草篮、花束）（adapt）
- 可见差异锚点：低层瓦顶屋顶群替代高层混凝土墙面与都市天际线；陶盆花卉女儿墙替代女儿墙 + 墙面黑色大字；午后暖侧光替代暖棕平光；钟楼远景替代玻璃幕墙楼群
- 特殊机制：smt_sh003_s1_frame_in_frame(adapt), smt_sh003_s1_pose_hold(adapt)
- 参考帧决策：`merged_reference` / `needed`；实体 ent_person_florist_girl, ent_scene_town_rooftop
- 状态绑定：st_florist_initial；st_rooftop_afternoon；st_style_single
- 生成假设：ga_003, ga_004
- 审计项：nc_sh003_s1_identity_leak
- 缺失输入：mi_003
- 状态：`ready_with_assumptions`

### VS001_SH003_S2　10.0-11.5s

- 生成画面：女孩头部轻微右转、视线随之微移，持花姿势保持；镜头缓慢推近，景别由中景向中近景过渡，末端以单帧强运动模糊转场。
- 生成动作/运镜：10.0s 头部开始轻微右转 → 视线随之移动 → 11.5s 景别明显变近并进入单帧强运动模糊。｜机位：slow dolly in / push-in｜构图：心形双圆交叠取景框内构图（框中框）；中景向中近景过渡；主体居中；缓推（Dolly In）
- 焦点/景深：推近过程中人物保持清晰，背景屋顶逐渐柔化。
- 必须可见：女孩头部轻微右转与视线移动；草篮与花束保持在同一位置；景别逐步变近；末端单帧强运动模糊
- 台词/口播/旁白或画面文字：无台词无口播；只写头部转动、视线方向与呼吸般的轻微起伏。
- 场景迁移：都市天台 → 小镇屋顶露台（adapt）
- 主体/道具迁移：米色西装女性 → 3D 动漫卖花女孩（adapt）
- 可见差异锚点：陶土瓦屋顶与钟楼远景替代城市楼群
- 特殊机制：smt_sh003_s2_slow_push_in(inherit), smt_sh003_s2_motion_blur_transition(inherit)
- 参考帧决策：`merged_reference` / `needed`；实体 ent_person_florist_girl, ent_scene_town_rooftop
- 状态绑定：st_florist_initial；st_rooftop_afternoon；st_style_single
- 生成假设：ga_003, ga_004
- 审计项：none
- 缺失输入：none
- 状态：`ready_with_assumptions`

## VS001_SH004　11.5-15.0s（3.5s）

- 参考单元：`VS001:shot4`；`unit_type=video_shot`；`status=ready_with_assumptions`
- 参考功能：closing_reveal_setup
- 目标画面：取景框内推近到卖花女孩的面部大特写：栗棕色编辫、左耳上方的白色小花、琥珀色眼睛与浅色雀斑清晰可见；背景是粉彩色花店外墙与木质条板，浅景深柔化。
- 拍摄继承：static camera with slight drift / 平视近距观察视角 / 面部与发饰锐利清晰，背景花店外墙明显虚化。
- 剪辑与转场：由上一镜头以单帧运动模糊切入（约 11.5s）。
- 使用素材：`reference_video_excerpt_VS001` 作为 `<video_1>`（motion/camera/timing reference）
- unit 负向约束：nc_unit_sh004_no_sunglasses
- 缺失输入：none

| segment | 时间 | 时长 | 参考功能 | 目标功能 | 场景迁移 | 主体/动作迁移 | 画内文字/logo | 后期叠加 | 参考帧决策 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `VS001_SH004_S1` | 11.5-12.0s | 0.5s | `visual_display` | `close_up_establish` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `merged_reference`（st_florist_initial, st_shopwall_daylight） | - | `ready_with_assumptions` |
| `VS001_SH004_S2` | 12.0-14.0s | 2.0s | `action_or_interaction` | `micro_action_contact_and_release` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `person_reference`（st_florist_hair_touch） | - | `ready_with_assumptions` |
| `VS001_SH004_S3` | 14.0-15.0s | 1.0s | `closing_or_prompt` | `closing_hold` | adapt | adapt | none（不生成可读文字） | `omitted_by_user_confirmation`（postprocess_ffmpeg_opencv） | `merged_reference`（st_florist_initial, st_shopwall_daylight） | - | `ready_with_assumptions` |

### VS001_SH004_S1　11.5-12.0s

- 生成画面：取景框内推近到卖花女孩的面部大特写：栗棕色编辫、左耳上方的白色小花、琥珀色眼睛与浅色雀斑清晰可见；背景是粉彩色花店外墙与木质条板，浅景深柔化。
- 生成动作/运镜：11.5s 由运动模糊切入面部大特写 → 五官与发饰细节清晰稳定。｜机位：static camera with slight drift｜构图：心形双圆交叠取景框内构图（框中框）；面部大特写（Extreme Close-Up）；面部居中；背景浅景深；左右边缘注释安全区占位
- 焦点/景深：面部与发饰锐利清晰，背景花店外墙明显虚化。
- 必须可见：栗棕色编辫与左耳上方白色小花；琥珀色眼睛与浅色雀斑；粉彩色花店外墙与悬挂花篮虚化背景
- 台词/口播/旁白或画面文字：无台词无口播；本段不出现说话或对口型，只保留面部静止与轻微眨眼。
- 场景迁移：带竖向格栅的浅色建筑外墙、镜片反射建筑 → 粉彩抹灰花店外墙、木质条板、悬挂花篮与橱窗反射（adapt）
- 主体/道具迁移：深色齐刘海短发、红色多边形框墨镜、银色耳环、红色衣领 → 栗棕色编辫、白色小花发饰、无墨镜的完整面部、奶油白衬衫领口（adapt）
- 可见差异锚点：粉彩抹灰 + 木质条板花店外墙替代灰色竖向格栅建筑外墙；悬挂花篮替代空白墙面；橱窗反射街景替代品牌字标反射
- 特殊机制：smt_sh004_s1_close_up_reveal(adapt), smt_sh004_s1_frame_in_frame(adapt)
- 参考帧决策：`merged_reference` / `needed`；实体 ent_person_florist_girl, ent_scene_floral_shop_wall
- 状态绑定：st_florist_initial；st_shopwall_daylight；st_style_single
- 生成假设：ga_003, ga_004
- 审计项：nc_sh004_s1_no_sunglasses
- 缺失输入：none
- 状态：`ready_with_assumptions`

### VS001_SH004_S2　12.0-14.0s

- 生成画面：在同一面部大特写中，女孩右手从画面外抬起，指尖接触右侧耳际发丝并把碎发拨到耳后，随后手离开画面；头部随之轻微偏转，背景与光线保持一致。
- 生成动作/运镜：12.0s 右手从画面右侧抬起 → 12.0-13.0s 指尖接触耳际发丝并把碎发向耳后拨拢 → 13.0-14.0s 手离开画面回到静止。｜机位：static camera with slight drift｜构图：心形双圆交叠取景框内构图（框中框）；面部大特写（Extreme Close-Up）；面部居中；手部动作进入画面右侧
- 焦点/景深：手指与耳际发丝清晰，背景持续虚化。
- 必须可见：右手从画面外抬起；指尖与耳际发丝的接触点；碎发被拨到耳后的动作方向；手离开画面后恢复静止佩戴状态
- 台词/口播/旁白或画面文字：无台词无口播；以手部微动作承担收束节奏。
- 场景迁移：带竖向格栅的浅色建筑外墙 → 粉彩抹灰花店外墙（adapt）
- 主体/道具迁移：手指扶推墨镜镜框 → 手指整理耳际发丝（adapt）
- 可见差异锚点：花店外墙替代格栅建筑外墙
- 特殊机制：smt_sh004_s2_micro_action(adapt), smt_sh004_s2_single_take(inherit)
- 参考帧决策：`person_reference` / `needed`；实体 ent_person_florist_girl
- 状态绑定：st_florist_hair_touch；st_shopwall_daylight；st_style_single
- 生成假设：ga_003
- 审计项：none
- 缺失输入：none
- 状态：`ready_with_assumptions`

### VS001_SH004_S3　14.0-15.0s

- 生成画面：手离开画面后回到静止状态，女孩头部轻微转动并自然眨眼，面部大特写与虚化的花店外墙保持到 15.0s 结束。
- 生成动作/运镜：14.0s 手完全离开画面 → 头部轻微转动、自然眨眼 → 15.0s 画面结束。｜机位：static camera with slight drift｜构图：心形双圆交叠取景框内构图（框中框）；面部大特写（Extreme Close-Up）；面部居中；背景浅景深
- 焦点/景深：面部清晰，背景保持虚化。
- 必须可见：手已离开画面的静止状态；头部轻微转动与自然眨眼；取景框与安全区保持不动直到结束
- 台词/口播/旁白或画面文字：无台词无口播；结尾只保留注视与停顿。
- 场景迁移：带竖向格栅的浅色建筑外墙 → 粉彩抹灰花店外墙（adapt）
- 主体/道具迁移：墨镜佩戴静止状态 → 编辫与花朵发饰的静止状态（adapt）
- 可见差异锚点：花店外墙替代格栅建筑外墙
- 特殊机制：smt_sh004_s3_closing_hold(inherit), smt_sh004_s3_frame_in_frame(adapt)
- 参考帧决策：`merged_reference` / `needed`；实体 ent_person_florist_girl, ent_scene_floral_shop_wall
- 状态绑定：st_florist_initial；st_shopwall_daylight；st_style_single
- 生成假设：ga_003
- 审计项：none
- 缺失输入：none
- 状态：`ready_with_assumptions`

## 参考帧摘要

- `frame_requirement_level`: required_visual_anchors
- `plan_required`: True
- `person_entity_count`: 1
- `subject_entity_count`: 1
- `scene_entity_count`: 4
- `state_frame_count`: 2
- `planned_frame_count`: 7
- `selected_h3_image_count`: 0
- `merged_frame_count`: 0
- `h3_image_budget`: 8
- `plan_path`: 07_reference_frame_plan/reference_frame_plan.json
- `ready_frame_ids`: 
- `summary_status`: ready
- `triggered_rules`: person_reference_entity_present, subject_reference_entity_present, scene_reference_entity_present, appearance_state_change_present
- `notes`: 全局元素库中 1 个人物实体（2 个外观状态）、1 个关键道具实体、4 个场景实体需要参考图；风格氛围实体不需参考图。, 进入 H3 的图片参考总数预计 7 张，未超过 8 张预算，不需要合并。

## 文字与 logo 策略

- `post_overlay_default`: `True`
- `in_scene_allowed_when_physically_attached`: `True`
- `render_post_overlay_in_video_model`: `False`
- `post_overlay_render_method`: `ffmpeg_or_opencv`
- `do_not_generate_unconfirmed_readable_text`: `True`

## 负向约束策略

- `prompt_weight`: `low`；`default_prompt_visibility`: `audit_only`
- 全局审计项：source_identity_leak（原片人物身份/服装配饰）、unconfirmed_text_logo（原片品牌字标与注释文案）、post_overlay_only（左右注释层）、unsupported_claim（无）、asset_fidelity_risk（无用户素材）

## 音频

- `unsupported_audio.status`: `unsupported_skipped`；范围：music, bgm, sound_effects, singing, voice_emotion, beat_sync

## 缺失输入与生成假设

- `mi_001` `in_scene_text_logo` → `neutralize_allowed` / `omit_or_neutralize`
- `mi_002` `post_overlay_text_content` → `missing_required_input` / `omit_or_neutralize`
- `mi_003` `target_scene_and_actor_visual` → `missing_generate_fallback` / `generate_with_confirmed_assumption`
- `ga_001` `visual_style` → `user_confirmed`；需要参考帧：`False`
- `ga_002` `scene` → `user_confirmed`；需要参考帧：`True`
- `ga_003` `actor` → `user_confirmed`；需要参考帧：`True`
- `ga_004` `props` → `proposed`；需要参考帧：`False`
- `ga_005` `post_overlay_text_content` → `proposed`；需要参考帧：`False`

## 专业知识整合

- `professional_prompt_context.status`: `partial`
- `VK-COMP-003`（composition）：backend/profiles/视觉/画幅构图与空间/景别与机位视点/景别与机位视点.md
- `VK-COMP-004`（composition）：backend/profiles/视觉/画幅构图与空间/前中后景与景深层次/前中后景与景深层次.md
- `VK-CAM-001`（camera_motion）：backend/profiles/视觉/镜头运动与光学/摄影机位移旋转与复合运镜/摄影机位移旋转与复合运镜.md
- `VK-CAM-002`（camera_motion）：backend/profiles/视觉/镜头运动与光学/焦点转移与镜头光学/焦点转移与镜头光学.md
- `VK-LIGHT-002`（lighting）：backend/profiles/视觉/光线色彩与质感/色温调色与画面质感/色温调色与画面质感.md
- `VK-EDIT-001`（editing）：backend/profiles/视觉/剪辑转场与时间/硬切淡化与音画先后切/硬切淡化与音画先后切.md
- `VK-GFX-001`（overlay）：backend/profiles/视觉/字幕图形与画面合成/字幕排版与平台安全区/字幕排版与平台安全区.md
- `VK-ACT-001`（action_continuity）：backend/profiles/视觉/主体动作与连续性/主体动作、物体交互与出入画/主体动作物体交互与出入画.md
- `VK-ACT-002`（action_continuity）：backend/profiles/视觉/主体动作与连续性/多镜头身份与风格锚定/多镜头身份与风格锚定.md
- 采用术语数：17

## 校验标记

- `no_user_assets_provided_target_side_is_text_only`
- `target_appearance_based_on_generation_assumptions_requires_visible_difference_anchor`
- `in_scene_readable_text_not_confirmed_target_side_neutralized`
- `post_overlay_text_content_missing_renders_clean_safe_area_only`
- `audio_unsupported_skipped`
- `script_narrative_profile_directory_empty`

