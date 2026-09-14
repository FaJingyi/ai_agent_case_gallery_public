# 参考视频复刻大纲（审阅稿）

- schema: `common_replication_outline.v2`  status: **ready_with_assumptions**  scope: `single_generation_task`
- 参考视频: `test_data/dance/2_2_case2-H3-original.mp4` (10.125s, vertical)
- 目标: 参考视频生成一条新视频，一位欧美女性在户外篮球场上跳舞
- 时间精度: truncate 到 0.1s
- timeline_unit_count: **1**  temporal_segment_count: **5**

## 参考元素处理决策

| element | type | decision | 保留/改写 |
| --- | --- | --- | --- |
| ret_001 | time_structure | inherit | 保留: 单镜头连续时长结构, 最终时长在一镜头内保持完整 ｜ 改写: — |
| ret_002 | shot_structure | inherit | 保留: 单镜头一镜到底的结构, 无剪辑点 ｜ 改写: — |
| ret_003 | composition | inherit | 保留: 竖屏画幅, 全身取景, 中心构图, 主体上下留空间 ｜ 改写: — |
| ret_004 | camera | inherit | 保留: 固定机位, 平视机位, 焦点锁定主体 ｜ 改写: — |
| ret_005 | visual_style | inherit | 保留: 户外自然漫射光, 冷调低饱和, 写实纪实质感 ｜ 改写: 按用户场景（户外篮球场）落地为白天户外自然光，保持同一光线机制 |
| ret_006 | scene_content | adapt | 保留: 户外开阔场地类型, 混凝土硬质地面与白色画线, 中等景深的空间层次, 自然天空背景 ｜ 改写: 用户文本指定场景：户外篮球场, 篮球场地面画线、篮球架/篮筐、球场围网或场边设施, 与参考看台场地形成可见差异：空间类型从看台/跑道改为篮球场，配色与场边陈设不同 |
| ret_007 | person_or_body | adapt | 保留: 单一人物主体承接全部舞蹈动作, 全身可见，动作链由身体完成 ｜ 改写: 用户文本指定目标主体：一位欧美女性, 与参考主体形成可见差异：性别不同；采用不同于参考的运动休闲穿搭（例如亮色运动上衣+深色运动短/紧身裤），发型与体型按欧美成年女性生成 |
| ret_008 | action_structure | inherit | 保留: 动作链的时间顺序与连续性, 重心左右转移与上下起伏, 单脚支撑/点地的接触关系, 节拍停顿 ｜ 改写: 具体舞种与舞步按目标主体重新编排，保持同一节奏结构 |
| ret_009 | dialogue_or_voiceover | discard | 保留: — ｜ 改写: — |
| ret_010 | text_or_ui | discard | 保留: — ｜ 改写: — |

## 全局外观元素库（第二层去重）

### person1 (person_appearance) — person1
- 种族与气质：欧美成年女性，自信、运动感
- 年龄印象：20-30 岁
- 体型：匀称、四肢修长，适合舞蹈动作
- 发型：中长自然发（可扎起或披散），与参考男性兜帽造型明显不同
- 妆容：自然运动妆，非浓妆
- 服装：不同于参考米白卫衣+棕色短裤的运动休闲穿搭，例如亮色/饱和色运动上衣搭配深色运动短裤或紧身裤
- 配饰：可从简（无品牌 logo、无可读文字）
- 与参考的可见差异: 性别与参考男性主体不同；服装配色与参考米白+棕色明显不同；发型与参考兜帽造型不同

### scene1 (scene_appearance) — scene1
- 空间类型：户外篮球场（区别于参考看台/跑道场地）
- 前景：硬质沥青或塑胶球场地面，带白色球场画线
- 中景：主体所在球场空间
- 背景：篮球架/篮筐、场边围网或看台、自然天空
- 光线：白天户外自然漫射光，冷调、低饱和、低对比
- 材质：硬质地面、金属篮球架、围网
- 背景密度：中等，主体周围保留可辨识但不过度杂乱的背景
- 景深：中等景深，主体清晰、背景轻度虚化
- 氛围：写实、纪录感、户外运动
- 与参考的可见差异: 空间类型从看台/跑道改为篮球场；场边出现篮球架/篮筐而非参考红色看台座椅；配色与场边陈设明显不同

