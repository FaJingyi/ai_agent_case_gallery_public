# 复刻大纲审阅稿（replication_outline.md）

- 状态：ready_with_assumptions
- 生成范围：single_generation_task
- 时间精度：one_decimal / truncate
- timeline_unit 数：10；temporal_segment 数：17
- 说明：下游 prompt 中的 `[Shot N]` 为 prompt-level shots（由 temporal_segments 生成），不是参考镜头的新拆分。

## 目标与世界设定
- 目标主体：东方树叶乌龙茶瓶
- 人物实体：E_PERSON_01
- 场景实体：E_SCENE_01, E_SCENE_02, E_SCENE_03

## 场景迁移
| 场景实体 | 参考场景 | 目标场景描述 | 可见差异 |
| --- | --- | --- | --- |
| E_SCENE_01 | 白色护墙板客厅 / 明亮大房间 / 室内房间 | 明亮现代客厅：浅色木地板、米白布艺沙发、圆形木质茶几、带纱帘的落地窗与绿植，暖白墙面，日间柔和自然光，画面干净通透 | 由白色护墙板+雕塑+米色扶手椅的自持宅邸客厅改为浅木+米白+绿植的现代公寓客厅 |
| E_SCENE_02 | 咖啡馆 / 室内农场 | 阳光茶室：暖色木桌与座椅、格栅落地窗、绿植与陶制茶具，午后窗光落于桌面，暖木色与米色调，安静温润 | 由黑白地砖咖啡馆与室内动物农场改为暖木色阳光茶室 |
| E_SCENE_03 | 户外砖路 / 健身房 / 户外广场 | 城市绿荫广场：浅灰石材铺装、行道树绿荫、长椅与步道，背景为弧形现代建筑，明亮日光，开阔清爽 | 由砖路+红色雨棚+停放汽车改为绿荫广场+浅灰铺装+弧形建筑，并替代原健身房场景 |

## 记忆点迁移
- `vm_001` (visual) 保留：鱼眼锁定机位、前景物体放大、主体位于中景的强制透视层次、边缘外弯与球面感；适配：前景物体改为东方树叶乌龙茶瓶、中景人物与场景改为目标世界
- `vm_002` (visual) 保留：双手举起商品朝向镜头的展示手势、物品正对镜头并贴近、微笑与轻微晃动；适配：举起的目标商品改为东方树叶乌龙茶瓶
- `vm_003` (visual) 保留：硬切快剪节奏、每个 shot 约 1 秒、跨 shot 维持同一展示手势与构图机制；适配：场景改为目标场景世界
- `vm_004` (visual) 保留：开盖、送至唇边、仰头倾斜饮用、放下、较长停留；适配：容器与商品改为东方树叶乌龙茶瓶
- `vm_005` (visual) 保留：平视中景、主体居中、人物持商品于胸前建立开场；适配：商品改为东方树叶乌龙茶瓶、人物外观与服装改为目标侧设定
- `sm_001` (script) 保留：开场即人物+商品同框、平视中景亮相构图、配合口号的微笑亮相姿态；适配：人物与商品改为目标侧设定、开场文字按缺失处理或使用目标文案
- `sm_002` (script) 保留：重复的举物向镜头展示手势、约每秒一镜的快切节奏、跨场景并列的证明结构；适配：被举物体统一改为目标商品、场景改为目标场景世界
- `sm_003` (script) 保留：文字随镜头出现的信息节奏、中上/中下安全区位置、卖点信息递进结构；适配：文字内容改为目标侧文案；缺失时保留节拍并标记缺失
- `sm_004` (script) 保留：完整使用动作链、结尾镜头停留较久、收束口号的出现位置与节奏；适配：容器与商品改为目标商品、结尾文字按缺失处理或使用目标文案
- 音频：unsupported_skipped（音乐/BGM/音效/声音情绪/卡点节奏不参与复刻）

