# 复刻大纲审阅稿

- schema_version: `common_replication_outline.v2`
- status: `ready_with_assumptions`
- generation_scope: `single_generation_task`
- 目标视频: 欧美女性户外篮球场舞蹈复刻, 10.1s, 9:16, 768P, 1 个参考镜头
- 参考视频: `test_data/dance/2_2_case2-H3-original.mp4` (10.1s, single_continuous_take)
- 时间精度: 截断到小数点后一位, 不四舍五入

## 参考元素处理计划

| element_id | 类型 | 观察到的参考元素 | decision | 目标绑定 |
| --- | --- | --- | --- | --- |
| `RET01` | time_structure | 单连续镜头 0.0-10.1s, 时长约10.1s | `inherit` | U001 |
| `RET02` | shot_structure | 固定机位, 竖屏9:16居中全身构图 | `inherit` | U001 |
| `RET03` | action_structure | 连续舞步节拍: 双手侧展→交叉腿步与重心切换→抬腿/前伸点地→双拳屈肘摆动→右臂上举→收尾 | `adapt` | U001, U001_S001, U001_S002, U001_S003, U001_S004, U001_S005 |
| `RET04` | person_or_body | 年轻男性舞者, 兜帽戴起, 米白连帽卫衣, 棕色短裤, 白袜白鞋, 短深色头发 | `adapt` | U001, E_PERSON_1 |
| `RET05` | scene_content | 户外混凝土天台/平台, 米黄高墙+金属栏杆+高灯杆+阴天天空, 左右红色看台, 地面白线 | `adapt` | U001, E_SCENE_1 |
| `RET06` | visual_style | 阴天漫射自然光, 柔和阴影, 低饱和真实拍摄质感 | `inherit` | U001, E_ATMOS_1 |
| `RET07` | text_or_ui | not_observed: 参考视频无可读文字/logo/水印/字幕/UI | `discard` | U001 |
| `RET08` | unsupported_audio | ASR识别到英文歌词式演唱内容(疑似唱歌/音乐层) | `discard` | U001 |
| `RET09` | other | special_composition/presentation/transition/camera_or_focus 均为 not_observed; micro_action observed(点地/抬腿, 握拳屈肘, 头部轻侧倾) | `inherit` | U001, U001_S001, U001_S002, U001_S003, U001_S004, U001_S005 |
| `RET10` | transition | 无转场(单连续镜头) | `discard` | U001 |

## 全局外观库

### 目标女性舞者 (`E_PERSON_1`, person_appearance)

- 欧美女性成年表演者, 非特定身份(不可识别)
- 女性身体形态, 身材匀称, 面向镜头正面表演
- 发型: 非兜帽的自然长发或利落扎发(与参考兜帽短发形成可见差异)
- 妆容: 自然妆容, 清爽运动感
- 服装: 运动休闲套装, 暖色或亮色系(如珊瑚红/亮橙/薄荷绿运动上衣+同系运动短裤或长裤), 明显区别于参考米白连帽卫衣+棕色短裤
- 配饰: 简约运动发带或手腕毛巾等普通运动配饰
- 气质: 自信、活力, 街舞表演感
- 可见差异锚点: 女性性别呈现 / 非兜帽发型 / 暖色/亮色运动套装替代米白卫衣+棕色短裤 / 移除兜帽造型
- 引用分镜: U001_S001, U001_S002, U001_S003, U001_S004, U001_S005

### 户外篮球场 (`E_SCENE_1`, scene_appearance)

- 空间类型: 户外标准半场/全场篮球场
- 地面: 室外球场塑胶或水泥地面, 带清晰白色或黄色场地划线(中圈/三分线/罚球线)
- 背景锚点: 正后方或侧后方篮球架+篮板+篮圈(金属支柱)
- 环境: 球场周边金属围网, 场边长椅或矮护栏
- 光线: 阴天漫射自然光, 柔和阴影, 无强逆光
- 色调: 低饱和真实色, 场地常用蓝绿或红棕塑胶色作为主色块, 与参考米黄墙+红色看台明显不同
- 景深/密度: 中景地面延伸到背景篮架与围网, 背景密度中等
- 氛围: 白天户外运动、真实拍摄质感
- 可见差异锚点: 户外篮球场替代混凝土天台/平台 / 篮球架/篮板/围网替代米黄高墙+金属栏杆+高灯杆 / 球场塑胶色替代米黄墙+红色看台
- 引用分镜: U001_S001, U001_S002, U001_S003, U001_S004, U001_S005

### 阴天漫射真实拍摄氛围 (`E_ATMOS_1`, style_atmosphere)

- 阴天漫射自然光, 阴影柔和
- 低饱和写实色调
- 真实live-action拍摄质感
- 固定机位稳定画面, 无风格化滤镜
- 引用分镜: U001_S001, U001_S002, U001_S003, U001_S004, U001_S005

