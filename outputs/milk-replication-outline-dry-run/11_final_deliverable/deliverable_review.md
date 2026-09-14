# 最终交付审阅

- run: `milk-replication-outline-dry-run` / status: `ready_with_assumptions` / dry_run: `True`
- timeline_unit_count: 11 / temporal_segment_count: 12 / h3_prompt_shot_count: 11
- H3 prompt `[Shot N]` 为 prompt-level shots（对应 timeline unit），非 reference-level shots；内部 `temporal_segments[]` 为参考级节拍。

## 逐 segment 审阅
### U001 / seg_001_1  0.0-2.0s
- 参考功能 -> 目标功能: visual_display -> 开场先给目标主体与钩子
- 场景迁移: 空间类型：现代居家客厅；前景/中景/背景：前景沙发与茶几、中景人物、背景落地窗；置景：浅灰蓝色布艺沙发、原木茶几、绿植；光线：落地窗自然侧光，柔和均匀；色调：浅灰+暖木+一点绿；材质：布艺、原木、棉麻；背景密度：中低；景深：深焦，环境可读；氛围：清爽温暖
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: [('subtitle', 'missing_required_input')]
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_003'], frames=[]
- 缺失输入: ['mi_004'] / 状态: ready_with_assumptions

### U002 / seg_002_1  2.0-3.0s
- 参考功能 -> 目标功能: visual_display -> 强化目标产品主视觉
- 场景迁移: 空间类型：现代居家客厅；前景/中景/背景：前景沙发与茶几、中景人物、背景落地窗；置景：浅灰蓝色布艺沙发、原木茶几、绿植；光线：落地窗自然侧光，柔和均匀；色调：浅灰+暖木+一点绿；材质：布艺、原木、棉麻；背景密度：中低；景深：深焦，环境可读；氛围：清爽温暖
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: [('title', 'missing_required_input')]
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_003'], frames=[]
- 缺失输入: ['mi_004'] / 状态: ready_with_assumptions

### U003 / seg_003_1  3.0-4.0s
- 参考功能 -> 目标功能: visual_display -> 用多场景快切证明目标产品适用于多种生活场景
- 场景迁移: 空间类型：街角现代茶饮店；前景/中景/背景：前景操作台、中景人物、背景饮品墙；置景：浅色木纹吧台、玻璃罐、绿植、暖光吊灯；光线：室内暖光+窗外自然光；色调：奶油+浅木+绿；材质：木纹、玻璃、哑光漆；背景密度：中；景深：中；氛围：明亮清新
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: 无
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_004'], frames=[]
- 缺失输入: [] / 状态: ready_with_assumptions

### U004 / seg_004_1  4.0-5.0s
- 参考功能 -> 目标功能: text_overlay_or_information_reveal -> 释放产品信息节拍
- 场景迁移: 空间类型：挑高现代商场中庭；前景/中景/背景：前景栏杆与扶梯、中景人物、背景多层商铺；置景：玻璃栏板、绿植装置、浅灰石材地面；光线：顶部天窗自然光；色调：浅灰+白+绿；材质：玻璃、浅灰石材、金属；背景密度：中高但有秩序；景深：深；氛围：通透现代
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: [('caption', 'missing_required_input')]
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_005'], frames=[]
- 缺失输入: ['mi_004'] / 状态: ready_with_assumptions

### U005 / seg_005_1  5.0-6.0s
- 参考功能 -> 目标功能: visual_display -> 用普通大号道具强化记忆并延续多场景证明
- 场景迁移: 空间类型：城市户外绿荫人行步道；前景/中景/背景：前景行道树、中景人物、背景现代建筑；置景：浅灰铺装、行道树、长椅；光线：树荫下柔和自然光；色调：浅灰+绿；材质：石材铺装、树皮、金属；背景密度：中；景深：深；氛围：清新自然
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: 无
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_006'], frames=[]
- 缺失输入: [] / 状态: ready_with_assumptions

### U006 / seg_006_1  6.0-7.0s
- 参考功能 -> 目标功能: visual_display -> 延续多场景适用性证明
- 场景迁移: 空间类型：现代健身工作室；前景/中景/背景：前景器械、中景人物、背景镜墙与器械墙；置景：哑铃架、瑜伽垫、镜墙；光线：均匀顶光；色调：浅灰+白+原木；材质：金属、橡胶、镜面；背景密度：中；景深：中；氛围：干净有活力
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: 无
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_007'], frames=[]
- 缺失输入: [] / 状态: ready_with_assumptions

