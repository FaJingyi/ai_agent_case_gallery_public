# 复刻大纲审阅稿（replication_outline.md）

- schema: `common_replication_outline.v2`
- status: `ready_with_assumptions`
- generation_scope: `single_generation_task`
- 目标视频: 13.9s / 9:16 / 主体=British man from user asset man.jpeg
- 场景: UK city street → UK park
- 替换道具: fresh glossy red apple (replaces the source drink cup)
- 旁白: en / generated_from_reference_asr_function

## 强继承 / 参考继承

强继承项：
- `si_time_structure` (time_structure): 8-shot linear order, ~1.8s average, montage/action pacing, environment first then prop reveal then closing hold
- `si_shot1_camera` (camera_language): slightly low eye-level frontal medium shot, subject centered, slight handheld
- `si_shot2_camera` (camera_language): close side profile, subject fills frame, shallow green bokeh
- `si_shot3_camera` (camera_language): back-view medium shot, subject in lower midground, three-layer depth
- `si_shot4_camera` (camera_language): extreme close-up micro texture, extremely shallow focus
- `si_shot5_camera` (camera_language): extreme close-up face on trunk, extremely shallow focus
- `si_shot6_camera` (camera_language): low-angle medium shot, sky above canopy
- `si_shot7_camera` (camera_language): close-up of face and held object, green bokeh
- `si_shot8_camera` (camera_language): full shot, seated centered on wide steps, columned facade behind
- `si_hard_cuts` (transition_mechanism): every boundary is a direct hard cut
- `si_foreground_framing_shot3` (special_composition): shot3 out-of-focus leaf band forms a foreground frame across the top edge; three-layer foreground/midground/background space
- `si_spatial_relations` (space_relation): vertical full-frame; layered fore/mid/background; subject occupies the main area
- `si_contact_escalation` (form_memory_point): contact intensity escalates hand -> cheek -> embrace as emotional high point, then returns to calm

参考继承项（目标侧改写）：
- `ri_subject` (person_identity): long black-haired young woman in white clothing → replace with the British man from the user asset (tan jacket, dark brown collar, white tee, short light-brown swept-up hair)
- `ri_scene` (scene_content): European town street, forest, mossy trunk, stone steps → adapt to UK city street and UK park per user text; keep lighting/depth/composition style
- `ri_prop_drink` (prop): transparent straw cup with blue label (milk tea) → replace with a fresh glossy red apple in SH007-SH008, continuous as the same apple
- `ri_voiceover` (voiceover_text): 4 Chinese voiceover lines tied to the contact/prop beats → generate 4 English voiceover lines with the same information function and placement
- `ri_brand_logo` (logo): source brand logo「树夏 SUMMER JUICE」and packaging text → discard; audit only, never enter the target frame
- `ri_subtitles` (screen_text): burned-in Chinese subtitles in shot4-shot7 → discard; no target subtitle text authorized, keep clean plate
- `ri_micro_hand_touch` (micro_action): fingers touch and slide slowly across the mossy trunk → adapt to the man's hand sliding slowly across UK park tree bark, keeping contact point, direction and end pause
- `ri_micro_embrace` (micro_action): both arms wrap the trunk and hold with closed eyes → adapt to the man embracing the UK park tree, keeping the full wrap, slight sway and closed-eye hold
- `ri_micro_object_to_face` (micro_action): held object lifts toward the face and tilts closer with a closed-eye pause → adapt to the man raising the apple toward his face, tilting it closer and closing his eyes
- `ri_micro_raise_object` (micro_action): look down at the held object, lift it, raise the head and smile with a short hold → adapt to the man looking down at the apple, lifting it and raising his head with a calm smile
- `ri_book_prop` (prop): white book/folder carried in shot1 and shot3 → adapt to a plain neutral closed notebook carried consistently, no readable text

降级项: 0 项

## 旁白/文本迁移

- speech_status: `voiceover`
- `tt_vo_001` (voiceover, en) → ['S004']: "I live between the city and the green."
- `tt_vo_002` (voiceover, en) → ['S005']: "Breathing in the same quiet rhythm."
- `tt_vo_003` (voiceover, en) → ['S006']: "Between fast and slow,"
- `tt_vo_004` (voiceover, en) → ['S007']: "this is just right."

## 时间轴

### SH001（0.0-0.8s, 0.8s）

- 功能: establish the man and the UK city street
- 视角: slightly low eye-level frontal view (inherited from reference shot1)
- 构图: vertical 9:16 full frame；medium shot, waist-up, subject centered；slightly low camera；paved street midground, brick/stone buildings background；subject occupies center vertical band
- 运镜: subtle handheld sway, near-static｜焦点: subject sharp, background slightly soft
- 转场: hard cut to next shot｜节奏: quick 0.8s establishing beat (montage rhythm)
- 画面: a man walks toward the camera on a UK street and turns his head to screen-left
- 动作迁移: close_motion_reference｜the British man walks steadily toward camera, turns his head to screen-left, short hair moves with his step
  - segment `S001` (0.0-0.8s, 0.8s): man walks toward camera and turns head to screen-left