### prop1 (key_prop_appearance) — scene1 篮球架/篮筐
- 视觉功能：建立篮球场空间属性，位于背景中景
- 形状：地面篮球架与篮筐/篮板
- 材质：金属支架与篮板
- 颜色：中性或透明篮板，无品牌 logo
- 与主体关系：仅作为环境陈设，不与主体交互
- 与参考的可见差异: 参考视频无篮球架/篮筐，属目标场景新增的普通陈设

### atmosphere1 (style_atmosphere) — style_atmosphere
- 光线氛围：户外白天自然漫射光，无强烈阴影
- 色彩倾向：冷调、低饱和度、低对比
- 真实感：写实纪录质感
- 质感/镜头感：竖屏 9:16 手机竖拍质感，中等景深
- 美术方向：真实户外运动场景，不做风格化调色

## 时间轴分镜

### SEG001  0.0-1.0s (1.0s)
- 参考功能: `visual_display` ｜ 目标功能: `opening_pose_and_establish`
- 生成画面: 一位欧美女性舞者全身站在户外篮球场中央，双手自然下垂，静止起手，背景可见篮球架与场边设施
- 动作/运镜: 动作=主体双脚分开站立、双手自然下垂，重心居中，尚未开始舞蹈；运镜=固定机位，无推拉摇移，焦点锁定主体
- 场景迁移: 户外篮球场（场景1）：户外篮球场硬质地面与白色球场画线，背景可见篮球架/篮筐、场边围网或看台，呈现户外开阔空间；与参考视频看台场地在空间类型、配色和场边陈设上明显不同。
- 画面内实体文字/logo: 无（`in_scene_text_logo_plan` 为空）
- 后期叠加: 无（`post_overlay_plan` 为空，H3 只出 clean plate）
- 参考帧: ['rf_person_001', 'rf_scene_001'] (role=person_reference)
- 缺失输入: 无 ｜ 生成假设: ['ga_001', 'ga_003']
- 状态: `ready_with_assumptions`

### SEG002  1.0-2.0s (1.0s)
- 参考功能: `action_or_interaction` ｜ 目标功能: `arm_extension_phrase`
- 生成画面: 欧美女性舞者在篮球场上双臂向两侧伸展并收回，配合身体律动开始舞蹈
- 动作/运镜: 动作=主体双臂向两侧伸展并收回，肩与手臂带动躯干轻微摆动，双脚保持支撑；运镜=固定机位，无推拉摇移，焦点锁定主体
- 场景迁移: 户外篮球场（场景1）：户外篮球场硬质地面与白色球场画线，背景可见篮球架/篮筐、场边围网或看台，呈现户外开阔空间；与参考视频看台场地在空间类型、配色和场边陈设上明显不同。
- 画面内实体文字/logo: 无（`in_scene_text_logo_plan` 为空）
- 后期叠加: 无（`post_overlay_plan` 为空，H3 只出 clean plate）
- 参考帧: ['rf_person_001', 'rf_scene_001'] (role=person_reference)
- 缺失输入: 无 ｜ 生成假设: ['ga_001', 'ga_003']
- 状态: `ready_with_assumptions`

### SEG003  2.0-4.0s (2.0s)
- 参考功能: `action_or_interaction` ｜ 目标功能: `punch_beat_phrase`
- 生成画面: 欧美女性舞者在篮球场上做类似握拳前伸再收回的节拍动作，身体重心左右移动
- 动作/运镜: 动作=主体双拳在胸前与向前之间往复，重心随节拍左右移动；运镜=固定机位，无推拉摇移，焦点锁定主体
- 场景迁移: 户外篮球场（场景1）：户外篮球场硬质地面与白色球场画线，背景可见篮球架/篮筐、场边围网或看台，呈现户外开阔空间；与参考视频看台场地在空间类型、配色和场边陈设上明显不同。
- 画面内实体文字/logo: 无（`in_scene_text_logo_plan` 为空）
- 后期叠加: 无（`post_overlay_plan` 为空，H3 只出 clean plate）
- 参考帧: ['rf_person_001', 'rf_scene_001'] (role=person_reference)
- 缺失输入: 无 ｜ 生成假设: ['ga_001', 'ga_003']
- 状态: `ready_with_assumptions`