### U007 / seg_007_1  7.0-8.0s
- 参考功能 -> 目标功能: text_overlay_or_information_reveal -> 释放口感/体验信息节拍
- 场景迁移: 空间类型：挑高现代商场中庭；前景/中景/背景：前景栏杆与扶梯、中景人物、背景多层商铺；置景：玻璃栏板、绿植装置、浅灰石材地面；光线：顶部天窗自然光；色调：浅灰+白+绿；材质：玻璃、浅灰石材、金属；背景密度：中高但有秩序；景深：深；氛围：通透现代
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: [('caption', 'missing_required_input')]
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_005'], frames=[]
- 缺失输入: ['mi_004'] / 状态: ready_with_assumptions

### U008 / seg_008_1  8.0-9.0s
- 参考功能 -> 目标功能: visual_display -> 延续多场景证明并强化产品同框
- 场景迁移: 空间类型：现代健身工作室；前景/中景/背景：前景器械、中景人物、背景镜墙与器械墙；置景：哑铃架、瑜伽垫、镜墙；光线：均匀顶光；色调：浅灰+白+原木；材质：金属、橡胶、镜面；背景密度：中；景深：中；氛围：干净有活力
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: 无
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_007'], frames=[]
- 缺失输入: [] / 状态: ready_with_assumptions

### U009 / seg_009_1  9.0-10.0s
- 参考功能 -> 目标功能: text_overlay_or_information_reveal -> 再次强调目标产品名称节拍
- 场景迁移: 空间类型：现代城市广场；前景/中景/背景：前景广场铺装、中景人物、背景玻璃幕墙建筑；置景：浅灰铺装、绿植花池、玻璃幕墙；光线：明亮户外自然光；色调：浅灰+蓝+绿；材质：石材、玻璃、金属；背景密度：中；景深：深；氛围：开阔都市
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: [('caption', 'missing_required_input')]
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_008'], frames=[]
- 缺失输入: ['mi_004'] / 状态: ready_with_assumptions

### U010 / seg_010_1  10.0-11.0s
- 参考功能 -> 目标功能: action_or_interaction -> 从展示转向使用前的期待
- 场景迁移: 空间类型：现代简约室内休息区；前景/中景/背景：前景矮几、中景人物、背景圆拱装饰与浅色家具；置景：米色圆拱装饰、浅色布艺椅、落地灯；光线：室内柔和暖光；色调：米白+浅木；材质：布艺、木、哑光漆；背景密度：低；景深：中；氛围：温暖放松
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: [('cta', 'missing_required_input')]
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_009'], frames=[]
- 缺失输入: ['mi_004'] / 状态: ready_with_assumptions

### U011 / seg_011_1  11.0-13.0s
- 参考功能 -> 目标功能: closing_or_prompt -> 以目标使用动作+结尾标语收束
- 场景迁移: 空间类型：现代简约室内休息区；前景/中景/背景：前景矮几、中景人物、背景圆拱装饰与浅色家具；置景：米色圆拱装饰、浅色布艺椅、落地灯；光线：室内柔和暖光；色调：米白+浅木；材质：布艺、木、哑光漆；背景密度：低；景深：中；氛围：温暖放松
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: [('cta', 'missing_required_input')]
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_009'], frames=[]
- 缺失输入: ['mi_004'] / 状态: ready_with_assumptions

### U011 / seg_011_2  13.0-15.0s
- 参考功能 -> 目标功能: closing_or_prompt -> 以目标使用动作+结尾标语收束
- 场景迁移: 空间类型：现代简约室内休息区；前景/中景/背景：前景矮几、中景人物、背景圆拱装饰与浅色家具；置景：米色圆拱装饰、浅色布艺椅、落地灯；光线：室内柔和暖光；色调：米白+浅木；材质：布艺、木、哑光漆；背景密度：低；景深：中；氛围：温暖放松
- 主体/动作迁移: reference_milk_bottle -> 东方树叶乌龙茶原味茶饮料500ml瓶装（adapt）
- 画面内实体文字/logo: [('product', 'ready')]
- 后期叠加: [('cta', 'missing_required_input')]
- 参考帧决策: role=person_reference, entities=['ent_002', 'ent_009'], frames=[]
- 缺失输入: ['mi_004'] / 状态: ready_with_assumptions

## 参考帧状态
- plan: `07_reference_frame_plan/reference_frame_plan.json` (8 帧)
- ready_frame_ids: ['rf_001', 'rf_002', 'rf_003', 'rf_004', 'rf_005', 'rf_006', 'rf_007', 'rf_008']
- H3 白名单素材数: 10；mapping 参考图上限 5

## H3 状态
- 打包: `completed`，产物 `09_h3_package/`；validator 通过（0 issues）。
- 可提交 request: `09_h3_package/h3_request.json`（未提交）。
- 视频生成: `skipped_dry_run`（dry-run 边界，未调用 H3 视频生成）。