# 复刻大纲审阅稿 (replication_outline.md)

- schema_version: `common_replication_outline.v2`
- status: `ready_with_assumptions`
- replication_mode: `shot_structure`
- generation_scope: `single_generation_task`
- timeline_unit_count: 6
- temporal_segment_count: 11
- 时间精度: 截断到 1 位小数 (truncate)
- 参考视频: 720x1280 / 9:16 / 15.6s / 6 shots / structure_type=before_after
- 目标素材: `asset_1` (`<picture_1>`) — long stiletto-shaped nails in black, taupe and silver metallic foil with 3D eye motifs, pearls and rhinestones
- 参考视频输入: `<video_1>` = VS001 前 15 秒截断版本
- 文字/logo: 目标侧无任何可读文字，参考视频三条中文字幕仅作源侧审计
- 音频: `unsupported_skipped`

## 参考元素处理总览

| element_id | type | decision | 处理摘要 |
| --- | --- | --- | --- |
| `ret_001` | `time_structure` | `inherit` | 15s single-generation duration |
| `ret_002` | `shot_structure` | `inherit` | six-shot order scene content inside each shot is rebuilt for the target dark gothic world |
| `ret_003` | `camera` | `inherit` | handheld static framing with slight drift |
| `ret_004` | `composition` | `inherit` | centered subject placement |
| `ret_005` | `action_structure` | `inherit` | spread-finger palm turn the presented surface becomes the target nail art from <picture_1> the original performer's hand shape and rings as identity evidence |
| `ret_006` | `transition` | `inherit` | hand-to-lens foreground wipe as the before/after boundary the scene revealed after the wipe is the target dark gothic hall |
| `ret_007` | `composition` | `inherit` | upper-left rectangular inset position inset content shows the target nail art from <picture_1> |
| `ret_008` | `transition` | `inherit` | direct hard cut on the same location |
| `ret_009` | `camera` | `inherit` | macro hand detail framing |
| `ret_010` | `subject_content` | `adapt` | the nail surface is the hero detail of the after state replace the nail art pattern with the user asset nail art from <picture_1> (long stiletto-shaped nails in black, taupe and silver metallic foil with 3D eye motifs, pearls and rhinestones) original blue/white/black motif set |
| `ret_011` | `person_or_body` | `adapt` | same body part ownership across shots a non-identifiable young adult woman with long straight black hair, neutral confident expression presented as a non-identifiable performer; wardrobe rebuilt as dark gothic garments that match the nail art palette original identifiable person |
| `ret_012` | `scene_content` | `adapt` | enclosed starting space a compact dark gothic anteroom: black velvet curtain, tall antique mirror, brass wall sconce, dark plaster wall, low-key warm practical light for the opening shots and a deep dark gothic atelier hall: tall blackened metal lattice window frames, deep green-black velvet drapes, dark stone floor, candle-like practical lights, cool blue night light through the lattice from the reveal onward; scene direction comes from the user style requirement white indoor doorway wall |
| `ret_013` | `visual_style` | `adapt` | consistent single light setup across all shots low-key moody dark interior lighting with cool blue window light and warm brass practicals; controlled highlights on the metallic nail surface bright high-key daylight |
| `ret_014` | `prop` | `adapt` | a small handheld botanical prop is pinched between two fingers in the macro detail shot a small dark botanical prop (deep plum-black dried flower sprig with silver-grey leaves) that matches the dark gothic palette bright yellow wildflower |
| `ret_015` | `text_or_ui` | `discard` | the opening POV subtitle text |
| `ret_016` | `watermark_or_platform_ui` | `discard` | any platform UI, account watermark or corner badge would be excluded if present |
| `ret_017` | `unsupported_audio` | `discard` | background music |
| `ret_018` | `incidental_detail` | `discard` | silver rings |

## 时间轴

### TU001 — 参考 VS001:shot1（0.0 - 3.0 s，3.0 s）

- 参考功能: `opening_hook` / 目标功能: establish the plain before state and start the hand presentation chain
- content_subject_type: `mixed`
- 使用素材: <video_1>(ref_video_excerpt_VS001)
- 生成画面: a non-identifiable woman stands in a dark anteroom with her hands on her hips, then lifts and presents her plain nails and pushes both hands toward the lens
- 动作/运镜: standing with hands on hips; lifting both hands; turning the palms to the lens; pushing forward toward the lens / mostly static with a slight handheld drift
- 场景迁移: a compact dark gothic anteroom: black velvet curtain, tall antique mirror, brass wall sconce, dark plaster wall, low-key warm practical light
- 台词/口播/画面文字: no spoken line; the shot only shows the before state and a calm confident look toward the lens
- 画内实体文字/logo 状态: 无（目标侧未提供任何文字或 logo）
- 后期叠加状态: 无（参考字幕按源侧审计丢弃，H3 输出 clean plate）
- 参考帧决策: role=person_reference / status=needed

