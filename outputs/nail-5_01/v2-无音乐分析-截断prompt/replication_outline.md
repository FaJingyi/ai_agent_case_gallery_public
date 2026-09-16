# 复刻大纲审阅稿（nail-5）

- `schema_version`: `common_replication_outline.v2`
- `status`: `ready_with_assumptions`
- `replication_mode`: `shot_structure`
- `generation_scope`: `single_generation_task`
- 目标时长/画幅: `15.0s` / `9:16`（`resolution_target=720x1280`）
- 时间精度: 截断到小数点后一位（`precision=one_decimal`, `method=truncate`）
- 参考视频事实来源: `01_reference_video_analysis/reference_video_analysis.json`
- 用户目标素材: `test_data/nail-5/user_input/shangpin-3.png`（A001）
- 用户需求: 将参考视频里的美甲的图案替换成素材图片里的美甲图案，人物的装扮和场景和美甲风格一致。

## 1. 复刻目标

保留参考视频的 5 个 shot 结构、镜头顺序、景别推进（中景 → 手部大特写 → 极近特写）、前景遮挡转场、画中画版式、俯拍机位与硬切节奏；把源侧的明亮户外世界、原人物造型、原甲面图案与原画面文案全部替换为目标侧内容。

目标侧世界为素材美甲 A001 的**暗黑哥特金属**风格：目标人物改为暗色皮革/缎面/金属造型，场景改为暗色室内化妆间、夜间暗色露台庭院、暗色石造工业回廊，注意力中心始终是佩戴在人物手指上的目标甲面。

## 2. 时间结构总览

| unit | 参考 shot | 时间(s) | 主体类型 | 参考功能 | 目标功能 | segment |
| --- | --- | --- | --- | --- | --- | --- |
| U001 | shot1 | 0.0-3.5 | human | opening_hook | 建立目标空间与人物，并以手部前景遮挡转场 | S001, S002 |
| U002 | shot2 | 3.5-8.5 | human | visual_display | 在目标暗色露台完整展示目标甲面并保留文字节拍 | S003, S004, S005 |
| U003 | shot3 | 8.5-10.0 | mixed | information_reveal | 手部大特写 + 画中画 + 底部文字安全区强化细节 | S006, S007 |
| U004 | shot4 | 10.0-14.5 | human | visual_display | 第三造型展示 + 佩戴头饰 + 俯拍展示 | S008, S009, S010 |
| U005 | shot5 | 14.5-15.0 | environment | closing | 暗色地面极近特写收尾 | S011 |

`timeline_units[]` 保持 shot 级（5 个），`temporal_segments[]` 共 11 个。H3 prompt 中的 `[Shot N]` 由 `temporal_segments` 渲染，标记为 `prompt_shots_from_temporal_segments`，不新增、拆分或重排参考镜头。

## 3. 全局外观库

