# 复刻大纲审阅稿

- schema: `common_replication_outline.v2` / status: `ready_with_assumptions` / scope: `single_generation_task`
- 目标视频: 15.0s, 9:16, 主体: 东方树叶乌龙茶原味茶饮料500ml瓶装
- 参考视频结构: montage, 11 个 timeline unit
- timeline_unit_count: 11 / temporal_segment_count: 12 / h3_prompt_shot_count: 11
- 说明: H3 prompt 中的 `[Shot N]` 为 prompt-level shots（对应当前 timeline unit），不是 reference-level shots；每个 unit 内部仍保留 `temporal_segments[]`。

## 显式替换绑定
- milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装；覆盖 unit: U001, U002, U003, U004, U005, U006, U007, U008, U009, U010, U011；状态: fully_covered（每镜均含可见替换产品）

## 全局外观库
- `ent_001` target_product_东方树叶乌龙茶 (main_subject_appearance, single_entity): 细长圆柱形透明塑料瓶，净含量500ml；透明螺旋瓶盖；瓶内金黄色/琥珀色茶汤
- `ent_002` person_非可识别成年女性 (person_appearance, single_entity) / 参考帧 rf_001: 年龄印象：25-30岁成年女性；体型：中等身形；发型：及肩深棕微卷发
- `ent_010` key_prop_普通大号道具组 (key_prop_appearance, single_entity): 视觉功能：作为前景框架遮挡并强化记忆；物品：巨型柠檬塔模型、巨型茶壶模型、普通大号遮阳帽、普通哑铃；位置：镜头前景、正对镜头、遮挡画面上半部
- `ent_011` atmosphere_明亮高调真实商业短视频 (style_atmosphere, single_entity): 光线氛围：明亮均匀高调光；色彩倾向：明亮暖调，各场景主色协调；真实感：真实拍摄质感
- `ent_003` scene_001_明亮居家客厅 (scene_appearance, single_entity) / 参考帧 rf_002: 空间类型：现代居家客厅；前景/中景/背景：前景沙发与茶几、中景人物、背景落地窗；置景：浅灰蓝色布艺沙发、原木茶几、绿植
- `ent_004` scene_002_街角现代茶饮店 (scene_appearance, single_entity) / 参考帧 rf_003: 空间类型：街角现代茶饮店；前景/中景/背景：前景操作台、中景人物、背景饮品墙；置景：浅色木纹吧台、玻璃罐、绿植、暖光吊灯
- `ent_005` scene_003_现代商场中庭 (scene_appearance, single_entity) / 参考帧 rf_004: 空间类型：挑高现代商场中庭；前景/中景/背景：前景栏杆与扶梯、中景人物、背景多层商铺；置景：玻璃栏板、绿植装置、浅灰石材地面
- `ent_006` scene_004_城市户外绿荫步道 (scene_appearance, single_entity) / 参考帧 rf_005: 空间类型：城市户外绿荫人行步道；前景/中景/背景：前景行道树、中景人物、背景现代建筑；置景：浅灰铺装、行道树、长椅
- `ent_007` scene_005_现代健身工作室 (scene_appearance, single_entity) / 参考帧 rf_006: 空间类型：现代健身工作室；前景/中景/背景：前景器械、中景人物、背景镜墙与器械墙；置景：哑铃架、瑜伽垫、镜墙
- `ent_008` scene_006_现代城市广场 (scene_appearance, single_entity) / 参考帧 rf_007: 空间类型：现代城市广场；前景/中景/背景：前景广场铺装、中景人物、背景玻璃幕墙建筑；置景：浅灰铺装、绿植花池、玻璃幕墙
- `ent_009` scene_007_现代简约室内 (scene_appearance, single_entity) / 参考帧 rf_008: 空间类型：现代简约室内休息区；前景/中景/背景：前景矮几、中景人物、背景圆拱装饰与浅色家具；置景：米色圆拱装饰、浅色布艺椅、落地灯

