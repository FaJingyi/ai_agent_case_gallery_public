# 复刻大纲人工审阅稿

- 主产物：`06_replication_outline/replication_outline.json`（机器读取依据，本文件仅为人工审阅稿）
- 状态：`ready_with_assumptions`
- 生成范围：`single_generation_task`，目标时长 15.0 秒，竖屏 9:16
- 时间精度：one_decimal / truncate（截断，不四舍五入）
- timeline_units：10 个（shot 级）
- temporal_segments：13 个
- 参考帧计划：`07_reference_frame_plan/reference_frame_plan.json`，planned_frame_count=6，selected_h3_image_count=6
- 目标素材：`test_data/milk/user_input/东方树叶.jpg`（resolved_slot=product，asset_id=`asset_f0be03649f94433d8e62d4aa94e0c6ea`）
- 未支持音频：`unsupported_skipped`（音乐、BGM、音效、疑似唱歌、声音情绪、卡点节奏、对白）

## 主体与场景映射

| 目标实体 | 类型 | 使用镜头 |
| --- | --- | --- |
| 表演者甲（石板蓝亚麻开衫，齐肩深棕直发） | person | shot1, shot2, shot4, shot7, shot10 |
| 表演者乙（芥末黄衬衫，栗棕低马尾） | person | shot3, shot5, shot6, shot8, shot9 |
| 东方树叶乌龙茶 500ml PET 瓶（用户素材） | product | shot1, shot2, shot4, shot6, shot9, shot10 |
| 晨光混凝土阁楼影棚 | scene | shot1, shot2 |
| 现代茶饮品鉴台 | scene | shot3 |
| 玻璃中庭温室 | scene | shot4, shot7 |
| 镜面舞蹈教室 | scene | shot6, shot8 |
| 海滨木栈道 | scene | shot5 |
| 浅灰铺装屋顶露台 | scene | shot9 |
| 亚麻窗帘阅读角 | scene | shot10 |

## 逐 segment 审阅