- 参考帧需求: merged_reference / entities=['person_man_01', 'scene_uk_street_01']
- 状态: `ready`

### SH002（0.8-1.6s, 0.8s）

- 功能: shift from street into calm park nature
- 视角: side-profile, near eye-level close view (inherited from reference shot2)
- 构图: vertical 9:16；close-up side profile, head and shoulder；subject filling most of frame；deep green blurred park bokeh background
- 运镜: almost static, only faint head and hair motion｜焦点: shallow depth of field, face sharp, background soft bokeh
- 转场: hard cut from street to park｜节奏: short 0.8s transition beat
- 画面: close side profile of the man with eyes closed, head slightly tilted up, against green park bokeh
- 动作迁移: close_motion_reference｜the man keeps his eyes closed with his head tilted slightly up, only faint movement in his hair
  - segment `S002` (0.8-1.6s, 0.8s): eyes closed side profile against green park bokeh
- 参考帧需求: merged_reference / entities=['person_man_01', 'scene_uk_park_01']
- 状态: `ready`

### SH003（1.6-3.8s, 2.2s）

- 功能: show the man settled inside the park under the leaves
- 视角: back view, near eye-level medium shot (inherited from reference shot3)
- 构图: vertical 9:16；back-view medium shot, man in lower midground；leaf band forming an out-of-focus foreground frame across the top edge；three-layer space: blurred foreground leaves / sharp midground man / soft deep-green background
- 运镜: basically fixed, only faint subject sway｜焦点: foreground blurred, midground sharp, background softly blurred
- 转场: hard cut in and out｜节奏: 2.2s developing beat
- 画面: back-view medium shot of the man standing under park trees, hands behind his back holding a plain notebook, wind moving his hair, leaves framing the top of the frame
- 动作迁移: close_motion_reference｜the man stands with his back to camera, both hands behind his back holding a plain notebook, wind moving his short hair
- 特殊机制: special_composition: A soft out-of-focus band of green leaves hangs across the top edge of the frame, framing the man who stands in the lower midground, with deeper park foliage softly blurred behind him.
  - segment `S003` (1.6-3.8s, 2.2s): back-view man under park trees with a leaf foreground frame
- 参考帧需求: merged_reference / entities=['person_man_01', 'scene_uk_park_01']
- 状态: `ready`

### SH004（3.8-5.7s, 1.9s）

- 功能: first tactile contact with nature; first voiceover line
- 视角: extreme close-up, near eye-level (inherited from reference shot4)
- 构图: vertical 9:16；extreme close-up of the hand on the bark；subject hand occupies most of the frame；texture is the main subject
- 运镜: essentially static with very slight handheld float｜焦点: extremely shallow depth of field, razor-thin focal plane on the bark and hand
- 转场: hard cut in and out｜节奏: slow 1.9s sensory beat with a pause at the end
- 画面: extreme close-up of the man's hand touching and slowly sliding along park tree bark
- 动作迁移: close_motion_reference｜the man's hand rests on the bark, then his fingers slide slowly from one side to the other and pause briefly
  - segment `S004` (3.8-5.7s, 1.9s): hand slides slowly on park tree bark; voiceover line 1｜旁白 `tt_vo_001`: "I live between the city and the green."
- 参考帧需求: merged_reference / entities=['person_man_01', 'scene_uk_park_01']
- 状态: `ready`

### SH005（5.7-7.8s, 2.1s）

- 功能: contact escalates from hand to face; second voiceover line
- 视角: extreme close-up of the face, near eye-level (inherited from reference shot5)
- 构图: vertical 9:16；face close-up with cheek against the trunk；face occupies most of the frame；bark texture visible beside the cheek
- 运镜: static with faint breathing motion｜焦点: extremely shallow focus on the cheek and bark contact
- 转场: hard cut in and out｜节奏: 2.1s sensory beat
- 画面: extreme close-up of the man's cheek resting on the same tree trunk, eyes open looking to screen-right
- 动作迁移: close_motion_reference｜the man keeps his cheek against the bark, breathing faintly, eyes open toward screen-right
  - segment `S005` (5.7-7.8s, 2.1s): cheek against tree trunk, eyes open right; voiceover line 2｜旁白 `tt_vo_002`: "Breathing in the same quiet rhythm."
- 参考帧需求: merged_reference / entities=['person_man_01', 'scene_uk_park_01']
- 状态: `ready`

### SH006（7.8-9.6s, 1.8s）

- 功能: emotional high point: full embrace; third voiceover line
- 视角: low-angle medium shot (inherited from reference shot6)
- 构图: vertical 9:16；low-angle medium shot；man centered hugging the trunk；bright sky and leaves above the frame
- 运镜: essentially static｜焦点: medium depth, man sharp, sky/leaves above
- 转场: hard cut in and out｜节奏: 1.8s hold-type beat
- 画面: low-angle medium shot of the man with both arms wrapped around the park tree trunk, eyes closed
- 动作迁移: close_motion_reference｜the man wraps both arms around the trunk, holds the embrace, sways faintly with his eyes closed
  - segment `S006` (7.8-9.6s, 1.8s): man embraces the park tree, eyes closed; voiceover line 3｜旁白 `tt_vo_003`: "Between fast and slow,"