## 记忆点迁移计划

| memory_id | 类型 | 保留机制 | 目标侧改编 | 仅审计 |
| --- | --- | --- | --- | --- |
| `vm_001` | composition | 单连续镜头; 固定机位无切换; 居中全身构图; 竖屏9:16构图关系 | 主体改为目标女性舞者后微调站姿, 保持居中全身构图 | 不新增切镜或拆分镜头; 不迁移参考视频专属场地内容 |
| `vm_002` | camera_motion | 固定机位静止镜头; 无变焦无移焦 | 目标视频保持同一机位与景别关系 | 不加入运镜或焦点变化 |
| `vm_003` | micro_action | 连续舞步的动作阶段顺序; 交叉腿步与重心切换; 抬腿/点地节拍; 屈肘握拳摆动; 动作衔接连续性 | 动作由目标女性舞者在户外篮球场完成, 服装与造型适配目标侧 | 不迁移源侧男性舞者身份与具体服装 |
| `vm_004` | lighting_texture | 阴天漫射自然光; 柔和阴影; 低饱和色调; 真实拍摄质感 | 户外篮球场环境适配同类阴天漫射光, 保持同一光线逻辑 | 不迁移参考视频具体场地/看台/墙面颜色作为目标内容 |
| `sm_001` | opening_hook | 开篇直接进入主体动作; 单一连续镜头结构 | 目标视频开篇同样直接进入女性舞者在篮球场的舞蹈动作 | 不迁移源侧人物身份与具体场地 |
| `sm_002` | emotional_arc | 动作节奏弧线(起步-推进-收尾); 无切镜的连续推进 | 目标人物在同一镜头内复现同样的节奏弧线 | 不新增文字或口播 |

## 场景迁移

- `ST01` `preserve_scene_style`: 户外白天场景; 阴天漫射自然光与柔和阴影; 低饱和写实色调; 前景主体/中景地面/背景结构的空间深度关系; 真实拍摄质感
- `ST02` `adapt_scene_content`: 场地由混凝土天台/平台替换为户外篮球场; 背景锚点替换为篮球架/篮板/篮圈/金属围网; 地面替换为球场塑胶或水泥地面并带场地划线; 移除米黄高墙、金属栏杆、高灯杆与左右红色看台

## 时间轴

### U001 (0.0-10.1s, 10.1s) `ready_with_assumptions`

- 素材绑定: h3_video_1:motion_camera_timing_reference, E_PERSON_1:person_appearance_reference, E_SCENE_1:scene_appearance_reference

| segment | 时间 | reference_function | 生成画面 | 动作/运镜 | 文本 | 使用素材 | 参考帧 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `U001_S001` | 0.0-2.0s | `opening_hook` | 开场: 目标女性舞者居中站立, 双手抬至体侧手掌张开, 随后右腿抬起点地、双臂展开 | 目标女性舞者双手抬至体侧后右腿点地, 手臂侧展, 身体小幅摆动; 脚部接触球场地面 / 固定机位, 竖屏9:16, 居中全身构图; 平视机位 | 无文字 | E_PERSON_1, E_SCENE_1 | E_PERSON_1, E_SCENE_1 | `ready_with_assumptions` |
| `U001_S002` | 2.0-4.5s | `proof` | 2.0-4.5s 目标女性舞者双腿大幅分开后连续交叉腿步, 双拳屈肘置于体侧, 重心下沉并切换 | 双腿分开下沉 -> 连续交叉腿步 -> 重心左右切换; 双拳屈肘随节奏摆动; 头部轻微倾斜 / 固定机位不变, 居中全身构图; 主体仍在画面中央 | 无文字 | E_PERSON_1, E_SCENE_1 | E_PERSON_1, E_SCENE_1 | `ready_with_assumptions` |
| `U001_S003` | 4.5-6.5s | `action_or_interaction` | 4.5-6.5s 目标女性舞者右腿高抬屈膝后恢复站立, 双拳屈肘保持节奏 | 右腿高抬屈膝 -> 落地恢复站立 -> 小幅点地; 双拳屈肘摆动 / 固定机位, 居中全身; 抬腿时保持全身在画面内 | 无文字 | E_PERSON_1, E_SCENE_1 | E_PERSON_1, E_SCENE_1 | `ready_with_assumptions` |
| `U001_S004` | 6.5-9.0s | `action_or_interaction` | 6.5-9.0s 目标女性舞者继续交叉腿步与踏步, 右腿前外侧点地, 右臂上举握拳靠近头部 | 交叉腿步 -> 右腿前外侧点地 -> 右腿屈膝抬起 -> 右臂上举握拳靠近头部, 左臂下垂 / 固定机位, 居中全身构图; 手臂上举时仍在画面内 | 无文字 | E_PERSON_1, E_SCENE_1 | E_PERSON_1, E_SCENE_1 | `ready_with_assumptions` |
| `U001_S005` | 9.0-10.1s | `closing_or_prompt` | 9.0-10.1s 目标女性舞者双脚接近并拢, 双拳屈肘收于身前, 完成收尾定格 | 双脚并拢站直 -> 双拳屈肘收于身前 -> 收尾定格 / 固定机位, 居中全身构图保持到结束 | 无文字 | E_PERSON_1, E_SCENE_1 | E_PERSON_1, E_SCENE_1 | `ready_with_assumptions` |

