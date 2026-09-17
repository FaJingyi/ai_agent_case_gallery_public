# 复刻大纲审阅稿

本文件是 `06_replication_outline/replication_outline.json` 的人工审阅稿，按时间轴展示目标视频的生成画面、动作/运镜、场景迁移、文字策略、素材绑定、参考帧决策、审计项和各阶段状态。

## 运行摘要

| 字段 | 值 |
| --- | --- |
| schema_version | `common_replication_outline.v2` |
| 复刻模式 | `shot_structure`（单条连续镜头结构复刻） |
| 生成状态 | `ready_with_assumptions` |
| 参考视频 | `test_data/animal/2_2_case4-H3-original.mp4` |
| 参考视频时长/画幅/帧率 | 5.9s / 1344x768 / 24.0fps |
| 目标视频时长 | 5.8s |
| 目标画幅 | 1344x768 |
| 目标主体 | 三只哈士奇（同型哈士奇，以用户素材中的哈士奇为外观锚点，第二、第三只带可见差异） |
| 目标场景 | 开阔的户外草坪运动场，白天自然光 |
| `timeline_unit_count` | 1 |
| `temporal_segment_count` | 7 |
| `h3_prompt_shot_count` | 7（Step 9 prompt 中 `[Shot 1]`-`[Shot 7]`，为 prompt 级分镜，不等于参考视频镜头数） |
| H3 素材模式 | `reference_video_plus_reference_images` |
| 参考视频 H3 输入策略 | enabled=`True` / mode=`full_video_reference` |
| 参考帧计划 | plan_required=`True` / planned=`4` / selected_h3_image_count=`4` / budget=`8` |
| H3 prompt/request 状态 | Step 9 产物位于 `09_h3_package/`（`h3_submit_prompt.md`、`h3_request.json`）；本 dry run 只准备请求，不提交 |
| H3 视频状态 | `skipped_dry_run`（未提交、未生成 `10_h3_video_output/`） |

## 全局外观库（global_appearance_dedup_pass.global_appearance）

| entity_id | 名称 | 类型 | 关键外观（可执行细节） | 状态 | 参考帧策略 | 引用 segment |
| --- | --- | --- | --- | --- | --- | --- |
| `ENT_HUSKY_LEFT` | husky_left（左侧哈士奇，下层承重犬） | `main_subject_appearance` | 中型偏大的哈士奇：灰黑色鞍状背部与体侧、白色胸腹与四肢、典型白色面部面具；双层蓬松被毛，毛量厚实；颈部与尾部毛量尤其明显；立耳，耳内浅粉；黑色鼻头；张嘴时露出粉色舌头；异色瞳：一侧琥珀棕色眼、一侧蓝色眼 | HSK_LEFT_S1(站立外观/single_state) | `HSK_LEFT_S1=reuse_user_asset` | SEG001, SEG006, SEG007 |
| `ENT_HUSKY_CENTER` | husky_center（中间哈士奇，上层攀爬犬） | `main_subject_appearance` | 同型哈士奇，体型略瘦、四肢略长，便于完成攀爬上叠动作；被毛基色与用户素材一致（灰黑白三色），面部面具比左侧哈士奇更深、更宽；双眼均为琥珀棕色，与左侧哈士奇的异色瞳形成可见区分；立耳，黑色鼻头，蓬松向上卷曲的尾巴 | HSK_CENTER_S1(站立外观/single_state) | `HSK_CENTER_S1=image_to_image_from_user_asset` | SEG001, SEG006, SEG007 |
| `ENT_HUSKY_RIGHT` | husky_right（右侧哈士奇，下层承重犬） | `main_subject_appearance` | 同型哈士奇，体型略大、胸腔更宽，作为右侧承重犬；被毛整体偏银灰色，深色背部范围比左侧哈士奇更浅；单侧蓝眼（另一侧浅褐），与另外两只形成可见区分；立耳、黑色鼻头、蓬松向上卷曲的尾巴 | HSK_RIGHT_S1(站立外观/single_state) | `HSK_RIGHT_S1=image_to_image_from_user_asset` | SEG001, SEG006, SEG007 |
| `ENT_LAWN_SCENE` | outdoor_lawn_scene（户外草坪场景） | `scene_appearance` | 空间类型：开阔的户外草坪运动场，无室内结构与人工道具；前景：修剪整齐的绿色草地，草叶细节清晰，带有柔和反光；中景：平整连续的草地承载三只哈士奇的表演动作；背景：低密度虚化的户外环境，仅保留远处建筑或树林的柔和轮廓，不出现可读文字、招牌或 logo | LAWN_S1(白天户外草坪/single_state) | `LAWN_S1=text_to_image` | SEG001, SEG005, SEG007 |
| `ENT_STYLE_ATMOSPHERE` | daylight_lawn_atmosphere（白天草坪氛围） | `style_atmosphere` | 光线情绪：明亮、通透的白天户外自然光；色彩倾向：饱和绿色为主，暖色高光与偏冷环境阴影形成色温对比；真实感：自然写实的实拍质感，非风格化滤镜；质感：草叶与犬只被毛纹理清晰，背景柔和虚化 | single_state（风格氛围，无独立参考帧） | `not_required` | SEG001, SEG007 |

