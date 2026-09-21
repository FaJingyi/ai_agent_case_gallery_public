# 复刻大纲审阅稿 — quiet-in-the-city

本稿是 `06_replication_outline/replication_outline.json` 的人工审阅版本，按参考视频时间轴展示目标侧生成计划。时间字段截断到小数点后一位。

## 总览

- 目标视频：`quiet-in-the-city` / 13.5s / 1080:1624
- 复刻模式：`shot_structure`；状态：`ready_with_assumptions`；生成范围：`single_generation_task`
- 参考视频：9 个 shot、1 个 scene，时长 13.5s
- 主要主体：British man from <picture_1>
- 场景迁移：British street, British park pond
- 时间结构：`timeline_units`=9，`temporal_segments`=12
- 旁白：4 条英语旁白（改编自参考中文旁白），`speech_source=voiceover`，画内不做口型。
- 参考帧：`plan_required=True`，计划 4 张（1 人物 2 状态 + 2 场景）。
- 画内可读文字/logo：全部丢弃，不生成；字幕/标题层属于 post overlay，仅保留 clean plate。
- H3 prompt/request：本阶段尚未生成（步骤 9 待执行）。
- H3 视频生成：dry-run，未提交。

## 全局元素库（第二层）

### entity_person_1 — British man (person)
- 外观：young adult male；short swept-back light-brown hair；blue-green eyes；clean-shaven；same face across all close-ups
- 状态 `state_city`（city outfit, role=initial, change=static_appearance_change, ref=reuse_user_asset）：khaki jacket with a dark brown collar；plain white crew-neck t-shirt；dark trousers｜segments: VS001_SH001, VS001_SH002, VS001_SH004, VS001_SH005
- 状态 `state_park`（park outfit, role=final, change=static_appearance_change, ref=image_to_image_from_user_asset）：soft grey-green knit sweater；dark trousers；same face and hair｜segments: VS001_SH006, VS001_SH007, VS001_SH008, VS001_SH009
- 引用 segments：VS001_SH001, VS001_SH002, VS001_SH004, VS001_SH005, VS001_SH006, VS001_SH007, VS001_SH008, VS001_SH009

### entity_scene_city — British street (scene)
- 外观：Victorian and Georgian brick and stone facades；grey pavement；dark metal pedestrian railing；a few parked cars；overcast diffuse daylight；low saturation grey-green palette
- 状态 `state_city_scene`（single_state, role=single_state, change=unclear, ref=text_to_image）：British street exterior｜segments: VS001_SH001, VS001_SH002, VS001_SH004
- 引用 segments：VS001_SH001, VS001_SH002, VS001_SH004

### entity_scene_park — British park pond (scene)
- 外观：wide calm pond；mature broadleaf trees；clipped green lawn；dark tree trunk；soft overcast daylight；deep background space
- 状态 `state_park_scene`（single_state, role=single_state, change=unclear, ref=text_to_image）：British park pond exterior｜segments: VS001_SH005, VS001_SH006, VS001_SH007, VS001_SH008, VS001_SH009
- 引用 segments：VS001_SH005, VS001_SH006, VS001_SH007, VS001_SH008, VS001_SH009

### entity_prop_book — open paperback book (prop_context)
- 外观：plain white pages；no readable text；held and opened by the British man
- 引用 segments：VS001_SH005, VS001_SH006

### entity_style_atmosphere — quiet overcast realism (style_atmosphere)
- 外观：soft diffused overcast light；low saturation natural greens, whites and greys；low contrast；shallow depth of field；handheld lifestyle realism
- 引用 segments：VS001

## 时间轴

### VS001_SH001  0.0-1.7s
- 参考功能 / 目标功能：`context` / `context`
- 使用素材：<picture_1> (person identity and city-outfit appearance reference)
#### segment VS001_SH001_S1  0.0-1.7s
- 参考/目标功能：`context` / `establish British street and the male subject`
- 生成画面：full-body medium-wide shot of the British man standing with arms crossed on a British street, a blurred dark metal railing crossing the lower foreground, brick facades behind
- 视角：eye-level, slightly low from the pavement；构图：full-body medium-wide, subject centred behind a blurred foreground railing (foreground occlusion + midground subject + shallow background)；lower third occupied by the out-of-focus railing；运镜：static camera；焦点/景深：shallow depth of field with the subject sharp and the foreground railing heavily blurred
- 主体动作（close_motion_reference）：the British man stands almost still with arms folded
- 场景迁移：a British urban street: Victorian and Georgian brick and stone facades, grey pavement, a dark metal pedestrian railing in the foreground, a road with a few parked cars, overcast diffuse daylight
- 承接/转场：hard cut into the face close-up of the same man
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1', 'entity_scene_city'] states=['state_city']
- 状态：`ready_with_assumptions`

