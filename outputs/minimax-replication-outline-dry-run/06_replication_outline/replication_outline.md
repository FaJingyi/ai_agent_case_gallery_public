# 复刻大纲审阅稿 (replication_outline)

- status: `ready_with_assumptions`  |  generation_scope: `single_generation_task`  |  duration: 15.0s
- timeline_unit_count: 4  |  temporal_segment_count: 8
- 参考视频: `test_data/minimax/minimax.mp4` (前 15.0s)
- 用户需求: 参考视频生成一条新的视频，把视频里所有"minimax"字母换成"MetaX"，把视频中的模特换成猫咪

## 显式替换覆盖 (explicit replacement coverage)
- `REP001` on-screen 'minimax' lettering / MINIMAX wordmark -> **MetaX** | segments 8/8 visible | status `covered`
- `REP002` the model / the woman appearing in the reference video -> **cat** | segments 4/4 visible | status `covered`
- binding status: `passed`

## 参考元素处理 (reference_element_treatment_plan)
- `E001` [inherit] composition: the whole clip sits inside two side-by-side circular apertures on a black field with a soft vignette
- `E002` [adapt] text_or_ui: red monospace scouting UI text at the left and right frame edges, changing per shot
- `E003` [inherit] transition: three hard cuts between four equal ~4s holds with the mask, warm grade and UI staying continuous
- `E004` [inherit] camera: completely locked camera in every shot; all motion comes from the subject or environment
- `E005` [inherit] visual_style: warm amber vintage-film grade, light grain, medium contrast, observation mood
- `E006` [adapt] scene_content: a branded bus-stop shelter standing on a city street in front of a beige stone building
- `E007` [inherit] action_structure: the only motion in shot 1 is a faint drift of the lettering's ground shadow
- `E008` [adapt] scene_content: a low-angle view of a tall building carrying a large vertical white fabric banner
- `E009` [inherit] action_structure: the banner ripples gently in the wind while the camera stays locked
- `E010` [inherit] composition: low-angle building view as the second scouting step
- `E011` [adapt] person_or_body: a woman in a beige suit holding a black phone stands at the left of a rooftop
- `E012` [adapt] prop: large three-dimensional brand letters on the rooftop structure behind the subject
- `E013` [inherit] composition: medium shot with the subject left and the structure behind
- `E014` [adapt] scene_content: the rooftop viewpoint with a parapet and a lettering structure
- `E015` [adapt] person_or_body: an extreme close-up of a face wearing red-framed geometric sunglasses that reflect the brand lettering
- `E016` [discard] person_or_body: a silver round earring is visible in the closing close-up
- `E017` [discard] person_or_body: a red high-neck top is visible in the closing close-up
- `E018` [adapt] text_or_ui: the source brand wordmark is planted on the bus shelter in shot 1 and paid off as a lens reflection in shot 4
- `E019` [discard] watermark_or_platform_ui: source-specific scouting labels and the source brand word appear as edge UI and in-scene lettering
- `E020` [inherit] scene_content: beige stone facade and a cloudy sky recur behind the subjects
- `E021` [discard] unsupported_audio: the clip carries a music bed but audio is out of scope for this workflow
- `E022` [discard] dialogue_or_voiceover: a single low-confidence English phrase was detected but not confirmed as speech

## 记忆点迁移 (memory_transfer_plan)
- `vm_001` (visual) preserve: twin circular aperture mask; black surround; soft vignette at the circular edges -> keep the mask geometry locked; replace all subject and scene content with the MetaX/cat target world
- `vm_002` (visual) preserve: red monospace type; left/right symmetric edge layout; per-shot label change -> render the edge UI in post as neutral non-declarative red monospace; never render source wording or the source brand in the UI layer
- `vm_003` (visual) preserve: three hard cuts between four equal holds; continuous mask, grade and UI across cuts -> keep the hard-cut rhythm and the continuous mask/grade; change only the subject and location content
- `vm_004` (visual) preserve: slight head turn; reflection changing with the turn; locked camera -> the cat turns its head slightly so the mirrored MetaX lettering slides inside the sunglass lenses
- `sm_001` (script) preserve: open directly inside the framed observing POV; withhold the wider context -> open on the MetaX shelter inside the apertures with the same withheld context
- `sm_002` (script) preserve: four-step descending reveal order; per-step label change -> keep the four-step order: street, banner, rooftop animal, reflected wordmark; adapt each step's subject and wording
- `sm_003` (script) preserve: plant the wordmark early; pay it off visibly in a reflective surface at the close -> plant MetaX on the shelter panel in shot 1 and pay it off as a reflection in the sunglasses in shot 4
- `sm_004` (script) preserve: progressively narrowing scale from environment to an intimate detail -> narrow from the street and building scale to the rooftop animal and finally to the cat's reflective lenses
- audio: `unsupported_skipped`

