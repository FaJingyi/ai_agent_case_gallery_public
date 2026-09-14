# Pre-Generation Checklist

- [x] 参考视频绑定: http://10.42.1.1:30100/v1/assets/asset_13a9ed64612548b2a0f1bd8c80e8c701/content (motion/camera/timing reference only)
- [x] material count: 参考视频 1 + 人物1 1 + 场景 2 + 全局素材1 1 = 4 images + 1 video (<= H3 5-image limit)
- [x] shot count: 15 prompt-level shots from 15 temporal_segments across 8 timeline units
- [x] timeline_unit_count=8, temporal_segment_count=15, h3_prompt_shot_count=15
- [x] all material URLs are http(s) and service-reachable
- [x] replacement target 全局素材1 (深色哥特眼球图案长款美甲（黑/深褐/灰褐底，写实眼球图案＋白色珍珠＋金色圆珠＋金属亮片，高光泽树脂/凝胶质感）) appears in every affected shot sentence
- [x] special mechanism sm_trans_001 (contrast hard cut, 分镜3) preserved with before/after state
- [x] special mechanism sm_obs_001 (top-left picture-in-picture, 分镜8/分镜9) preserved as visible layout, not post overlay
- [x] negative constraints kept as audit/compact guardrails; not stacked per shot
- [ ] human review of generated reference frames (recorded, not gated)

## missing / blocking
- mi_001 nail_art_worn_on_hands: missing_generate_fallback (resolved by ga_001 usage-state assumption)
- mi_002 on_screen_subtitle: missing_required_input (omit/neutralize; no subtitle rendered by video model)
- blocking_items: none

## prompt-level vs reference-level
- 分镜N are prompt-level shots generated from temporal_segments; reference-level shots remain 8 timeline units.