| entity_id | 类型 | 名称 | 关键外观 |
| --- | --- | --- | --- |
| MS001 | main_subject_appearance | 目标美甲款式 | 10 片尖形长尖杏仁甲；黑亮面 / 深灰褐哑光 / 灰褐拼黑；立体写实眼睛（棕与黄绿虹膜、黑瞳、白眼白）、白珍珠与金边珍珠、银色金属浮雕与滴落线条、白色细线、金色小圆点与水钻；暗黑哥特华丽金属风 |
| PE001 | person_appearance | 目标人物 | 成年亚洲女性，深色长发自然垂落，深色烟熏眼妆与深色唇；三套造型状态；暗色金属与银色戒指、暗色金属细手链；暗黑冷峻金属气质 |
| SCN001_T | scene_appearance | 场景1 暗色室内化妆间 | 深色台面与暗色金属托盘、天鹅绒软包座椅、深灰石纹墙面与金属边框化妆镜；低照度侧光与镜面高光；冷调深灰黑 |
| SCN002_T | scene_appearance | 场景2 夜间暗色露台庭院 | 暗色阔叶植物、黑色铁艺栏杆、深色石板地面、暗色金属雕塑、深色夜空与远处建筑轮廓；冷色月光与冷白补光；深灰蓝黑 |
| SCN003_T | scene_appearance | 场景3 暗色石造工业回廊 | 深色石板地面、暗色金属栏杆、石材立柱、黑色金属格构梁架；冷白顶光与结构高光；黑灰冷调 |
| KP001 | key_prop_appearance | 暗色金属小道具 | 指间捏持的小型花形/球状物，暗色金属与黑曜石质感，黑色深灰带银色高光 |
| KP002 | key_prop_appearance | 暗色金属头饰 | 细金属环与暗色宝石拼接头饰，深灰黑金属哑光与高光交错 |
| KP003 | key_prop_appearance | 手部配饰 | 暗色金属与银色戒指、暗色金属细手链 |
| SA001 | style_atmosphere | 暗黑哥特金属质感 | 低照度侧光与冷白补光、金属高光与镜面反射；黑/深灰/深灰蓝/银点缀；写实竖屏浅景深 |

PE001 绑定最早出现的初始状态 `PE001_ST1`（深黑缎面与皮革拼接上衣 + 深灰长裤，生效于 S001-S002）；`PE001_ST2`（黑色金属光泽上衣 + 银色金属装饰片，生效于 S003-S007）；`PE001_ST3`（深灰黑长外套 + 黑色高领 + 暗色金属头饰，生效于 S008-S011）。参考图只锚定 ST1 初始状态，后续造型状态由分镜描述控制。

## 4. 逐段分镜

### 分镜 S001（0.0-2.0s，U001）

- 画面: PE001 目标人物立于 SCN001_T 暗色室内化妆间，竖屏中景、正面平视、主体居中、浅景深。
- 动作: 人物双手先扶腰侧，随后抬起一只手转向镜头展示手部与目标甲面。
- 光线/质感: 低照度侧光与镜面反射高光，冷调深灰。
- 素材/参考帧: FR_PE001（人物1）、FR_SCN001_T（场景1）、MS001 目标甲面。
- 文字: 顶部画面文字为后期叠加，目标侧文本未提供，仅保留顶部安全区（`missing_required_input`）。
- 承接: 片段开场，段内连续。

### 分镜 S002（2.0-3.5s，U001）

- 画面: 中景转手部近景，正面机位，主体迅速放大。
- 动作: 人物双手抬至胸前、十指张开向镜头前伸并贴近镜头，手部占满画面形成遮挡。
- 特殊机制: `SMT001 foreground_wipe`（medium）→ “人物双手十指张开向镜头前伸并贴近镜头形成前景遮挡，遮挡结束时画面已切换到目标暗色空间。”
- 承接: 以手部前景遮挡转场衔接 U002。

### 分镜 S003（3.5-5.0s，U002）

- 画面: PE001 在 SCN002_T 夜间暗色露台，竖屏中景、正面平视、主体居中、浅景深。
- 动作: 双手上举至胸前、十指张开正对镜头缓慢展示，随后轻微翻转手掌。
- 光线/质感: 冷色月光与冷白补光，金属质感高光。
- 承接: 承接前景遮挡转场。

### 分镜 S004（5.0-7.0s，U002）

- 画面: 竖屏中近景、正面平视、主体居右、画面顶部留出文字安全区。
- 动作: 双手由胸前移向脸侧，掌面朝镜头保持甲面可见，头部轻微侧转。
- 文字: 顶部画面文字为后期叠加，目标侧文本未提供，仅保留安全区与节拍（`missing_required_input`）。
- 记忆点: 保留画面文字出现时机与信息强调节奏，不迁移源文案。

### 分镜 S005（7.0-8.5s，U002）

- 画面: 手部近景，浅景深虚化暗色背景。
- 动作: 人物侧身，手部上抬至面部一侧，拇指与食指捏住 KP001 暗色金属小道具并轻微转动。
- 承接: 硬切到 U003。