## 特殊机制迁移 (special_mechanism_transfer)
- `M001` [special_composition] handoff=both: Frame the entire 15-second video inside two side-by-side circular apertures on a black field with a soft dark vignette at the circular edges, and keep that mask geometry, position and scale locked across all four shots.
- `M002` [special_transition] handoff=downstream_prompt: Cut hard at 4.0s, 8.0s and 12.0s between four equal holds, and keep the twin aperture mask, the warm vintage grade and the red monospace edge-UI layout continuous across every cut.

## 全局外观库 (global_appearance_dedup_pass)
- `MAIN_SUBJECT_1` (main_subject_appearance, merge=single_entity): the cat (replacement for the model)
  - details: domestic short-hair cat with a warm ginger-and-cream coat; amber eyes with a calm, alert gaze; upright pointed ears with soft inner fur, fine whiskers and a small pink nose; compact, well-groomed body covered in soft dense fur
- `SCENE_1` (scene_appearance, merge=single_entity): ground-level urban street with the MetaX bus-stop shelter
  - details: ground-level city street in front of a beige stone building; modern MetaX-branded bus-stop shelter as the observed object; sidewalk, long ground shadow cast by the shelter lettering; warm daylight, beige stone materials, medium background density
- `SCENE_2` (scene_appearance, merge=single_entity): building exterior with the vertical MetaX fabric banner
  - details: tall building facade seen from a low upward angle; large vertical white fabric banner hanging down the facade; cloudy sky above a beige stone surface; cooler overcast daylight in the upper frame, warm grade overall
- `SCENE_3` (scene_appearance, merge=single_entity): open rooftop with the 3D MetaX lettering structure
  - details: open rooftop terrace with a parapet; oversized three-dimensional lettering structure on the rooftop; cloudy sky beyond the parapet, warm daylight; space re-scaled so the small animal subject reads against the large letters
- `PROP_1` (key_prop_appearance, merge=single_entity): MetaX in-scene lettering
  - details: three-dimensional block lettering spelling MetaX; clean geometric sans-serif capitals with slight extruded depth; warm off-white surface finish matching the host structure; appears as shelter panel lettering, vertical banner lettering, 3D rooftop lettering and a sunglass-lens reflection
- `PROP_2` (key_prop_appearance, merge=single_entity): red geometric sunglasses worn by the cat
  - details: oversized sunglasses with thick red geometric frames; two rounded-rectangle mirrored lenses; the MetaX lettering is visible as a reflection inside the lenses; worn on the cat's face in the closing close-up
- `STYLE_ATMOSPHERE_1` (style_atmosphere, merge=single_entity): warm vintage observing-device atmosphere
  - details: warm amber vintage-film grade with light grain and soft vignette; medium contrast, warm highlights, relaxed shadows; stylized retro documentary realism; locked observational mood with red monospace edge UI

## 场景迁移 (scene_transfer)
- `SCENE_1`: ground-level city street with a modern MetaX-branded bus-stop shelter in front of a beige stone building, warm daylight, long ground shadow, sidewalk and low set dressing
- `SCENE_2`: tall beige stone building facade seen from a low angle with a large vertical MetaX fabric banner hanging down it under a cloudy sky
- `SCENE_3`: open rooftop terrace with a parapet and oversized three-dimensional MetaX lettering, cloudy sky beyond, warm daylight, space proportioned for a small animal subject

## 时间轴 (timeline_units / temporal_segments)