### VS001_SH002  1.7-2.4s
- 参考功能 / 目标功能：`focus` / `focus`
- 使用素材：<picture_1> (person identity and city-outfit appearance reference)
#### segment VS001_SH002_S1  1.7-2.4s
- 参考/目标功能：`focus` / `tighten from environment to the man's face`
- 生成画面：head-and-shoulders close-up of the British man against a plain grey wall, shallow background
- 视角：eye level；构图：head-and-shoulders close-up, face centred；plain grey wall background, generous negative space；运镜：static camera；焦点/景深：shallow depth of field
- 主体动作（close_motion_reference）：the British man makes a slight head and gaze movement
- 场景迁移：a British urban street: Victorian and Georgian brick and stone facades, grey pavement, a dark metal pedestrian railing in the foreground, a road with a few parked cars, overcast diffuse daylight
- 承接/转场：the picture dips to black
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1'] states=['state_city']
- 状态：`ready_with_assumptions`

### VS001_SH003  2.4-3.7s
- 参考功能 / 目标功能：`transition` / `transition`
- 使用素材：<picture_1> (person identity and city-outfit appearance reference)
#### segment VS001_SH003_S1  2.4-3.7s
- 参考/目标功能：`transition` / `black card chapter divider between city and nature blocks`
- 生成画面：the picture fades to a plain black card with no readable text, then fades back in
- 视角：n/a；构图：full-frame black card, lower safe area kept as a clean plate；运镜：static；焦点/景深：n/a
- 主体动作（beat_structure_only）：no subject action
- 场景迁移：a British urban street: Victorian and Georgian brick and stone facades, grey pavement, a dark metal pedestrian railing in the foreground, a road with a few parked cars, overcast diffuse daylight
- 承接/转场：fade in from black into live street action
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=none status=not_required entities=[] states=[]
- 状态：`ready_with_assumptions`

### VS001_SH004  3.7-4.9s
- 参考功能 / 目标功能：`development` / `development`
- 使用素材：<picture_1> (person identity and city-outfit appearance reference)
#### segment VS001_SH004_S1  3.7-4.4s
- 参考/目标功能：`development` / `city walking beat with handheld follow`
- 生成画面：medium-full walking shot of the British man on the British street, strong motion blur, slightly off-centre
- 视角：eye level；构图：medium-full walking framing, subject slightly off-centre；blurred British facades behind；运镜：handheld follow with strong motion blur；焦点/景深：shallow depth of field with motion blur on the background
- 主体动作（close_motion_reference）：the British man walks toward the camera
- 场景迁移：a British urban street: Victorian and Georgian brick and stone facades, grey pavement, a dark metal pedestrian railing in the foreground, a road with a few parked cars, overcast diffuse daylight
- 承接/转场：hard cut into the book close-up
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1', 'entity_scene_city'] states=['state_city']
- 状态：`ready_with_assumptions`
#### segment VS001_SH004_S2  4.4-4.9s
- 参考/目标功能：`development` / `small natural gesture while walking`
- 生成画面：the walking British man raises one hand to brush his hair and gives a brief smile
- 视角：eye level；构图：medium-full, subject slightly off-centre；background still smeared with motion blur；运镜：handheld follow continues；焦点/景深：shallow depth of field
- 主体动作（close_motion_reference）：the British man raises his right hand to his hair and smiles
- 场景迁移：a British urban street: Victorian and Georgian brick and stone facades, grey pavement, a dark metal pedestrian railing in the foreground, a road with a few parked cars, overcast diffuse daylight
- 承接/转场：hard cut into the book close-up
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1'] states=['state_city']
- 状态：`ready_with_assumptions`

### VS001_SH005  4.9-5.4s
- 参考功能 / 目标功能：`focus` / `focus`
- 使用素材：<picture_1> (person identity and city-outfit appearance reference)
#### segment VS001_SH005_S1  4.9-5.4s
- 参考/目标功能：`focus` / `introduce the book and the slower rhythm`
- 生成画面：extreme close-up of a hand holding an open paperback above blurred green grass
- 视角：high oblique；构图：extreme close-up of hand and open book, centred；blurred green grass background；运镜：static camera；焦点/景深：extremely shallow depth of field on the hand and book
- 主体动作（close_motion_reference）：the British man's hand holds the open paperback and turns a page
- 场景迁移：a British park with a wide calm pond, mature broadleaf trees, clipped green lawn, a dark tree trunk, soft overcast daylight and deep background space
- 承接/转场：hard cut with prop continuity on the same book
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1', 'entity_scene_park'] states=['state_park']
- 状态：`ready_with_assumptions`