## 记忆点迁移（memory_transfer_plan.visual）

| memory_id | 时间范围 | 保留机制 | 目标侧替换 | segment 绑定 | 状态 |
| --- | --- | --- | --- | --- | --- |
| `VM-1` | 3.0-5.4s | 单条连续镜头；前段静止宽幅开场；约 3.0s 起单次连续推近收紧取景；取景变化过程中动作不中断 | 室内休息区场景改写为户外草坪；三只水豚替换为三只哈士奇；推近的物理动因按户外开阔空间重写 | TU001, SEG004, SEG005 | `adapted` |
| `VM-2` | 0.0-3.0s | 宽幅开场构图；主体群居中；画面左侧三分之一保留独立视觉区；左右信息分区的读图顺序 | 左侧三分位的配角人物不迁移；由空旷草坪与远处虚化背景承担该区域的空间功能 | TU001, SEG001, SEG002 | `adapted` |
| `VM-3` | 0.0-5.8s | 单镜头内的有序动作节拍；群体同步的姿势变化；朝镜头方向的移动；被承载支撑的叠站终点造型并保持到结尾 | 节拍主体改为三只哈士奇；动作按犬科体型与草地接触关系重写；终点造型改为草坪上的哈士奇叠站 | TU001, SEG001, SEG002, SEG003, SEG004, SEG005, SEG006, SEG007 | `adapted` |
| `VM-4` | 0.0-5.8s | 暖色主光与冷色背景的色温对比机制；地面反光增强空间纵深；自然写实的画面质感 | 室内夜景改为白天户外自然光；抛光地板反光改为草叶柔和反光；冷色来源由夜间窗光改为天空方向环境光 | TU001, SEG001, SEG007 | `adapted` |

`memory_points.audio[]` 与音乐/BGM/音效保持 `unsupported_skipped` 审计，不进入目标画面与 prompt。

## 时间轴单元 `TU001`（0.0-5.8s，单条连续镜头）

- 参考结构：单镜头一镜到底，无切点；动作节拍按时间顺序推进。
- 目标结构：一条连续镜头，三只哈士奇在户外草坪上完成并排站立、同步趴卧、保持、起身前移、两只并立承重、中间一只上叠并保持到结尾的群体表演。
- 镜头总变化：动作=三只哈士奇在草坪上完成一整套有序群体动作并以叠站造型收尾；运镜=前段静止锁定，约 3.0s 起单次连续推近，取景由宽幅收紧到群体中景；构图=画面重心由环境转向主体群，主体群比例逐步增大；转场=全片一条连续镜头，无切点
- 生成重点：三只哈士奇的群体动作同步性；连续推近机制；叠站承载关系；户外草坪场景一致性

### SEG001 | 0.0-1.0s | 宽幅建立镜头交代户外草坪场地与并排站立的三只哈士奇