### TU001  0.0-4.0s  (4.0s)  status=ready_with_assumptions
- 参考功能/目标内容: held street observation of a MetaX-branded bus-stop shelter inside the dual aperture frame
- 主体: MetaX-branded bus-stop shelter on a warm city street
- 镜头语言: twin side-by-side circular apertures on black; centre-weighted medium-wide framing | static locked-off camera
  - **TU001_S1** 0.0-2.5s | ref=visual_display -> tgt=opening_hook | status=ready_with_assumptions
    - 生成画面: holds the restricted observing frame on a MetaX-branded bus-stop shelter on a city street, establishing the scouting POV before any context
    - 动作/运镜: no subject movement; the frame is held while the lettering shadow drifts very slightly | static locked-off camera, no push, pan or zoom
    - 场景迁移: {'scene_entity_id': 'SCENE_1', 'preserve_scene_style': True, 'adapt_scene_content': 're-letter to MetaX, keep composition and lighting'}
    - 画面内实体文字/logo: ready:in-scene physical lettering reading MetaX on the bus-stop shelter panel
    - 后期叠加: label:neutralize_allowed
    - 参考帧: scene_reference ['SCENE_1']
    - 缺失输入: none | 生成假设: ['GA002']
    - guardrail: The shelter panel lettering reads MetaX; no other readable brand text appears.
  - **TU001_S2** 2.5-4.0s | ref=text_overlay_or_information_reveal -> tgt=information_release | status=ready_with_assumptions
    - 生成画面: continues the held observation and releases the first scouting information beat on the edge UI while the MetaX lettering shadow drifts
    - 动作/运镜: lettering shadow drifts slightly; no camera or subject motion | static locked-off camera
    - 场景迁移: {'scene_entity_id': 'SCENE_1', 'preserve_scene_style': True, 'adapt_scene_content': 'unchanged'}
    - 画面内实体文字/logo: ready:in-scene physical lettering reading MetaX
    - 后期叠加: label:neutralize_allowed
    - 参考帧: scene_reference ['SCENE_1']
    - 缺失输入: ['MI004'] | 生成假设: none

### TU002  4.0-8.0s  (4.0s)  status=ready_with_assumptions
- 参考功能/目标内容: low-angle reveal of a vertical MetaX fabric banner on a tall building facade
- 主体: vertical MetaX fabric banner hanging on a tall building
- 镜头语言: low-angle wide framing inside the dual aperture mask; vertical subject centred | static locked-off camera
  - **TU002_S1** 4.0-6.5s | ref=visual_display -> tgt=reveal | status=ready_with_assumptions
    - 生成画面: hard cut to a low-angle view of a tall building carrying a large vertical MetaX fabric banner against a cloudy sky
    - 动作/运镜: the banner hangs; wind begins to move the fabric | static locked-off camera, no tilt or zoom
    - 场景迁移: {'scene_entity_id': 'SCENE_2', 'preserve_scene_style': True, 'adapt_scene_content': 're-letter the banner to MetaX'}
    - 画面内实体文字/logo: ready:in-scene physical lettering reading MetaX printed down the vertical fabric banner
    - 后期叠加: label:neutralize_allowed
    - 参考帧: scene_reference ['SCENE_2']
    - 缺失输入: none | 生成假设: ['GA002']
    - guardrail: The vertical banner lettering reads MetaX.
  - **TU002_S2** 6.5-8.0s | ref=action_or_interaction -> tgt=reveal | status=ready_with_assumptions
    - 生成画面: the vertical MetaX fabric banner ripples in the wind while the locked camera and aperture mask stay unchanged
    - 动作/运镜: the banner fabric ripples gently and continuously along its length | static locked-off camera; all motion comes from the fabric
    - 场景迁移: {'scene_entity_id': 'SCENE_2', 'preserve_scene_style': True, 'adapt_scene_content': 'unchanged'}
    - 画面内实体文字/logo: ready:in-scene physical lettering reading MetaX on the rippling vertical banner
    - 后期叠加: label:neutralize_allowed
    - 参考帧: scene_reference ['SCENE_2']
    - 缺失输入: none | 生成假设: none