## 分镜与内部节拍
### U001  0.0-2.0s  (VS001:shot1)
- 生成画面: 开场：女性正面站在明亮居家客厅，双手在腹部位置握住东方树叶瓶，微笑对镜头，给出开场钩子
- 动作/运镜: 女性正面站立，双手在腹部位置握住东方树叶瓶，身体轻微晃动，微笑看向镜头，镜头静止；动作阶段为展示起点 / 机位: 静止镜头 / 平视中景，腰以上取景、中心构图，主体居中、竖屏 9:16，底部预留字幕安全区
  - [seg_001_1 0.0-2.0s] 参考功能: visual_display -> 目标功能: 开场先给目标主体与钩子
    - 场景迁移: 空间类型：现代居家客厅；前景/中景/背景：前景沙发与茶几、中景人物、背景落地窗；置景：浅灰蓝色布艺沙发、原木茶几、绿植；
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；女性身体轻微晃动、微笑对镜头；双手稳定握瓶
    - 画面内实体文字/logo: product:ready；后期叠加: subtitle:missing_required_input
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_003'] used_frames=[]
    - 缺失输入: ['mi_004']；状态: ready_with_assumptions

### U002  2.0-3.0s  (VS001:shot2)
- 生成画面: 广角/鱼眼低角度仰拍：女性将东方树叶瓶高举，瓶身朝向镜头形成强透视，人物在背景变小
- 动作/运镜: 女性双手将东方树叶瓶高高举起，瓶身朝向镜头，人物在背景中显得较小，保持微笑；动作阶段为产品主视觉强化 / 机位: 广角/鱼眼仰拍（静止机位+轻微上仰） / 广角/鱼眼低角度仰拍、前景产品占据画面上半部、近大远小夸张
  - [seg_002_1 2.0-3.0s] 参考功能: visual_display -> 目标功能: 强化目标产品主视觉
    - 场景迁移: 空间类型：现代居家客厅；前景/中景/背景：前景沙发与茶几、中景人物、背景落地窗；置景：浅灰蓝色布艺沙发、原木茶几、绿植；
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；瓶子由腹部位置变为高举过头；镜头由平视变为低角度仰拍
    - 画面内实体文字/logo: product:ready；后期叠加: title:missing_required_input
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_003'] used_frames=[]
    - 缺失输入: ['mi_004']；状态: ready_with_assumptions

### U003  3.0-4.0s  (VS001:shot3)
- 生成画面: 街角现代茶饮店：女性一手在另一手前景托举东方树叶瓶，另一手托举巨型柠檬塔普通道具
- 动作/运镜: 女性双手托举物品展示在镜头前，低角度使道具显得巨大；东方树叶瓶在另一手前景保持可见 / 机位: 静止镜头 / 前景特写，低角度、中心构图、前景道具占据画面大部
  - [seg_003_1 3.0-4.0s] 参考功能: visual_display -> 目标功能: 用多场景快切证明目标产品适用于多种生活场景
    - 场景迁移: 空间类型：街角现代茶饮店；前景/中景/背景：前景操作台、中景人物、背景饮品墙；置景：浅色木纹吧台、玻璃罐、绿植、暖光吊灯
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；双手托举动作，道具正对镜头；东方树叶瓶在另一手前景保持稳定可见
    - 画面内实体文字/logo: product:ready；后期叠加: 无
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_004'] used_frames=[]
    - 缺失输入: []；状态: ready_with_assumptions

### U004  4.0-5.0s  (VS001:shot4)
- 生成画面: 现代商场中庭：女性双手托举东方树叶瓶，瓶身正对镜头
- 动作/运镜: 女性双手托举东方树叶瓶，瓶身正对镜头；动作阶段为产品展示 / 机位: 静止镜头 / 中近景，平视、中心构图
  - [seg_004_1 4.0-5.0s] 参考功能: text_overlay_or_information_reveal -> 目标功能: 释放产品信息节拍
    - 场景迁移: 空间类型：挑高现代商场中庭；前景/中景/背景：前景栏杆与扶梯、中景人物、背景多层商铺；置景：玻璃栏板、绿植装置、浅灰石材
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；双手托举产品正对镜头，保持微笑
    - 画面内实体文字/logo: product:ready；后期叠加: caption:missing_required_input
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_005'] used_frames=[]
    - 缺失输入: ['mi_004']；状态: ready_with_assumptions