| 时间范围 | 参考功能 | 目标功能 | 场景迁移 | 动作迁移 | 画内文字/logo | 后期叠加 | 参考帧决策 | 缺失输入 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0.0-1.0s | visual_display | target_product_and_presenter_reveal | 晨光混凝土阁楼影棚｜空间类型由参考视频的居家客厅改为混凝土阁楼影棚；主色由绿/米色改为米白/冷灰，靠枕由绿色改为锈橙色 | 表演者甲：由自然站立进入胸前托瓶，动作幅度小，微笑保持 | `isl_ts_001_package`（ready） | 无 | person_reference：ent_person_a、ent_scene_loft、ent_subject_product | 无（继承全局） | ready_with_assumptions |
| 1.0-1.6s | text_overlay_or_information_reveal | target_opening_text_safe_area | 晨光混凝土阁楼影棚｜空间类型由参考视频的居家客厅改为混凝土阁楼影棚；主色由绿/米色改为米白/冷灰，靠枕由绿色改为锈橙色 | 表演者甲：人物保持托瓶姿态，仅在安全区内留出图形层位置，画面无新增实体 | `isl_ts_002_package`（ready） | `ov_ts_002_opening_line_safe_area`（neutralize_allowed） | person_reference：ent_person_a、ent_scene_loft、ent_subject_product | 无（继承全局） | ready_with_assumptions |
| 1.6-2.8s | visual_display | target_fisheye_product_push | 晨光混凝土阁楼影棚｜空间类型由参考视频的居家客厅改为混凝土阁楼影棚；主色由绿/米色改为米白/冷灰，靠枕由绿色改为锈橙色 | 表演者甲：动作由胸前举持连续推进到完全伸展，终点为瓶身停在画面正中心 | `isl_ts_003_package`（ready） | 无 | person_reference：ent_person_a、ent_scene_loft、ent_subject_product | 无（继承全局） | ready_with_assumptions |
| 2.8-3.8s | action_or_interaction | target_prop_push_fisheye | 现代茶饮品鉴台｜空间类型由参考视频的咖啡馆/店铺改为茶饮品鉴台；地面由花纹地砖改为浅灰石板，主色由暖木色+花纹改为深胡桃木+浅灰 | 表演者乙：由台面持碟转为双手向镜头推送，终点为蛋糕停在画面正中心 | 无 | 无 | person_reference：ent_person_b、ent_scene_tea_lab | 无（继承全局） | ready_with_assumptions |
| 3.8-5.0s | visual_display | target_label_reveal_with_claim_safe_area | 玻璃中庭温室｜空间类型由参考视频的室内农场/村庄缩小布景改为玻璃中庭温室；陈设由微缩房屋与干草改为水磨石地面与高大蕨类 | 表演者甲：由中位举持推进到完全高举，终点为标签面朝向镜头并停稳 | `isl_ts_005_package`（ready） | `ov_ts_005_product_claim_safe_area`（neutralize_allowed） | person_reference：ent_person_a、ent_scene_atrium、ent_subject_product | 无（继承全局） | ready_with_assumptions |
| 5.0-6.0s | action_or_interaction | target_prop_push_fisheye | 海滨木栈道｜空间类型由参考视频的户外街道改为海滨木栈道；背景由车流与骑楼改为海面与白色售卖亭，主色改为木色/浅蓝 | 表演者乙：由站立持物转为双手前推，终点为茶青枝条停在画面正中心 | 无 | 无 | person_reference：ent_person_b、ent_scene_boardwalk | 无（继承全局） | ready_with_assumptions |
| 6.0-7.1s | visual_display | target_label_reveal_with_claim_safe_area | 镜面舞蹈教室｜空间类型由参考视频的器械健身房改为镜面舞蹈教室；地面由带数字格的地面改为浅枫木地板，墙色改为墨蓝 | 表演者乙：由中位举持推进到完全高举，终点为标签面朝向镜头并停稳 | `isl_ts_007_package`（ready） | `ov_ts_007_product_claim_safe_area`（neutralize_allowed） | person_reference：ent_person_b、ent_scene_dance_studio、ent_subject_product | 无（继承全局） | ready_with_assumptions |
| 7.1-8.2s | action_or_interaction | target_prop_push_with_taste_claim_safe_area | 玻璃中庭温室｜空间类型由参考视频的室内农场/村庄缩小布景改为玻璃中庭温室；陈设由微缩房屋与干草改为水磨石地面与高大蕨类 | 表演者甲：由胸位持碟转为双手前推，终点为曲奇停在画面正中心 | 无 | `ov_ts_008_taste_claim_safe_area`（neutralize_allowed） | person_reference：ent_person_a、ent_scene_atrium | 无（继承全局） | ready_with_assumptions |
| 8.2-9.5s | action_or_interaction | target_prop_raise_lens_switch | 镜面舞蹈教室｜空间类型由参考视频的器械健身房改为镜面舞蹈教室；地面由带数字格的地面改为浅枫木地板，墙色改为墨蓝 | 表演者乙：起点为自然站立，中段开始举起，终点为瑜伽垫停在画面正中心并被放大 | 无 | 无 | person_reference：ent_person_b、ent_scene_dance_studio | 无（继承全局） | ready_with_assumptions |
| 9.5-10.9s | visual_display | target_closing_product_reveal | 浅灰铺装屋顶露台｜空间类型由参考视频的户外广场改为屋顶露台；背景由弧形大楼立面改为天际线与陶土花盆 | 表演者乙：由中位举持推进到完全高举，终点为瓶身朝前并停稳 | `isl_ts_010_package`（ready） | `ov_ts_010_closing_text_safe_area`（neutralize_allowed） | person_reference：ent_person_b、ent_scene_rooftop、ent_subject_product | 无（继承全局） | ready_with_assumptions |
| 10.9-12.5s | visual_display | target_product_presentation_hold | 亚麻窗帘阅读角｜空间类型由参考视频的室内房间微调为阅读角；墙饰由黄色圆形装饰改为圆形藤编，侧柜由木质边柜改为浅桦木边柜 | 表演者甲：由自然站立进入胸前托瓶，姿态稳定并保持微笑 | `isl_ts_011_package`（ready） | 无 | person_reference：ent_person_a、ent_scene_reading_nook、ent_subject_product | 无（继承全局） | ready_with_assumptions |
| 12.5-13.4s | action_or_interaction | target_uncap_micro_action | 亚麻窗帘阅读角｜空间类型由参考视频的室内房间微调为阅读角；墙饰由黄色圆形装饰改为圆形藤编，侧柜由木质边柜改为浅桦木边柜 | 表演者甲：由持瓶状态进入旋拧，再进入把瓶盖移离瓶口的完成状态 | `isl_ts_012_package`（ready） | 无 | person_reference：ent_person_a、ent_scene_reading_nook、ent_subject_product | 无（继承全局） | ready_with_assumptions |
| 13.4-15.0s | closing_or_prompt | target_drink_and_closing_hold | 亚麻窗帘阅读角｜空间类型由参考视频的室内房间微调为阅读角；墙饰由黄色圆形装饰改为圆形藤编，侧柜由木质边柜改为浅桦木边柜 | 表演者甲：由开盖完成态进入仰头饮用，随后保持稳定直到片尾 | `isl_ts_013_package`（ready） | `ov_ts_013_closing_prompt_safe_area`（neutralize_allowed） | person_reference：ent_person_a、ent_scene_reading_nook、ent_subject_product | 无（继承全局） | ready_with_assumptions |

## 审计项与缺失项

- `miss_001`（actor_identity）：missing_generate_fallback → generate_with_confirmed_assumption
- `miss_002`（scene）：missing_generate_fallback → generate_with_confirmed_assumption
- `miss_003`（subtitle_text）：neutralize_allowed → omit_or_neutralize

源侧专属内容（仅审计，不进入目标描述）：

- 源侧画面文字：向全世界 / 安利好喝的金典鲜活 / INFO.0.09秒超瞬时杀菌 锁住鲜甜 / 口感满分 不冰也好喝 / 金典鲜活纯牛奶 / 好喝到每一刻都想拥有 + 红色爱心图形
- 源侧工艺与口感声明：0.09 秒超瞬时杀菌、锁住鲜甜、口感满分、不冰也好喝
- 源侧人物身份、服装（橄榄绿花纹开衫、灰色开衫、绿色外套、棕色开衫、运动装）与原品牌
- ASR 仅输出片尾字模署名文本，无可用台词

## H3 阶段状态

- H3 prompt/request 状态：由步骤 9 生成，见 `09_h3_package/`
- H3 视频生成状态：`not_submitted`（dry run 边界：只产出 request，不提交、不运行视频生成）