### TU003  8.0-12.0s  (4.0s)  status=ready_with_assumptions
- 参考功能/目标内容: medium rooftop shot of a small cat in front of large 3D MetaX letters
- 主体: a small ginger-and-cream cat seated at the left of the rooftop
- 镜头语言: medium framing inside the dual aperture mask; subject left, letters behind and above | static locked-off camera
  - **TU003_S1** 8.0-10.0s | ref=visual_display -> tgt=reveal | status=ready_with_assumptions
    - 生成画面: hard cut to a rooftop: a small cat sits at the left with large three-dimensional MetaX letters on the structure behind it
    - 动作/运镜: the cat is revealed seated; it lifts its head and looks to the right | static locked-off camera
    - 场景迁移: {'scene_entity_id': 'SCENE_3', 'preserve_scene_style': True, 'adapt_scene_content': 're-letter the 3D rooftop letters to MetaX and re-scale the set for a small animal protagonist'}
    - 画面内实体文字/logo: ready:in-scene physical three-dimensional lettering reading MetaX on the rooftop structure
    - 后期叠加: label:neutralize_allowed
    - 参考帧: scene_reference ['SCENE_3']
    - 缺失输入: ['MI001'] | 生成假设: ['GA001', 'GA002']
    - guardrail: The rooftop letters read MetaX, and the seated subject is a small ginger-and-cream cat, not a person.
  - **TU003_S2** 10.0-12.0s | ref=action_or_interaction -> tgt=reveal | status=ready_with_assumptions
    - 生成画面: the cat holds its seated posture at the rooftop viewpoint and keeps looking to the right while the locked camera holds
    - 动作/运镜: the cat holds a calm alert posture with only a small head adjustment | static locked-off camera
    - 场景迁移: {'scene_entity_id': 'SCENE_3', 'preserve_scene_style': True, 'adapt_scene_content': 'unchanged'}
    - 画面内实体文字/logo: ready:in-scene physical three-dimensional lettering reading MetaX
    - 后期叠加: label:neutralize_allowed
    - 参考帧: scene_reference ['SCENE_3']
    - 缺失输入: ['MI001'] | 生成假设: ['GA001']

### TU004  12.0-15.0s  (3.0s)  status=ready_with_assumptions
- 参考功能/目标内容: extreme close-up of the cat wearing red geometric sunglasses; the lenses reflect the MetaX lettering and a slight head turn shifts the reflection
- 主体: extreme close-up of the cat's face wearing oversized red geometric sunglasses
- 镜头语言: extreme close-up inside the dual aperture mask; the lens reflection is the focal point | static locked-off camera; motion comes from the head turn
  - **TU004_S1** 12.0-13.5s | ref=visual_display -> tgt=closing | status=ready_with_assumptions
    - 生成画面: hard cut to an extreme close-up of the cat's face wearing oversized red geometric sunglasses that reflect the MetaX lettering
    - 动作/运镜: the cat's head is held facing the camera; the reflection sits steady at the start of the segment | static locked-off camera
    - 场景迁移: {'scene_entity_id': None, 'preserve_scene_style': True, 'adapt_scene_content': 'background falls away; no separate scene entity, this is a subject close-up'}
    - 画面内实体文字/logo: ready:in-scene physical lettering reading MetaX reflected inside the sunglass lenses
    - 后期叠加: label:neutralize_allowed
    - 参考帧: none []
    - 缺失输入: ['MI001'] | 生成假设: ['GA001', 'GA002']
    - guardrail: The lens reflection reads MetaX, and the same single ginger-and-cream cat continues from the rooftop shot.
  - **TU004_S2** 13.5-15.0s | ref=action_or_interaction -> tgt=closing | status=ready_with_assumptions
    - 生成画面: the cat turns its head slightly so the reflected MetaX lettering slides across the sunglass lenses, closing the sequence
    - 动作/运镜: the head rotates slightly; the reflected lettering slides across the lens surface; the camera stays locked | static locked-off camera; all motion comes from the slight head turn
    - 场景迁移: {'scene_entity_id': None, 'preserve_scene_style': True, 'adapt_scene_content': 'background soft and unchanged'}
    - 画面内实体文字/logo: ready:in-scene physical lettering reading MetaX reflected inside the sunglasses, moving as the head turns
    - 后期叠加: label:neutralize_allowed
    - 参考帧: none []
    - 缺失输入: ['MI001'] | 生成假设: ['GA001']
    - guardrail: The moving lens reflection reads MetaX.

## 参考帧摘要 (reference_frame_summary)
- plan_required=True person=0 scene=3 frames=3 level=required_person_scene_anchors
  - three visibly different scene entities (SCENE_1 street, SCENE_2 building exterior, SCENE_3 rooftop) require one scene_reference frame each
  - no person entity exists in the target global element library because the user replaced the model with a cat; a cat is a main subject, not a person, so no person_reference frame is planned under the person/scene-only rule
  - the cat subject appearance is carried by the generation assumption and segment-level appearance details instead of a reference frame

## 缺失项 / 假设 / 验证
- missing_inputs: MI001:primary_subject_reference_image, MI002:brand_logo_asset, MI003:scene_asset, MI004:edge_scouting_ui_label_wording, MI005:dialog_or_voiceover_text
- generation_assumptions: GA001:primary_subject, GA002:brand_wordmark, GA003:scene_content
- validation_flags: explicit_replacement_coverage_verified, no_blocking_items, cat_subject_has_no_reference_frame_by_person_scene_only_rule
- blocking_items: none (readiness ready_with_assumptions)