### U005  5.0-6.0s  (VS001:shot5)
- 生成画面: 城市户外绿荫步道：女性托举巨型茶壶普通道具作为前景框架，东方树叶瓶在另一手前景可见
- 动作/运镜: 女性双手托举巨大茶壶道具，道具占据画面大部分，人物在后方；东方树叶瓶在另一手前景保持可见 / 机位: 静止镜头 / 前景遮挡大特写、前景道具遮挡画面上半部、平视偏仰
  - [seg_005_1 5.0-6.0s] 参考功能: visual_display -> 目标功能: 用普通大号道具强化记忆并延续多场景证明
    - 场景迁移: 空间类型：城市户外绿荫人行步道；前景/中景/背景：前景行道树、中景人物、背景现代建筑；置景：浅灰铺装、行道树、长椅；光线
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；双手托举巨大道具，道具正对镜头遮挡人物
    - 画面内实体文字/logo: product:ready；后期叠加: 无
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_006'] used_frames=[]
    - 缺失输入: []；状态: ready_with_assumptions

### U006  6.0-7.0s  (VS001:shot6)
- 生成画面: 现代健身工作室：女性运动装双手托举东方树叶瓶，瓶身正对镜头
- 动作/运镜: 女性双手托举东方树叶瓶，瓶身正对镜头；动作阶段为产品展示 / 机位: 静止镜头 / 中近景，平视、中心构图
  - [seg_006_1 6.0-7.0s] 参考功能: visual_display -> 目标功能: 延续多场景适用性证明
    - 场景迁移: 空间类型：现代健身工作室；前景/中景/背景：前景器械、中景人物、背景镜墙与器械墙；置景：哑铃架、瑜伽垫、镜墙；光线：均匀
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；双手托举产品正对镜头
    - 画面内实体文字/logo: product:ready；后期叠加: 无
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_007'] used_frames=[]
    - 缺失输入: []；状态: ready_with_assumptions

### U007  7.0-8.0s  (VS001:shot7)
- 生成画面: 现代商场中庭：女性托举普通大号遮阳帽作为前景框架，东方树叶瓶在另一手前景可见
- 动作/运镜: 女性双手托举普通大号遮阳帽，帽子正对镜头并遮挡部分面部；东方树叶瓶在另一手前景保持可见 / 机位: 静止镜头 / 前景遮挡特写、中心构图
  - [seg_007_1 7.0-8.0s] 参考功能: text_overlay_or_information_reveal -> 目标功能: 释放口感/体验信息节拍
    - 场景迁移: 空间类型：挑高现代商场中庭；前景/中景/背景：前景栏杆与扶梯、中景人物、背景多层商铺；置景：玻璃栏板、绿植装置、浅灰石材
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；双手托举大号道具，道具遮挡部分面部
    - 画面内实体文字/logo: product:ready；后期叠加: caption:missing_required_input
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_005'] used_frames=[]
    - 缺失输入: ['mi_004']；状态: ready_with_assumptions

### U008  8.0-9.0s  (VS001:shot8)
- 生成画面: 现代健身工作室：女性双手握住一对普通哑铃，东方树叶瓶在前景可见
- 动作/运镜: 女性双手握住一对普通哑铃举在胸前/头部高度，哑铃正对镜头；东方树叶瓶在前景保持可见 / 机位: 静止镜头 / 前景特写，平视、中心构图
  - [seg_008_1 8.0-9.0s] 参考功能: visual_display -> 目标功能: 延续多场景证明并强化产品同框
    - 场景迁移: 空间类型：现代健身工作室；前景/中景/背景：前景器械、中景人物、背景镜墙与器械墙；置景：哑铃架、瑜伽垫、镜墙；光线：均匀
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；双手握住哑铃举在胸前/头部高度，哑铃正对镜头
    - 画面内实体文字/logo: product:ready；后期叠加: 无
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_007'] used_frames=[]
    - 缺失输入: []；状态: ready_with_assumptions

### U009  9.0-10.0s  (VS001:shot9)
- 生成画面: 现代城市广场：女性双手托举东方树叶瓶，瓶身正对镜头，再次强调产品名称节拍
- 动作/运镜: 女性双手托举东方树叶瓶，瓶身正对镜头；动作阶段为产品名称强调 / 机位: 静止镜头 / 中近景，平视、中心构图
  - [seg_009_1 9.0-10.0s] 参考功能: text_overlay_or_information_reveal -> 目标功能: 再次强调目标产品名称节拍
    - 场景迁移: 空间类型：现代城市广场；前景/中景/背景：前景广场铺装、中景人物、背景玻璃幕墙建筑；置景：浅灰铺装、绿植花池、玻璃幕墙；
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；双手托举产品正对镜头
    - 画面内实体文字/logo: product:ready；后期叠加: caption:missing_required_input
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_008'] used_frames=[]
    - 缺失输入: ['mi_004']；状态: ready_with_assumptions