- 参考功能 / 目标功能：`visual_display` → 宽幅建立镜头交代户外草坪场地与并排站立的三只哈士奇
- 生成画面（must_be_visible）：三只哈士奇并排站立、面朝镜头；修剪整齐的草坪地面；宽幅建立镜头
- 动作推进：三只哈士奇在草地上并排站立、面朝镜头，身体保持直立，右侧一只略微靠前
- 视角/构图：与哈士奇同高的平视视角，略带轻微俯角；宽幅全景建立镜头，主体群位于画面中央，平视略带俯角
- 运镜：静止锁定镜头（Static）：无机位移动、无变焦、无焦点变化
- 焦点/景深：主体群清晰，背景柔和虚化；全程无焦点切换
- 剪辑/转场：无切点；本段与相邻段在同一镜头内连续承接
- 节奏：参考视频约 0.5-1.0 秒量级的单一节拍，节奏从容不拖沓
- 场景迁移：适配 室内休息区改为户外草坪, 木地板与球场划线改为修剪草地, 室内道具全部移除；生成描述「开阔的户外草坪运动场：修剪整齐的绿色草地覆盖画面前景与中景，背景为低密度虚化的户外环境与远处建筑轮廓，白天自然光照，暖色低角度日光为主光、天空方向提供偏冷的环境光」
- 台词/口播/旁白/画面文字：无台词、无口播、无旁白、无画面文字；仅保留表演动作的信息推进
- 画内文字/logo 状态：`in_scene_text_logo_plan=[]`（本段无画内实体文字/logo）；`text_logo_policy.do_not_generate_unconfirmed_readable_text=True`
- 后期叠加状态：`post_overlay_plan=[]`（无字幕/标题/贴纸等后期项，H3 无需预留安全区）
- 特殊机制：（无）
- 使用素材：VIDEO_REF_001；IMG_USER_001
- 参考帧决策：requirement=`needed` / usage_role=`merged_reference` / needed_entities=ENT_HUSKY_LEFT, ENT_HUSKY_CENTER, ENT_HUSKY_RIGHT, ENT_LAWN_SCENE / needed_states=HSK_LEFT_S1, HSK_CENTER_S1, HSK_RIGHT_S1, LAWN_S1
- 审计/缺失项：negative_constraints=（无）；missing_inputs=（无）；generation_assumptions=['ASM001', 'ASM002']
- H3 prompt/request 状态：`prepared`（由 Step 9 写入 `09_h3_package/`，本 dry run 不提交）
- H3 视频状态：`skipped_dry_run`

### SEG002 | 1.0-2.0s | 三只哈士奇同步趴卧

- 参考功能 / 目标功能：`action_or_interaction` → 三只哈士奇同步趴卧
- 生成画面（must_be_visible）：三只哈士奇同步趴卧到草地；身体贴近地面的姿势
- 动作推进：三只哈士奇同时降低身体重心，前腿折叠，身体贴近草地转入趴卧姿势
- 视角/构图：与哈士奇同高的平视视角，略带轻微俯角；景别不变，仍为宽幅全景，主体群保持居中
- 运镜：静止锁定镜头，保持不动
- 焦点/景深：主体群清晰，背景柔和虚化；全程无焦点切换
- 剪辑/转场：无切点；本段与相邻段在同一镜头内连续承接
- 节奏：参考视频约 0.5-1.0 秒量级的单一节拍，节奏从容不拖沓
- 场景迁移：适配 室内休息区改为户外草坪, 木地板与球场划线改为修剪草地, 室内道具全部移除；生成描述「开阔的户外草坪运动场：修剪整齐的绿色草地覆盖画面前景与中景，背景为低密度虚化的户外环境与远处建筑轮廓，白天自然光照，暖色低角度日光为主光、天空方向提供偏冷的环境光」
- 台词/口播/旁白/画面文字：无台词、无口播、无旁白、无画面文字；仅保留表演动作的信息推进
- 画内文字/logo 状态：`in_scene_text_logo_plan=[]`（本段无画内实体文字/logo）；`text_logo_policy.do_not_generate_unconfirmed_readable_text=True`
- 后期叠加状态：`post_overlay_plan=[]`（无字幕/标题/贴纸等后期项，H3 无需预留安全区）
- 特殊机制：（无）
- 使用素材：VIDEO_REF_001；IMG_USER_001
- 参考帧决策：requirement=`needed` / usage_role=`person_reference` / needed_entities=ENT_HUSKY_LEFT, ENT_HUSKY_CENTER, ENT_HUSKY_RIGHT / needed_states=HSK_LEFT_S1, HSK_CENTER_S1, HSK_RIGHT_S1
- 审计/缺失项：negative_constraints=（无）；missing_inputs=（无）；generation_assumptions=['ASM001']
- H3 prompt/request 状态：`prepared`（由 Step 9 写入 `09_h3_package/`，本 dry run 不提交）
- H3 视频状态：`skipped_dry_run`

### SEG003 | 2.0-2.5s | 保持趴卧姿势，仅有轻微头部动作