### 分镜 S006（8.5-9.2s，U003）

- 画面: 手部大特写、浅景深，左上角画中画约占画面四分之一，底部保留文字安全区。
- 动作: 手部特写定格，暗色金属小道具位于指间。
- 特殊机制: `SMT002 picture_in_picture`（high）→ “在手指捏持暗色金属小道具的手部大特写画面左上角，叠加一张同为手部与小道具、暗色空间背景的小图，小图约占画面四分之一并保持与主图一致的冷色调。”
- 文字: 底部画面文字为后期叠加，目标侧文本未提供（`missing_required_input`）。
- 承接: 硬切自 U002，段内定格。

### 分镜 S007（9.2-10.0s，U003）

- 画面: 手部大特写、浅景深、主体居中偏下。
- 动作: 手指轻轻转动暗色金属小道具，甲面反光随角度变化。
- 承接: 硬切到 U004。

### 分镜 S008（10.0-11.5s，U004）

- 画面: PE001 在 SCN003_T 暗色石造工业回廊，竖屏中景、正面平视、主体居中、冷调浅景深；造型为 PE001_ST3。
- 动作: 双手举起至胸前展示甲面并缓慢翻转手掌。
- 承接: 硬切自 U003。

### 分镜 S009（11.5-13.0s，U004）

- 画面: 竖屏中近景、正面平视、主体居中。
- 动作: 人物双手抬起将 KP002 暗色金属头饰戴到头上并扶正，随后手部靠近面部保持甲面可见。
- 记忆点: 保留造型变化节拍。

### 分镜 S010（13.0-14.5s，U004）

- 画面: 俯拍机位，主体居中，手部靠近画面上方。
- 动作: 人物坐于暗色石板地面上，双手向镜头上方举起展示甲面，随后手部缓缓放下接近地面。
- 特殊机制: `SMT003 overhead_or_bird_eye_shot`（medium）→ “机位转为俯拍，人物坐于暗色石板地面，双手向镜头上方举起展示目标甲面，随后手部缓缓放下。”
- 承接: 硬切到 U005。

### 分镜 S011（14.5-15.0s，U005）

- 画面: 极近特写、浅景深，手部位于画面中下部。
- 动作: 手部落在暗色石板地面上并轻微移动，甲面仅部分可见。
- 收尾: 片段收尾，回落情绪。

## 5. 场景迁移

| scene_id | 参考场景 | 目标时间(s) | preserve_scene_style | adapt_scene_content | visible_difference_anchor |
| --- | --- | --- | --- | --- | --- |
| SCN001_T | SCN001 | 0.0-3.5 | 竖屏中景构图、主体居中、浅景深、写实质感 | 室内化妆间、冷调深灰黑、金属镜框与石纹墙面、暗色软包与托盘 | 由明亮户外草地改为室内化妆间；高饱和蓝天绿草改为深灰黑 |
| SCN002_T | SCN002 | 3.5-10.0 | 构图关系与空间深度、浅景深虚化、写实质感 | 夜间露台庭院、深灰蓝黑、铁艺栏杆与暗色植物、移除湖泊雪山 | 由日间湖畔草地改为夜间露台庭院 |
| SCN003_T | SCN003 | 10.0-15.0 | 构图关系与空间深度、主体居中、浅景深、俯拍机位 | 室内石造工业回廊、黑灰冷调、石材立柱与金属格构梁架 | 由日间铁塔草坡改为室内石造工业回廊 |

目标素材 A001 的背景按 `asset_incidental_background_not_used` 处理，只作为审计线索，不作为目标场景。

## 6. 文字与 logo 策略