## 脚本与文字

- 剧本内容: `none` — 目标侧未提供台词、口播、旁白或画面文字; 参考视频仅识别到英文歌词式演唱内容, 属 unsupported_skipped
- 文字/logo 政策: 后期叠加默认开启, 不在视频模型中渲染; 不生成未确认的可读文字
- unsupported_audio: `unsupported_skipped` (音乐、BGM、音效、疑似唱歌、声音情绪与卡点节奏保持 unsupported_skipped, 不参与复刻; H3 handoff 音乐行固定为交付指令, 不推断歌词/音效/卡点)

## 音频

- 状态: `unsupported_skipped`
- 音乐、BGM、音效、疑似唱歌、声音情绪和卡点节奏当前保持 `unsupported_skipped`。

## 参考帧摘要

- plan_required: `True`, frame_requirement_level: `required`
- 人物实体 1 个, 场景实体 1 个, 计划参考帧 2 张
- plan_path: `07_reference_frame_plan/reference_frame_plan.json`
- <E_PERSON_1> 目标女性舞者规划 1 张 person_reference
- <E_SCENE_1> 户外篮球场规划 1 张 scene_reference
- E_ATMOS_1 为氛围实体, 不规划参考帧

## 缺失项与生成假设

- missing_inputs: 无

- `ga1` (target_person_appearance): 目标人物为一位非特定身份的欧美(欧美裔)女性表演者; 具体发型、妆容与服装由模型按非身份识别方式生成, 需与参考视频男性舞者外观形成可见差异
  - 可见差异锚点: 性别与身体形态不同(女性表演者) / 服装色系改为非米白/黑白的运动休闲装(如暖色/亮色运动套装) / 发型采用非兜帽长发或扎发 / 避免复刻参考兜帽卫衣+棕色短裤造型
- `ga2` (target_scene): 目标场景为户外篮球场; 具体球场表面颜色、篮架、围网、周边建筑等普通场景道具按篮球场常规推断
  - 可见差异锚点: 场景类型从混凝土天台/平台改为户外篮球场 / 主要背景锚点改为篮球架/篮板/球场地线与围网 / 移除参考视频的米黄高墙与左右红色看台作为目标内容

## 专业知识上下文

- status: `ready`
- 生成简述: 竖屏 9:16 单连续长镜头, 固定机位静止镜头, 全景全身取景并用中心构图把目标女性舞者居中放置; 户外篮球场白天场景, 阴天漫射自然光, 柔和阴影, 低饱和写实色调与真实拍摄质感; 全程不移动、不变焦、不改变焦点, 无切镜; 目标女性舞者按实际发生先后完成 起步→交叉腿步与重心切换→抬腿/点地→屈肘摆动→收尾 的完整动作节奏弧线, 动作不中断、主体不出画。

| 术语 | 类别 | profile | 应用对象 |
| --- | --- | --- | --- |
| 全景（Full / Long Shot） | composition | `VK-COMP-003` | U001, U001_S001, U001_S002, U001_S003, U001_S004, U001_S005 |
| 中心构图（Centered Composition） | composition | `VK-COMP-002` | U001, U001_S001, U001_S002, U001_S003, U001_S004, U001_S005 |
| 9:16 竖屏 | composition | `VK-COMP-001` | target_video, U001 |
| 静止镜头（Static） | camera_motion | `VK-CAM-001` | U001, U001_S001, U001_S002, U001_S003, U001_S004, U001_S005 |
| 自然光（Natural Light） | lighting | `VK-LIGHT-001` | E_ATMOS_1, U001 |
| 时间顺序描述（Temporal Order） | action_continuity | `VK-ACT-001` | U001_S001, U001_S002, U001_S003, U001_S004, U001_S005 |
| 沉思型节奏 | editing | `VK-EDIT-003` | U001, target_video |

## 审计项

- 新知识库来源: VK-COMP-003, VK-COMP-002, VK-COMP-001, VK-CAM-001, VK-LIGHT-001, VK-ACT-001, VK-EDIT-003
- 准备度检查: `ready_with_assumptions` (blocking: 无)
- validation_flags: `prompt_shots_from_temporal_segments`, `reference_video_single_continuous_take_no_transition`
- 源侧人物身份、场地元素、可读文字仅进入审计, 不进入目标 prompt。