### VS001_SH006  5.4-8.5s
- 参考功能 / 目标功能：`action` / `action`
- 使用素材：<picture_1> (person identity and city-outfit appearance reference)
#### segment VS001_SH006_S1  5.4-6.6s
- 参考/目标功能：`action` / `wider park reveal with the seated man`
- 生成画面：wide-medium shot of the quiet British park with the pond and a mature tree, the British man seated at the base of the tree holding the book
- 视角：eye level wide；构图：wide-medium, subject at the base of the tree, centre-weighted；deep space with pond water and foliage behind；运镜：static camera；焦点/景深：deep space on the wide shot with a shallow foreground plane
- 主体动作（close_motion_reference）：the British man sits at the tree base and holds the open book
- 场景迁移：a British park with a wide calm pond, mature broadleaf trees, clipped green lawn, a dark tree trunk, soft overcast daylight and deep background space
- 承接/转场：hard cut into an extreme close-up of the same face
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1', 'entity_scene_park'] states=['state_park']
- 状态：`ready_with_assumptions`
#### segment VS001_SH006_S2  6.6-8.5s
- 参考/目标功能：`action` / `hold the quiet park beat`
- 生成画面：the seated British man holds the book with only a minor body adjustment in the quiet park
- 视角：eye level wide；构图：wide-medium park framing held steady；pond and foliage remain readable behind；运镜：static camera；焦点/景深：deep space on the wide shot
- 主体动作（beat_structure_only）：a minor body adjustment while holding the book
- 场景迁移：a British park with a wide calm pond, mature broadleaf trees, clipped green lawn, a dark tree trunk, soft overcast daylight and deep background space
- 承接/转场：hard cut into an extreme close-up of the same face
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1', 'entity_scene_park'] states=['state_park']
- 状态：`ready_with_assumptions`

### VS001_SH007  8.5-11.2s
- 参考功能 / 目标功能：`emotional_shift` / `emotional_shift`
- 使用素材：<picture_1> (person identity and city-outfit appearance reference)
#### segment VS001_SH007_S1  8.5-9.6s
- 参考/目标功能：`emotional_shift` / `face fills the frame as the mood turns inward`
- 生成画面：extreme close-up of the British man's face filling the frame against soft park bokeh
- 视角：eye level tight；构图：extreme close-up, face filling the frame；soft park bokeh background；运镜：static camera；焦点/景深：extremely shallow depth of field on the eyes
- 主体动作（close_motion_reference）：the British man turns his head into a profile with his gaze lifted
- 场景迁移：a British park with a wide calm pond, mature broadleaf trees, clipped green lawn, a dark tree trunk, soft overcast daylight and deep background space
- 承接/转场：hard cut landing on the water surface
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1'] states=['state_park']
- 状态：`ready_with_assumptions`
#### segment VS001_SH007_S2  9.6-11.2s
- 参考/目标功能：`emotional_shift` / `closing voiceover line over the face`
- 生成画面：the extreme close-up of the face holds while the closing line begins
- 视角：eye level tight；构图：extreme close-up held on the face；soft park bokeh；运镜：static camera；焦点/景深：extremely shallow depth of field
- 主体动作（beat_structure_only）：the British man holds the gaze nearly still
- 场景迁移：a British park with a wide calm pond, mature broadleaf trees, clipped green lawn, a dark tree trunk, soft overcast daylight and deep background space
- 承接/转场：hard cut landing on the water surface
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1'] states=['state_park']
- 状态：`ready_with_assumptions`

### VS001_SH008  11.2-12.5s
- 参考功能 / 目标功能：`emotional_shift` / `emotional_shift`
- 使用素材：<picture_1> (person identity and city-outfit appearance reference)
#### segment VS001_SH008_S1  11.2-12.5s
- 参考/目标功能：`emotional_shift` / `ripples on the pond carry the closing line`
- 生成画面：extreme close-up of the pond water surface as a hand reaches in and fingertips touch the water, sending out slow ripples
- 视角：oblique down；构图：extreme close-up of the water surface；hand entering frame from the side；运镜：static camera；焦点/景深：extremely shallow depth of field on the contact point
- 主体动作（close_motion_reference）：the British man's fingertips touch the pond water and slow ripples spread
- 场景迁移：a British park with a wide calm pond, mature broadleaf trees, clipped green lawn, a dark tree trunk, soft overcast daylight and deep background space
- 承接/转场：hard cut from the water detail to a soft chest-and-shoulder detail
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1', 'entity_scene_park'] states=['state_park']
- 状态：`ready_with_assumptions`