| segment | 时间 | 参考功能 | 目标功能 | 参考帧 entity/state |
| --- | --- | --- | --- | --- |
| `SEG001a` | 0.0-1.5 s | `visual_display` | establish the before state | person_1,nail_art_design,scene_dark_atelier / person_state_initial,nail_state_base,scene_state_anteroom |
| `SEG001b` | 1.5-3.0 s | `action_or_interaction` | run the hand presentation chain and launch the wipe | person_1,nail_art_design / person_state_initial,nail_state_base |

- 审计项: ncon_global_001; ncon_global_002; ncon_global_003; ncon_global_004; ncon_global_005; ncon_global_006
- 缺失项: 无

### TU002 — 参考 VS001:shot2（3.0 - 4.0 s，1.0 s）

- 参考功能: `transition` / 目标功能: carry the before/after boundary with a hand foreground wipe
- content_subject_type: `abstract_motion`
- 使用素材: <video_1>(ref_video_excerpt_VS001)
- 生成画面: both hands rush into the lens and wipe the anteroom away, revealing the dark hall
- 动作/运镜: hands enter the lens; frame is filled; new space is revealed / static; the subject's hands create the motion
- 场景迁移: a compact dark gothic anteroom: black velvet curtain, tall antique mirror, brass wall sconce, dark plaster wall, low-key warm practical light wiped away into a deep dark gothic atelier hall: tall blackened metal lattice window frames, deep green-black velvet drapes, dark stone floor, candle-like practical lights, cool blue night light through the lattice
- 台词/口播/画面文字: no spoken line; the wipe carries the before/after information change
- 画内实体文字/logo 状态: 无（目标侧未提供任何文字或 logo）
- 后期叠加状态: 无（参考字幕按源侧审计丢弃，H3 输出 clean plate）
- 参考帧决策: role=person_reference / status=needed

| segment | 时间 | 参考功能 | 目标功能 | 参考帧 entity/state |
| --- | --- | --- | --- | --- |
| `SEG002a` | 3.0-4.0 s | `transition` | execute the before/after wipe boundary | person_1,scene_dark_atelier / person_state_final,scene_state_hall |

- 审计项: ncon_global_001; ncon_global_002; ncon_global_003; ncon_global_004; ncon_global_005; ncon_global_006
- 缺失项: 无

### TU003 — 参考 VS001:shot3（4.0 - 9.0 s，5.0 s）

- 参考功能: `reveal` / 目标功能: reveal the finished target nail art in the dark gothic hall
- content_subject_type: `mixed`
- 使用素材: <video_1>(ref_video_excerpt_VS001), <picture_1>(asset_1)
- 生成画面: the same performer, now in the dark gothic lace outfit, raises both hands to her face and presents the finished dark gothic nails in the hall
- 动作/运镜: hands raised in front of the face; palms and fingertips turned to the lens; hands moved beside cheek and chin; head tilt; one hand lowered / handheld medium close-up with a slight drift
- 场景迁移: a deep dark gothic atelier hall: tall blackened metal lattice window frames, deep green-black velvet drapes, dark stone floor, candle-like practical lights, cool blue night light through the lattice
- 台词/口播/画面文字: no spoken line; the shot only holds a pleased look toward the lens
- 画内实体文字/logo 状态: 无（目标侧未提供任何文字或 logo）
- 后期叠加状态: 无（参考字幕按源侧审计丢弃，H3 输出 clean plate）
- 参考帧决策: role=person_reference / status=needed

| segment | 时间 | 参考功能 | 目标功能 | 参考帧 entity/state |
| --- | --- | --- | --- | --- |
| `SEG003a` | 4.0-6.0 s | `visual_display` | reveal the finished nail art | person_1,nail_art_design,scene_dark_atelier / person_state_final,nail_state_art,scene_state_hall |
| `SEG003b` | 6.0-7.0 s | `text_overlay_or_information_reveal` | hold the presentation pose at the information peak | person_1,nail_art_design / person_state_final,nail_state_art |
| `SEG003c` | 7.0-9.0 s | `action_or_interaction` | close the reveal and prepare the cut | person_1,nail_art_design / person_state_final,nail_state_art |