- 参考功能 / 目标功能：`action_or_interaction` → 保持趴卧姿势，仅有轻微头部动作
- 生成画面（must_be_visible）：趴卧姿势被保持；同一场景、同一机位、同一光线
- 动作推进：保持趴卧姿势，只有轻微的头部与耳朵动作
- 视角/构图：与哈士奇同高的平视视角，略带轻微俯角；景别不变，画面稳定无移动
- 运镜：静止锁定镜头，保持不动
- 焦点/景深：主体群清晰，背景柔和虚化；全程无焦点切换
- 剪辑/转场：无切点；本段与相邻段在同一镜头内连续承接
- 节奏：参考视频约 0.5-1.0 秒量级的单一节拍，节奏从容不拖沓
- 场景迁移：适配 室内休息区改为户外草坪, 木地板与球场划线改为修剪草地, 室内道具全部移除；生成描述「开阔的户外草坪运动场：修剪整齐的绿色草地覆盖画面前景与中景，背景为低密度虚化的户外环境与远处建筑轮廓，白天自然光照，暖色低角度日光为主光、天空方向提供偏冷的环境光」
- 台词/口播/旁白/画面文字：无台词、无口播、无旁白、无画面文字；仅保留表演动作的信息推进
- 画内文字/logo 状态：`in_scene_text_logo_plan=[]`（本段无画内实体文字/logo）；`text_logo_policy.do_not_generate_unconfirmed_readable_text=True`
- 后期叠加状态：`post_overlay_plan=[]`（无字幕/标题/贴纸等后期项，H3 无需预留安全区）
- 特殊机制：（无）
- 使用素材：VIDEO_REF_001；IMG_USER_001
- 参考帧决策：requirement=`not_required` / usage_role=`none` / needed_entities= / needed_states=
- 审计/缺失项：negative_constraints=（无）；missing_inputs=（无）；generation_assumptions=（无）
- H3 prompt/request 状态：`prepared`（由 Step 9 写入 `09_h3_package/`，本 dry run 不提交）
- H3 视频状态：`skipped_dry_run`

### SEG004 | 2.5-3.0s | 三只哈士奇重新撑起四肢站起

- 参考功能 / 目标功能：`action_or_interaction` → 三只哈士奇重新撑起四肢站起
- 生成画面（must_be_visible）：三只哈士奇重新站起；动作连续、无切点
- 动作推进：三只哈士奇撑起四肢重新站起，动作同步、速度平缓
- 视角/构图：与哈士奇同高的平视视角，略带轻微俯角；景别不变，构图保持；镜头仍处于静止锁定状态
- 运镜：静止锁定镜头，保持不动
- 焦点/景深：主体群清晰，背景柔和虚化；全程无焦点切换
- 剪辑/转场：无切点；本段与相邻段在同一镜头内连续承接
- 节奏：参考视频约 0.5-1.0 秒量级的单一节拍，节奏从容不拖沓
- 场景迁移：适配 室内休息区改为户外草坪, 木地板与球场划线改为修剪草地, 室内道具全部移除；生成描述「开阔的户外草坪运动场：修剪整齐的绿色草地覆盖画面前景与中景，背景为低密度虚化的户外环境与远处建筑轮廓，白天自然光照，暖色低角度日光为主光、天空方向提供偏冷的环境光」
- 台词/口播/旁白/画面文字：无台词、无口播、无旁白、无画面文字；仅保留表演动作的信息推进
- 画内文字/logo 状态：`in_scene_text_logo_plan=[]`（本段无画内实体文字/logo）；`text_logo_policy.do_not_generate_unconfirmed_readable_text=True`
- 后期叠加状态：`post_overlay_plan=[]`（无字幕/标题/贴纸等后期项，H3 无需预留安全区）
- 特殊机制：（无）
- 使用素材：VIDEO_REF_001；IMG_USER_001
- 参考帧决策：requirement=`not_required` / usage_role=`none` / needed_entities= / needed_states=
- 审计/缺失项：negative_constraints=（无）；missing_inputs=（无）；generation_assumptions=（无）
- H3 prompt/request 状态：`prepared`（由 Step 9 写入 `09_h3_package/`，本 dry run 不提交）
- H3 视频状态：`skipped_dry_run`

### SEG005 | 3.0-4.0s | 走向镜头；同一镜头开始连续推近