### VS001_SH009  12.5-13.5s
- 参考功能 / 目标功能：`closing` / `closing`
- 使用素材：<picture_1> (person identity and city-outfit appearance reference)
#### segment VS001_SH009_S1  12.5-13.5s
- 参考/目标功能：`closing` / `body-detail close resolves the film`
- 生成画面：body-detail close-up of the British man's chest and shoulder with one hand resting gently on the chest
- 视角：eye level close；构图：body-detail close-up, chest and shoulder filling the frame；soft blurred park background；运镜：static camera；焦点/景深：shallow depth of field
- 主体动作（close_motion_reference）：the British man's hand rests gently on his chest
- 场景迁移：a British park with a wide calm pond, mature broadleaf trees, clipped green lawn, a dark tree trunk, soft overcast daylight and deep background space
- 承接/转场：end of film
- 旁白：无
- 画内实体文字/logo：无
- 后期叠加：无（保留 clean plate）
- 参考帧决策：role=person_reference status=needed entities=['entity_person_1'] states=['state_park']
- 状态：`ready_with_assumptions`

## 记忆点迁移摘要

- `vm_001` → 保留：foreground occlusion frame；layered depth；vertical full-body framing｜改写：dark metal railing on a British pavement；British man as subject｜绑定：['VS001_SH001']
- `vm_002` → 保留：dip-to-black chapter divider；city-then-nature block order｜改写：plain black card without readable text；English voiceover continues across the card｜绑定：['VS001_SH003']
- `vm_003` → 保留：handheld follow；motion blur；off-centre walking subject｜改写：British man walking on a British street｜绑定：['VS001_SH004']
- `vm_004` → 保留：body-detail extreme close-up rhythm；shallow depth of field；simplified background｜改写：British man's hand / face / water / chest details｜绑定：['VS001_SH005', 'VS001_SH007', 'VS001_SH009']
- `vm_005` → 保留：reach-contact-ripple order；slow rhythm｜改写：British park pond water｜绑定：['VS001_SH008']
- `vm_006` → 保留：lower safe-area single-line layout；cross-cut continuity｜改写：reserve lower safe area as clean plate; no subtitle text rendered｜绑定：['VS001_SH007', 'VS001_SH008']
- `vm_007` → 保留：static appearance change synchronised with the scene change；stable identity anchors｜改写：khaki jacket -> grey-green knit for the park block｜绑定：['VS001_SH006', 'VS001_SH009']
- `sm_001` → 保留：black-card chapter divider carrying the theme line position｜改写：theme carried by the English voiceover tt_001 instead of on-screen text｜绑定：['VS001_SH003']
- `sm_002` → 保留：contrast between the city and nature blocks；outfit change synchronised with the block change｜改写：British street vs British park；male outfit difference｜绑定：['VS001_SH004', 'VS001_SH006']
- `sm_003` → 保留：detail close-up bound to one voiceover line；outside-to-inside information order｜改写：book -> face -> water -> chest with English lines｜绑定：['VS001_SH005', 'VS001_SH007', 'VS001_SH008', 'VS001_SH009']
- `sm_004` → 保留：closing line carried across a hard cut；body-detail ending without an explicit CTA｜改写：English closing line tt_004｜绑定：['VS001_SH008', 'VS001_SH009']

## 审计与缺口

- 缺口 `mi_001` slot=voiceover status=missing_generate_fallback policy=use_text_instruction
- 缺口 `mi_002` slot=actor_park_outfit_state status=missing_generate_fallback policy=generate_with_confirmed_assumption
- 假设 `ga_002` slot=actor_park_outfit_state：grey-green knit park outfit keeping the same identity anchors
- 假设 `ga_003` slot=scene：British street and British park pond generated from user text
- 假设 `ga_004` slot=prop：ordinary open paperback with no readable text

## 结果状态

- `replication_outline.json.status = ready_with_assumptions`（无阻塞项；英语旁白与公园造型为已确认假设生成）
- H3 prompt/request：待步骤 9 生成。
- H3 视频生成：dry-run 边界内不提交。