- 审计项: ncon_global_001; ncon_global_002; ncon_global_003; ncon_global_004; ncon_global_005; ncon_global_006
- 缺失项: 无

### TU004 — 参考 VS001:shot4（9.0 - 11.0 s，2.0 s）

- 参考功能: `proof` / 目标功能: prove nail surface detail with a macro shot and a picture-in-picture inset
- content_subject_type: `mixed`
- 使用素材: <video_1>(ref_video_excerpt_VS001), <picture_1>(asset_1)
- 生成画面: a macro shot of one hand holding a small dark botanical prop, with an upper-left picture-in-picture inset showing a second view of the same nails
- 动作/运镜: cut to macro; fingers curl around the prop; hand rotates toward the lens; inset stays mounted / nearly static, hand-led rotation
- 场景迁移: a deep dark gothic atelier hall: tall blackened metal lattice window frames, deep green-black velvet drapes, dark stone floor, candle-like practical lights, cool blue night light through the lattice
- 台词/口播/画面文字: no spoken line; the shot is a silent detail proof
- 画内实体文字/logo 状态: 无（目标侧未提供任何文字或 logo）
- 后期叠加状态: 无（参考字幕按源侧审计丢弃，H3 输出 clean plate）
- 参考帧决策: role=subject_reference / status=needed

| segment | 时间 | 参考功能 | 目标功能 | 参考帧 entity/state |
| --- | --- | --- | --- | --- |
| `SEG004a` | 9.0-9.5 s | `transition` | cut into macro and start the prop hold | nail_art_design,botanical_prop / nail_state_art,prop_state_single |
| `SEG004b` | 9.5-11.0 s | `visual_display` | hold the macro detail with the inset composition | nail_art_design,botanical_prop,scene_dark_atelier / nail_state_art,prop_state_single,scene_state_hall |

- 审计项: ncon_global_001; ncon_global_002; ncon_global_003; ncon_global_004; ncon_global_005; ncon_global_006
- 缺失项: 无

### TU005 — 参考 VS001:shot5（11.0 - 12.5 s，1.5 s）

- 参考功能: `proof` / 目标功能: re-present the nails against the metal lattice structure
- content_subject_type: `human`
- 使用素材: <video_1>(ref_video_excerpt_VS001), <picture_1>(asset_1)
- 生成画面: the performer raises both hands again with the black metal lattice window frames behind her
- 动作/运镜: hands raised with fingers spread; one hand moves toward the cheek; the other hand stays raised / steady handheld, slight drift
- 场景迁移: a deep dark gothic atelier hall: tall blackened metal lattice window frames, deep green-black velvet drapes, dark stone floor, candle-like practical lights, cool blue night light through the lattice with the lattice window frames prominent
- 台词/口播/画面文字: no spoken line; a calm satisfied look toward the lens
- 画内实体文字/logo 状态: 无（目标侧未提供任何文字或 logo）
- 后期叠加状态: 无（参考字幕按源侧审计丢弃，H3 输出 clean plate）
- 参考帧决策: role=person_reference / status=needed

| segment | 时间 | 参考功能 | 目标功能 | 参考帧 entity/state |
| --- | --- | --- | --- | --- |
| `SEG005a` | 11.0-12.5 s | `visual_display` | re-present the nails with the lattice background | person_1,nail_art_design,scene_dark_atelier / person_state_final,nail_state_art,scene_state_hall |

- 审计项: ncon_global_001; ncon_global_002; ncon_global_003; ncon_global_004; ncon_global_005; ncon_global_006
- 缺失项: 无

### TU006 — 参考 VS001:shot6（12.5 - 15.0 s，2.5 s）

- 参考功能: `closing_or_prompt` / 目标功能: close on the same nails in a heavier dark wardrobe
- content_subject_type: `human`
- 使用素材: <video_1>(ref_video_excerpt_VS001), <picture_1>(asset_1)
- 生成画面: the performer wears the long black velvet coat and wide-brim hat, presents both hands, crouches down and rises again with the hands still shown
- 动作/运镜: hands raised toward the lens; one hand to the cheek; crouch down while the hands stay near the face; rise again with the hands presented / handheld, follows the crouch and rise
- 场景迁移: a deep dark gothic atelier hall: tall blackened metal lattice window frames, deep green-black velvet drapes, dark stone floor, candle-like practical lights, cool blue night light through the lattice
- 台词/口播/画面文字: no spoken line; a calm closing look toward the lens
- 画内实体文字/logo 状态: 无（目标侧未提供任何文字或 logo）
- 后期叠加状态: 无（参考字幕按源侧审计丢弃，H3 输出 clean plate）
- 参考帧决策: role=person_reference / status=needed