- 参考功能 / 目标功能：`action_or_interaction` → 走向镜头；同一镜头开始连续推近
- 生成画面（must_be_visible）：三只哈士奇朝镜头前进；镜头约 3.0s 起连续推近；取景由宽幅收紧到群体中景
- 动作推进：三只哈士奇朝镜头方向迈步前进；同一镜头从宽幅开始连续推近，画面逐渐收紧到群体中景
- 视角/构图：与哈士奇同高的平视视角，略带轻微俯角；约 3.0s 起同一镜头开始连续推近，取景由环境全景收紧到群体中景，主体群在画面中逐步放大
- 运镜：约 3.0s 起执行单次连续推近（Dolly In）：缓慢、渐进、方向稳定，推近过程中动作不中断
- 焦点/景深：主体群清晰，背景柔和虚化；全程无焦点切换
- 剪辑/转场：无切点；本段与相邻段在同一镜头内连续承接
- 节奏：参考视频约 0.5-1.0 秒量级的单一节拍，节奏从容不拖沓
- 场景迁移：适配 室内休息区改为户外草坪, 木地板与球场划线改为修剪草地, 室内道具全部移除；生成描述「开阔的户外草坪运动场：修剪整齐的绿色草地覆盖画面前景与中景，背景为低密度虚化的户外环境与远处建筑轮廓，白天自然光照，暖色低角度日光为主光、天空方向提供偏冷的环境光」
- 台词/口播/旁白/画面文字：无台词、无口播、无旁白、无画面文字；仅保留表演动作的信息推进
- 画内文字/logo 状态：`in_scene_text_logo_plan=[]`（本段无画内实体文字/logo）；`text_logo_policy.do_not_generate_unconfirmed_readable_text=True`
- 后期叠加状态：`post_overlay_plan=[]`（无字幕/标题/贴纸等后期项，H3 无需预留安全区）
- 特殊机制：`SPM001` special_camera_or_focus（inherit）→ 同一镜头自约 3.0s 起执行单次连续推近，取景由宽幅环境全景收紧到三只哈士奇的群体中景
- 使用素材：VIDEO_REF_001；IMG_USER_001
- 参考帧决策：requirement=`needed` / usage_role=`scene_reference` / needed_entities=ENT_LAWN_SCENE / needed_states=LAWN_S1
- 审计/缺失项：negative_constraints=（无）；missing_inputs=（无）；generation_assumptions=（无）
- H3 prompt/request 状态：`prepared`（由 Step 9 写入 `09_h3_package/`，本 dry run 不提交）
- H3 视频状态：`skipped_dry_run`

### SEG006 | 4.0-4.3s | 左右两只并排停稳，中间一只踏上它们的背部

- 参考功能 / 目标功能：`action_or_interaction` → 左右两只并排停稳，中间一只踏上它们的背部
- 生成画面（must_be_visible）：左右两只哈士奇并排承重；中间一只前腿踏上下方两只背部
- 动作推进：左右两只哈士奇并排停稳并承重，中间一只抬起前腿踏上它们的背部
- 视角/构图：与哈士奇同高的平视视角，略带轻微俯角；推近持续，群体占据画面主要面积，主体群仍居中
- 运镜：连续推近继续，速度保持一致，无停顿、无来回
- 焦点/景深：主体群清晰，背景柔和虚化；全程无焦点切换
- 剪辑/转场：无切点；本段与相邻段在同一镜头内连续承接
- 节奏：参考视频约 0.5-1.0 秒量级的单一节拍，节奏从容不拖沓
- 场景迁移：适配 室内休息区改为户外草坪, 木地板与球场划线改为修剪草地, 室内道具全部移除；生成描述「开阔的户外草坪运动场：修剪整齐的绿色草地覆盖画面前景与中景，背景为低密度虚化的户外环境与远处建筑轮廓，白天自然光照，暖色低角度日光为主光、天空方向提供偏冷的环境光」
- 台词/口播/旁白/画面文字：无台词、无口播、无旁白、无画面文字；仅保留表演动作的信息推进
- 画内文字/logo 状态：`in_scene_text_logo_plan=[]`（本段无画内实体文字/logo）；`text_logo_policy.do_not_generate_unconfirmed_readable_text=True`
- 后期叠加状态：`post_overlay_plan=[]`（无字幕/标题/贴纸等后期项，H3 无需预留安全区）
- 特殊机制：（无）
- 使用素材：VIDEO_REF_001；IMG_USER_001
- 参考帧决策：requirement=`needed` / usage_role=`person_reference` / needed_entities=ENT_HUSKY_LEFT, ENT_HUSKY_CENTER, ENT_HUSKY_RIGHT / needed_states=HSK_LEFT_S1, HSK_CENTER_S1, HSK_RIGHT_S1
- 审计/缺失项：negative_constraints=（无）；missing_inputs=（无）；generation_assumptions=['ASM001']
- H3 prompt/request 状态：`prepared`（由 Step 9 写入 `09_h3_package/`，本 dry run 不提交）
- H3 视频状态：`skipped_dry_run`