## 分镜时间轴（segment 级）
| Unit | Segment | 时间 | 参考功能 | 目标功能 | 场景迁移 | 主体/动作迁移 | 画面内文字/logo | 后期叠加 | 参考帧 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| VS001_SH001 | VS001_SH001_S1 | 0.0-2.0s | visual_display | 建立人物与目标商品同框 | 明亮现代客厅：浅色木地板、米白布艺沙发、圆形木茶几、落地窗纱帘与绿植 | 女子在客厅把目标商品持于胸前微笑，身体轻微晃动 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_01 | 无 | ready |
| VS001_SH001 | VS001_SH001_S2 | 2.0-2.3s | text_overlay_or_information_reveal | 开场文字出现节拍（目标文案缺失） | 明亮现代客厅：浅色木地板、米白布艺沙发、圆形木茶几、落地窗纱帘与绿植 | 女子在客厅把目标商品持于胸前微笑，身体轻微晃动 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_01 | 无 | ready |
| VS001_SH002 | VS001_SH002_S1 | 2.3-3.3s | visual_display | 把目标商品推向镜头前展示并露出包装文字 | 同客厅空间，鱼眼镜头下画面边缘外弯 | 双臂前伸把目标商品举向镜头，瓶体贴近镜头放大 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_01 | 无 | ready |
| VS001_SH003 | VS001_SH003_S1 | 3.3-4.3s | visual_display | 以普通茶点延续展示手势 | 阳光茶室：暖色木桌椅、格栅落地窗、绿植与陶制茶具 | 双手托茶点盘向镜头前伸，茶点贴近镜头放大，目标商品在桌面可见 | ready | 无 | frame_person_01、frame_scene_02 | 无 | ready |
| VS001_SH004 | VS001_SH004_S1 | 4.3-4.8s | visual_display | 举瓶向镜头展示 | 同阳光茶室空间，窗光落于桌面 | 举瓶微笑，瓶体贴近镜头放大 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_02 | 无 | ready |
| VS001_SH004 | VS001_SH004_S2 | 4.8-5.3s | text_overlay_or_information_reveal | 卖点文字出现节拍（目标文案缺失） | 同阳光茶室空间，窗光落于桌面 | 举瓶微笑，瓶体贴近镜头放大 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_02 | 无 | ready |
| VS001_SH005 | VS001_SH005_S1 | 5.3-6.3s | visual_display | 在户外场景展示商品 | 城市绿荫广场：浅灰石材铺装、行道树绿荫、长椅与远处现代建筑 | 双手举瓶前伸，瓶体贴近镜头放大 | ready | 无 | frame_person_01、frame_scene_03 | 无 | ready |
| VS001_SH006 | VS001_SH006_S1 | 6.3-7.3s | visual_display | 把商品置于运动情境展示 | 同城市绿荫广场，明亮日光 | 运动后双手举瓶微笑，瓶体贴近镜头放大 | ready | 无 | frame_person_01、frame_scene_03 | 无 | ready |
| VS001_SH007 | VS001_SH007_S1 | 7.3-7.8s | visual_display | 商品与普通茶点一并展示 | 同阳光茶室空间 | 双手把目标商品与茶点一并举向镜头 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_02 | 无 | ready |
| VS001_SH007 | VS001_SH007_S2 | 7.8-8.3s | text_overlay_or_information_reveal | 口感文字出现节拍（目标文案缺失） | 同阳光茶室空间 | 双手把目标商品与茶点一并举向镜头 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_02 | 无 | ready |
| VS001_SH008 | VS001_SH008_S1 | 8.3-9.3s | visual_display | 运动后展示商品 | 同城市绿荫广场 | 拉伸后举瓶，瓶体贴近镜头放大 | ready | 无 | frame_person_01、frame_scene_03 | 无 | ready |
| VS001_SH009 | VS001_SH009_S1 | 9.3-10.0s | visual_display | 建筑前展示商品 | 同城市绿荫广场，背景为弧形现代建筑 | 双手举瓶微笑，瓶体贴近镜头放大 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_03 | 无 | ready |
| VS001_SH009 | VS001_SH009_S2 | 10.0-10.8s | text_overlay_or_information_reveal | 商品名文字出现节拍（目标文案缺失） | 同城市绿荫广场，背景为弧形现代建筑 | 双手举瓶微笑，瓶体贴近镜头放大 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_03 | 无 | ready |
| VS001_SH010 | VS001_SH010_S1 | 10.8-11.5s | action_or_interaction | 持瓶展示 | 同明亮现代客厅，结尾镜头回到室内 | 右手持目标商品并略举展示 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_01 | 无 | ready |
| VS001_SH010 | VS001_SH010_S2 | 11.5-12.5s | action_or_interaction | 拔盖并把瓶口送至唇边 | 同明亮现代客厅，结尾镜头回到室内 | 抬手拔开瓶盖，把瓶口缓缓送到唇边 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_01 | 无 | ready |
| VS001_SH010 | VS001_SH010_S3 | 12.5-14.5s | action_or_interaction | 仰头倾斜饮用 | 同明亮现代客厅，结尾镜头回到室内 | 仰头倾斜瓶身饮用，瓶身保持清晰可见 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_01 | 无 | ready |
| VS001_SH010 | VS001_SH010_S4 | 14.5-15.0s | closing_or_prompt | 放下瓶身并出现结尾文字节拍（目标文案缺失） | 同明亮现代客厅，结尾镜头回到室内 | 放低瓶身，收束动作 | ready | subtitle:missing_required_input | frame_person_01、frame_scene_01 | 无 | ready |

## 参考帧计划
- plan_required=True, person=1, scene=3, frames=4
- 计划路径：07_reference_frame_plan/reference_frame_plan.json

## 负向约束（audit）
- 不得出现参考视频的原人物身份与服装特征
- 不得出现参考视频原商品包装上的品牌文字与规格数字
- 不得迁移参考视频专属道具（蛋糕、大蟹、笑脸面包、哑铃）
- 不得生成未确认的功效、价格、活动或规格声明
- 字幕、结尾提示与贴纸由后期叠加，H3 只生成 clean plate 并预留安全区