- `post_overlay_default=true`，`render_post_overlay_in_video_model=false`，`post_overlay_render_method=ffmpeg_or_opencv`。
- 参考视频存在顶部/中部/底部画面文案节拍，目标侧文本未提供（`target_text_status=missing_required_input`），因此目标视频不生成任何可读文字，只在 S001 / S004 / S006 保留安全区与节拍，H3 生成 clean plate。
- `do_not_generate_unconfirmed_readable_text=true`；无画内实体 logo / 包装文字需求。

## 7. 记忆点迁移

| memory_id | 类型 | 保留机制 | 目标绑定 | 状态 |
| --- | --- | --- | --- | --- |
| vm_001 | visual | 手部前景遮挡转场与遮挡前后强对比 | S002, S003 | ready |
| vm_002 | visual | 画中画位置、面积占比与主次关系 | S006 | ready |
| vm_003 | visual | 俯拍机位与双手上举展示关系 | S010 | ready |
| vm_004 | visual | 手部动作阶段与向镜头前伸的接近感 | S002 | ready |
| vm_005 | visual | 硬切节奏与手部展示统一线索 | S003-S011 | ready |
| sm_001/sm_003/sm_004 | script | 开场钩子、信息强调时机、环境特写收尾的信息结构 | 全片 / S004 / S011 | 目标文案缺失，仅保留结构 |
| am_* | audio | 仅 `unsupported_skipped` 审计，不迁移 | - | skipped |

## 8. 参考帧摘要

- `frame_requirement_level=required_person_scene_anchors`，`plan_required=true`，`plan_path=07_reference_frame_plan/reference_frame_plan.json`
- 人物实体 1 个（PE001 绑定初始状态 PE001_ST1）→ 1 张纯人物参考图 `FR_PE001`
- 场景实体 3 个（SCN001_T / SCN002_T / SCN003_T 差异明显，保留独立）→ 3 张纯场景参考图 `FR_SCN001_T` / `FR_SCN002_T` / `FR_SCN003_T`
- 加上用户素材 A001，进入 H3 的图片总数为 5，未超过 5 张上限
- `ready_frame_ids` 在步骤 8 生成成功后回填

## 9. 审计与降级

- 缺失输入: MI001 `nail_worn_state`（把平铺穿戴甲转写为佩戴状态，`generate_with_confirmed_assumption`）；MI002 `actor_identity`（非特定身份，生成假设）；MI003 `on_screen_text`（`omit_or_neutralize`）。
- 生成假设: GA001 甲面佩戴状态；GA002 人物装扮按素材风格重设（用户确认）；GA003 场景按素材风格重设（用户确认）；GA004 人物外观细节；GA005 场景陈设细节。
- 源侧审计约束（`prompt_visibility=audit_only`）: `src_bright_outdoor_world`（medium）、`src_on_screen_caption_text`（high）、`src_claim_objects`（low）、`caption_layers_are_post_overlay`（low）等；不进入提交 prompt。
- 上游降级: VLM 响应在 `max_tokens=8000` 被截断；视频按约 24 帧稀疏采样，shot 边界为近似值；`backend/profiles` 的脚本/叙事结构与音乐目录为空（`skipped_empty_directory`）。
- 音频: ASR 返回疑似英文歌词，归类为音乐/疑似唱歌，`unsupported_skipped`，不迁移。
- 校验标记: `shot_boundaries_are_approximate_due_to_sparse_video_sampling`、`nail_worn_state_is_generation_assumption`、`source_on_screen_text_omitted_target_text_missing`、`scripts_knowledge_directory_empty_no_script_profile_used`、`reference_frame_count_including_user_asset_equals_h3_limit_5`。

## 10. 状态

- 准备度检查: `ready_with_assumptions`，16 条要求，0 个阻塞项。
- 大纲状态: `ready_with_assumptions`；参考帧计划与 H3 打包可继续。
- 下一步: 步骤 7 参考帧计划 → 步骤 8 参考帧生成 → 步骤 9 H3 打包输入整理（本 dry run 在 H3 请求产出后停止，不提交视频生成）。