### SEG007 | 4.3-5.8s | 叠站造型保持到结尾

- 参考功能 / 目标功能：`action_or_interaction` → 叠站造型保持到结尾
- 生成画面（must_be_visible）：叠站造型保持到片尾；中间哈士奇面向镜头
- 动作推进：叠站造型保持到片尾，中间一只面向镜头，下方两只仅做小幅平衡调整
- 视角/构图：与哈士奇同高的平视视角，略带轻微俯角；推近到位后保持紧凑群体中景，主体群填满画面中央
- 运镜：推近结束后保持稳定，不再改变机位与景别
- 焦点/景深：主体群清晰，背景柔和虚化；全程无焦点切换
- 剪辑/转场：无切点；本段与相邻段在同一镜头内连续承接
- 节奏：参考视频约 0.5-1.0 秒量级的单一节拍，节奏从容不拖沓
- 场景迁移：适配 室内休息区改为户外草坪, 木地板与球场划线改为修剪草地, 室内道具全部移除；生成描述「开阔的户外草坪运动场：修剪整齐的绿色草地覆盖画面前景与中景，背景为低密度虚化的户外环境与远处建筑轮廓，白天自然光照，暖色低角度日光为主光、天空方向提供偏冷的环境光」
- 台词/口播/旁白/画面文字：无台词、无口播、无旁白、无画面文字；仅保留表演动作的信息推进
- 画内文字/logo 状态：`in_scene_text_logo_plan=[]`（本段无画内实体文字/logo）；`text_logo_policy.do_not_generate_unconfirmed_readable_text=True`
- 后期叠加状态：`post_overlay_plan=[]`（无字幕/标题/贴纸等后期项，H3 无需预留安全区）
- 特殊机制：（无）
- 使用素材：VIDEO_REF_001；IMG_USER_001
- 参考帧决策：requirement=`needed` / usage_role=`person_reference` / needed_entities=ENT_HUSKY_LEFT, ENT_HUSKY_CENTER, ENT_HUSKY_RIGHT / needed_states=HSK_LEFT_S1, HSK_CENTER_S1, HSK_RIGHT_S1
- 审计/缺失项：negative_constraints=（无）；missing_inputs=（无）；generation_assumptions=（无）
- H3 prompt/request 状态：`prepared`（由 Step 9 写入 `09_h3_package/`，本 dry run 不提交）
- H3 视频状态：`skipped_dry_run`

## 素材绑定

| binding_id | asset_id | slot | H3 引用标签 | 用途 |
| --- | --- | --- | --- | --- |
| `AB001` | `VIDEO_REF_001` | `motion_camera_timing_reference` | `<video_1>` | 继承镜头结构、单镜头节奏、动作节拍与推近机制 |
| `AB002` | `IMG_USER_001` | `primary_subject_reference` | `<picture_1>` | 三只哈士奇的外观锚点与草坪地面证据 |

## 文字与 logo 策略

- `post_overlay_default`=True；`post_overlay_plan[]` 为空，本片无后期叠加项。
- `in_scene_text_logo_plan[]` 为空；目标侧无可读文字/logo 输入，`missing_inputs` 中 `M003=target_readable_text_or_logo` 记为 `missing_required_input`，策略 `omit_or_neutralize`。
- `render_post_overlay_in_video_model`=False；`do_not_generate_unconfirmed_readable_text`=True。

## 缺失项与生成假设

| missing_input_id | slot | status | resolution_policy | 阻塞参考帧 | 阻塞 H3 prompt/request |
| --- | --- | --- | --- | --- | --- |
| `M001` | `husky_individual_variants` | `missing_generate_fallback` | `generate_with_confirmed_assumption` | False | False |
| `M002` | `actor_presence` | `missing_required_input` | `omit_or_neutralize` | False | False |
| `M003` | `target_readable_text_or_logo` | `missing_required_input` | `omit_or_neutralize` | False | False |