### SEG004  4.0-7.0s (3.0s)
- 参考功能: `action_or_interaction` ｜ 目标功能: `cross_step_kick_phrase`
- 生成画面: 欧美女性舞者在篮球场上做交叉步、踢腿与转身晃动，重心左右转移明显
- 动作/运镜: 动作=主体腿部交叉步与踢腿，重心在左右脚之间转移，手臂配合摆动；运镜=固定机位，无推拉摇移，焦点锁定主体
- 场景迁移: 户外篮球场（场景1）：户外篮球场硬质地面与白色球场画线，背景可见篮球架/篮筐、场边围网或看台，呈现户外开阔空间；与参考视频看台场地在空间类型、配色和场边陈设上明显不同。
- 画面内实体文字/logo: 无（`in_scene_text_logo_plan` 为空）
- 后期叠加: 无（`post_overlay_plan` 为空，H3 只出 clean plate）
- 参考帧: ['rf_person_001', 'rf_scene_001'] (role=person_reference)
- 缺失输入: 无 ｜ 生成假设: ['ga_001', 'ga_003']
- 状态: `ready_with_assumptions`

### SEG005  7.0-10.1s (3.1s)
- 参考功能: `action_or_interaction` ｜ 目标功能: `single_leg_groove_and_settle`
- 生成画面: 欧美女性舞者在篮球场上做单脚支撑、另一脚点地或抬起的流畅舞步，动作持续推进到镜头结束
- 动作/运镜: 动作=主体以单脚支撑完成点地与抬腿，重心保持稳定，手臂随律动摆动至镜头结束；运镜=固定机位，无推拉摇移，焦点锁定主体
- 场景迁移: 户外篮球场（场景1）：户外篮球场硬质地面与白色球场画线，背景可见篮球架/篮筐、场边围网或看台，呈现户外开阔空间；与参考视频看台场地在空间类型、配色和场边陈设上明显不同。
- 画面内实体文字/logo: 无（`in_scene_text_logo_plan` 为空）
- 后期叠加: 无（`post_overlay_plan` 为空，H3 只出 clean plate）
- 参考帧: ['rf_person_001', 'rf_scene_001'] (role=person_reference)
- 缺失输入: 无 ｜ 生成假设: ['ga_001', 'ga_003']
- 状态: `ready_with_assumptions`

## 记忆点迁移

- vm_001 (visual) 保留: 连续舞蹈动作链的时间顺序；重心左右转移与上下起伏；单脚支撑/点地的接触关系；节拍停顿 / 改写: 舞种与舞步按目标舞者重新编排；主体改为欧美女性，场景改为户外篮球场
- sm_001 (script) 保留: 静—动的节奏弧线；动作能量逐步推进；结尾自然收束 / 改写: 具体舞步与结尾呈现按目标主体改写；无口播/CTA 保持为空

## 参考帧摘要

- plan_required=True person=1 scene=1 planned=2 status=ready

## H3 打包 / 视频生成状态

- H3 打包: 待生成 `09_h3_package/`（本 dry-run 到 H3 request/package 为止）
- H3 视频生成: `not_submitted`（dry-run 边界，不提交/不运行 H3）
- 音频: `unsupported_skipped`（疑似歌曲人声）

## 缺失与禁止项

- 缺失: mi_001 slot=actor_identity status=missing_generate_fallback policy=generate_with_confirmed_assumption
- 缺失: mi_002 slot=post_overlay_text status=neutralize_allowed policy=omit_or_neutralize
- prompt guardrails:
  - 目标主体为一位欧美女性，不迁移参考男性身份与其服装造型。
  - 目标场景为户外篮球场，不复制参考看台/跑道场地陈设；画面不生成任何可读文字或 logo。