- 参考帧需求: merged_reference / entities=['person_man_01', 'scene_uk_park_01']
- 状态: `ready`

### SH007（9.6-12.0s, 2.4s）

- 功能: reveal the apple prop; fourth voiceover line
- 视角: close-up, near eye-level (inherited from reference shot7)
- 构图: vertical 9:16；close-up of the man's face and the apple；apple held near the face at frame centre-right；green park bokeh background
- 运镜: very slight handheld float｜焦点: shallow depth of field, face and apple sharp, background bokeh
- 转场: hard cut in and out｜节奏: 2.4s reveal beat
- 画面: close-up of the man holding a fresh red apple near his face and tilting it slightly toward him, eyes closed
- 动作迁移: close_motion_reference｜the man raises the apple toward his face, tilts it slightly closer, closes his eyes and holds
  - segment `S007` (9.6-12.0s, 2.4s): man holds a red apple near his face, eyes closed; voiceover line 4｜旁白 `tt_vo_004`: "this is just right."
- 参考帧需求: merged_reference / entities=['person_man_01', 'scene_uk_park_01']
- 状态: `ready`

### SH008（12.0-13.9s, 1.9s）

- 功能: closing beat with a calm smile
- 视角: full shot, near eye-level with a slight high angle (inherited from reference shot8)
- 构图: vertical 9:16；full shot；man seated and centered on wide stone steps；columned building facade behind
- 运镜: fixed｜焦点: medium depth, man and steps sharp, facade softly resolved
- 转场: end of the video｜节奏: 1.9s closing hold
- 画面: full shot of the man sitting on the wide stone steps of a UK building, looking down at the apple, then lifting it and raising his head with a smile
- 动作迁移: close_motion_reference｜the man sits on the steps, looks down at the apple, lifts it and raises his head with a calm smile
  - segment `S008` (12.0-13.9s, 1.9s): seated on steps, look down at the apple, lift it, raise head and smile
- 参考帧需求: merged_reference / entities=['person_man_01', 'scene_uk_street_01']
- 状态: `ready`

## 全局外观元素库（第二层去重结果）

- `person_man_01` (person_appearance): European man, young adult；short light-brown hair swept up；clean-shaven, friendly calm expression（合并状态: merged）
- `scene_uk_street_01` (scene_appearance): UK town street with red-brick and pale-stone facades；black iron railings；paved pavement（合并状态: merged）
- `scene_uk_park_01` (scene_appearance): UK public park with mature trees and mown grass；deep green foliage；out-of-focus leaf band across the top edge in SH003（合并状态: merged）
- `prop_apple_01` (prop_context_appearance): fresh glossy red apple；held in the right hand；nested under the person entity, no standalone reference frame（合并状态: merged）
- `style_atmosphere_01` (style_atmosphere): soft overcast and diffused green daylight；fresh realistic texture；green-dominant palette with warm facade accents（合并状态: merged）

## 参考帧摘要

- plan_required=True, person=1, scene=2, planned_frame_count=3, budget=8
- plan_path=`07_reference_frame_plan/reference_frame_plan.json`
- notes: person_man_01 reuses the user asset man.jpeg；scene_uk_street_01 and scene_uk_park_01 are text_to_image frames；prop_apple_01 is folded into person/scene context and produces no standalone frame

## 记忆点迁移

- `vm_001` → ['timeline_units[SH003].unit_id', 'temporal_segments[S003].segment_id']
- `vm_002` → ['timeline_units[SH004].unit_id', 'timeline_units[SH005].unit_id']
- `vm_003` → ['temporal_segments[S004].segment_id']
- `vm_004` → ['temporal_segments[S006].segment_id']
- `vm_005` → ['temporal_segments[S007].segment_id']
- `vm_006` → ['temporal_segments[S008].segment_id']
- `sm_001` → ['target_video', 'timeline_units[SH001..SH008]']
- `sm_002` → ['target_video', 'timeline_units[SH004..SH008]']
- `sm_003` → ['temporal_segments[S007].segment_id', 'temporal_segments[S008].segment_id']

## 缺口 / 假设 / 审计

- missing_inputs: ['mi_scene', 'mi_voiceover']
- generation_assumptions: ['ga_001', 'ga_002', 'ga_003', 'ga_004']
- validation_flags: ['target_scene_depends_on_generation_assumption_with_user_instruction', 'source_brand_and_packaging_text_neutralized', 'voiceover_language_switched_to_english_by_user', 'target_scene_reference_frames_planned_as_text_to_image']
- unsupported_audio: ['music_bgm', 'sound_effects', 'singing', 'voice_emotion', 'beat_sync_rhythm']

## 文字/logo 策略

- 源品牌「树夏 SUMMER JUICE」、包装文字、烧录中文字幕：仅审计，不入目标画面（`exclude_or_neutralize`）。
- 目标侧无已确认可读文字/字幕授权；H3 生成 clean plate，字幕/叠加默认后期 ffmpeg/opencv 处理。