| assumption_id | slot | 说明 | 来源 | 需要参考帧 | 风险 | 状态 |
| --- | --- | --- | --- | --- | --- | --- |
| `ASM001` | `actor_variant` | 第二、第三只哈士奇沿用用户素材的哈士奇外观体系，并通过面具深浅、眼部颜色与体型形成可见区分 | `shot_replication_policy` | True | `medium` | `proposed` |
| `ASM002` | `scene` | 目标场景为白天户外草坪，继承参考视频的暖主光/冷背景色温机制 | `user_confirmation` | True | `low` | `user_confirmed` |
| `ASM003` | `actor_presence` | 参考视频中的配角人物不迁移，左侧三分区由空旷草地承担 | `shot_replication_policy` | False | `low` | `proposed` |

## 复刻准备度

- `overall_status`: `ready_with_assumptions`；`blocking_item_ids`: （无阻塞项）；`missing_input_ids`: M001, M002, M003
- 来源：`05_replication_readiness/replication_readiness_check.json`

## 专业知识上下文（professional_prompt_context）

- `status`: `ready`；`profile_root`: `backend/profiles`
- 已加载 profile：
  - `VK-COMP-003`（composition）：`backend/profiles/视觉/画幅构图与空间/景别与机位视点/景别与机位视点.md`
  - `VK-COMP-002`（composition）：`backend/profiles/视觉/画幅构图与空间/单主体位置与画面留白/单主体与空间构图_优化示例.md`
  - `VK-COMP-004`（composition）：`backend/profiles/视觉/画幅构图与空间/前中后景与景深层次/前中后景与景深层次.md`
  - `VK-CAM-001`（camera_motion）：`backend/profiles/视觉/镜头运动与光学/摄影机位移旋转与复合运镜/摄影机位移旋转与复合运镜.md`
  - `VK-LIGHT-002`（lighting）：`backend/profiles/视觉/光线色彩与质感/色温调色与画面质感/色温调色与画面质感.md`
  - `VK-ACT-001`（action_continuity）：`backend/profiles/视觉/主体动作与连续性/主体动作、物体交互与出入画/主体动作物体交互与出入画.md`
  - `VK-EDIT-003`（editing）：`backend/profiles/视觉/剪辑转场与时间/镜头时长与剪辑节奏/镜头时长与剪辑节奏.md`
- knowledge_terms：建立镜头（Wide / Establishing Shot）, 全景（Full / Long Shot）, 三分构图（Rule of Threes）, 视觉层级（Visual Hierarchy）, 前景遮挡 + 中景主体 + 浅景深, 推近（Dolly In）, 静止镜头（Static）, 暖色温（Warm）与冷色温（Cool）对比, 统一调色（Global Color Consistency）, 时间顺序描述（Temporal Order）, 主体揭示（Subject Revealing）, 揭示后保持
- validation_flags：['script_narrative_profiles_directory_empty_not_loaded']

## 审计约束（negative_constraint_policy）

- `prompt_weight`: `low`；`default_prompt_visibility`: `audit_only`；`allowed_prompt_visibility`: ['audit_only']
- 负向约束只进入审计与 checklist，不复制进 H3 prompt；本片无需要写入 prompt 的负向短句。

## 校验标记（validation_flags）

- `reference_video_single_shot_no_scene_split`
- `push_in_start_approximated_between_2_5s_and_3_2s`
- `climb_contact_moment_approximated`
- `unsupported_audio_kept_as_placeholder`
- `no_person_transferred_from_reference`

## 状态索引

- Step 1-6 产物：`00_inputs/`、`01_reference_video_analysis/`、`03_asset_inventory/`、`04_target_asset_analysis/`、`05_replication_readiness/`、`06_replication_outline/`
- Step 7 参考帧计划：`07_reference_frame_plan/reference_frame_plan.json`
- Step 8 参考帧生成：`08_reference_frames/`
- Step 9 H3 prompt/request：`09_h3_package/h3_prompt_draft.md`、`h3_prompt_lint_report.json`、`h3_submit_prompt.md`、`h3_request.json`
- Step 10 H3 视频生成：`skipped_dry_run`（本 dry run 不创建 `10_h3_video_output/`）
- 运行索引：`run_manifest.json`
