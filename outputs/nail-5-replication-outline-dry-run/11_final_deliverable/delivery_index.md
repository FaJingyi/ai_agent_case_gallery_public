# Delivery Index

- skill: common-video-replication-outline (shot_structure, dry-run -> H3 request/package only)
- outline status: ready_with_assumptions
- timeline_unit_count: 8 | temporal_segment_count: 15 | h3_prompt_shot_count: 15
- 说明: [Shot N]/分镜N 为 prompt-level shots（来自 temporal_segments），reference-level shots 仍为 8 个 timeline units。

## 主产物
- 06_replication_outline/replication_outline.json
- 06_replication_outline/replication_outline.md
- 07_reference_frame_plan/reference_frame_plan.json
- 08_reference_frames/ (3 frames: 1 person + 2 scene)
- 09_h3_package/h3_packager_input.md, reference_mapping.md, pre_generation_checklist.md, minimax_h3_prompt.md, assets/
- 10_h3_video_output/request.json (prepared, NOT submitted)
- run_manifest.json

## reference frames
- frame_person_001 (person_reference) 08_reference_frames/frame_person_001.png -> http://10.42.1.1:30100/v1/assets/asset_8e6bcab6481942dc92b975e1ef2d51cc/content
- frame_scene_001 (scene_reference) 08_reference_frames/frame_scene_001.png -> http://10.42.1.1:30100/v1/assets/asset_9decf1b059164c70b1e7516071696b81/content
- frame_scene_002 (scene_reference) 08_reference_frames/frame_scene_002.png -> http://10.42.1.1:30100/v1/assets/asset_2772f4fe6ea04966b44fa1022d8e8be7/content

## H3
- packager status: prepared; validator: passed
- video generation: skipped (dry-run boundary); request=10_h3_video_output/request.json