### U010  10.0-11.0s  (VS001:shot10)
- 生成画面: 现代简约室内：女性右手单手举起东方树叶瓶，左手自然下垂，进入展示到使用的过渡
- 动作/运镜: 女性右手单手举起东方树叶瓶，左手自然下垂或放在身侧；动作阶段为展示动作，作为动作匹配的起点 / 机位: 静止镜头 / 中景，平视、中心构图
  - [seg_010_1 10.0-11.0s] 参考功能: action_or_interaction -> 目标功能: 从展示转向使用前的期待
    - 场景迁移: 空间类型：现代简约室内休息区；前景/中景/背景：前景矮几、中景人物、背景圆拱装饰与浅色家具；置景：米色圆拱装饰、浅色布艺
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；右手单手举起产品，左手自然下垂，作为连续动作起点
    - 画面内实体文字/logo: product:ready；后期叠加: cta:missing_required_input
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_009'] used_frames=[]
    - 缺失输入: ['mi_004']；状态: ready_with_assumptions

### U011  11.0-15.0s  (VS001:shot11)
- 生成画面: 同室内场景：女性将东方树叶瓶举到嘴边仰头饮用，动作连贯；结尾保持并预留结尾标语位
- 动作/运镜: 女性将东方树叶瓶举到嘴边仰头饮用，动作连贯，从举起瓶子到喝下；11.0-13.0s 为饮用动作，13.0-15.0s 为饮用后保持并预留结尾标语 / 机位: 静止镜头 / 中近景，平视、中心构图
  - [seg_011_1 11.0-13.0s] 参考功能: closing_or_prompt -> 目标功能: 以目标使用动作+结尾标语收束
    - 场景迁移: 空间类型：现代简约室内休息区；前景/中景/背景：前景矮几、中景人物、背景圆拱装饰与浅色家具；置景：米色圆拱装饰、浅色布艺
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；瓶子从举起状态变为瓶口接触嘴唇的饮用状态
    - 画面内实体文字/logo: product:ready；后期叠加: cta:missing_required_input
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_009'] used_frames=[]
    - 缺失输入: ['mi_004']；状态: ready_with_assumptions
  - [seg_011_2 13.0-15.0s] 参考功能: closing_or_prompt -> 目标功能: 以目标使用动作+结尾标语收束
    - 场景迁移: 空间类型：现代简约室内休息区；前景/中景/背景：前景矮几、中景人物、背景圆拱装饰与浅色家具；置景：米色圆拱装饰、浅色布艺
    - 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）；瓶子从举起状态变为瓶口接触嘴唇的饮用状态
    - 画面内实体文字/logo: product:ready；后期叠加: cta:missing_required_input
    - 参考帧决策: person_reference used_entity=['ent_002', 'ent_009'] used_frames=[]
    - 缺失输入: ['mi_004']；状态: ready_with_assumptions

## 参考帧摘要
- plan_required=True, plan_path=07_reference_frame_plan/reference_frame_plan.json, planned=8, ready_frame_ids=['rf_001', 'rf_002', 'rf_003', 'rf_004', 'rf_005', 'rf_006', 'rf_007', 'rf_008']

## 不支持音频 / 缺失项
- unsupported_audio: {"enabled": false, "status": "unsupported_skipped", "unsupported_items": ["bgm_structure", "music_detection", "beat_alignment", "sfx_events", "singing_or_suspected_singing_detection", "voice_timing_as_audio", "audio_mood_curve"]}
- missing_inputs: ['mi_001', 'mi_002', 'mi_003', 'mi_004', 'mi_005']
- validation_flags: ['scene_entities_from_generation_assumption', 'post_overlay_text_missing_optional', 'explicit_replacement_fully_covered', 'script_profiles_directory_empty']

## H3 打包状态
- 状态: `ready_for_h3_submission_dry_run`；产物见 `09_h3_package/`（`h3_packager_input.md` / `minimax_h3_prompt.md` / `reference_mapping.md` / `pre_generation_checklist.md` / `h3_request.json`）。
- H3 视频生成: `skipped_dry_run`（未提交、未调用视频生成）。