| segment | 时间 | 参考功能 | 目标功能 | 参考帧 entity/state |
| --- | --- | --- | --- | --- |
| `SEG006a` | 12.5-13.5 s | `action_or_interaction` | open the closing beat with the wardrobe change | person_1,nail_art_design / person_state_wardrobe,nail_state_art |
| `SEG006b` | 13.5-15.0 s | `closing_or_prompt` | close the clip with a continuous crouch and rise | person_1,nail_art_design,scene_dark_atelier / person_state_wardrobe,nail_state_art,scene_state_hall |

- 审计项: ncon_global_001; ncon_global_002; ncon_global_003; ncon_global_004; ncon_global_005; ncon_global_006
- 缺失项: 无

## 记忆点迁移

| memory_id | 保留机制 | 目标改写 | 绑定 |
| --- | --- | --- | --- |
| `vm_001` | hand-to-lens foreground wipe as the before/after boundary; front-ward hand motion with increasing speed | the wipe still separates the before state from the after state, but both spaces are rebuilt as the dark anteroom and the dark hall; the hands keep the front-ward accelerating path | SEG001b, SEG002a |
| `vm_002` | picture-in-picture inset position and layered composition; main close-up plus secondary nail view | the inset keeps its upper-left rectangular position and stays mounted for the whole beat, but its content shows the target nail art instead of the reference nails | SEG004b |
| `vm_003` | spread-finger palm turn; lift-to-face presentation pause; front-ward hand push at the end | the presentation chain keeps its pose sequence and short pauses but is performed by the non-identifiable target performer in the dark gothic wardrobe inside the dark hall | SEG001b, SEG003a, SEG003b, SEG005a, SEG006a, SEG006b |
| `vm_004` | macro hand detail framing; slow rotation to keep surface detail toward the lens | the macro framing and slow rotation are kept, but the bright yellow wildflower becomes a small dark botanical prop that matches the nail palette | SEG004a, SEG004b |
| `sm_001` | open with a stance/situation hook; the hook is immediately followed by the initial-state hand display | the target keeps the hook-then-initial-state ordering, but the hook is carried visually by the plain-nail presentation instead of any subtitle copy | SEG001a, SEG001b |
| `sm_002` | before/after contrast on the same subject and the same body part; occlusion transition as the before/after boundary | the same-hands before/after contrast is kept: the plain nail base is replaced by the user asset nail art across the wipe, and the anteroom is replaced by the hall | SEG002a, SEG003a |
| `sm_003` | premise -> initial -> transition -> result -> detail -> re-presentation release order; every presentation points the hands at the lens | the release order is preserved across the six target shots; the presentation chain points the hands at the lens in every after-state shot | target_video, TU001, TU003, TU004, TU005, TU006 |
| `sm_004` | premise setup and payoff across shots; the payoff beat follows the result picture immediately | the setup/payoff pairing is kept as the wipe reveal followed by the macro detail proof, with no subtitle copy on the target side | SEG003a, SEG004a |

## 参考帧摘要

```json
{
  "frame_requirement_level": "required_visual_anchors",
  "plan_required": true,
  "plan_path": "07_reference_frame_plan/reference_frame_plan.json",
  "person_entity_count": 1,
  "subject_entity_count": 1,
  "scene_entity_count": 1,
  "state_frame_count": 5,
  "planned_frame_count": 0,
  "selected_h3_image_count": 0,
  "merged_frame_count": 0,
  "h3_image_budget": 8,
  "ready_frame_ids": [],
  "summary_status": "ready",
  "triggered_rules": [
    "person_reference_entity_present",
    "subject_reference_entity_present",
    "scene_reference_entity_present",
    "appearance_state_change_present"
  ],
  "notes": [
    "planned_frame_count is finalized in Step 7"
  ]
}
```

## H3 package 状态

- Step 9 H3 prompt/request: 由 `09_h3_package/` 产出，详见 `h3_prompt_lint_report.json`
- Step 10 H3 视频生成: dry-run 边界内未提交
