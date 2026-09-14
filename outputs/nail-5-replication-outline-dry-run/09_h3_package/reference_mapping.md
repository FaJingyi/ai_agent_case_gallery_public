# Reference Mapping

## picture n -> package asset (packager view)

| Label | File | Role | Segment | Purpose |
| --- | --- | --- | --- | --- |
| picture 1 | assets/global_material_1.png | target_nail_art_pattern_reference | all | target subject authority (nail art, resized 768x768) |
| picture 2 | assets/person_1.png | person_reference | all | person appearance consistency |
| picture 3 | assets/scene_1.png | scene_reference | tu_001 | indoor scene consistency |
| picture 4 | assets/scene_2.png | scene_reference | tu_002-tu_008 | outdoor scene consistency |

<Video 1> = reference video excerpt (motion/camera/timing reference).

## material name -> source


| Label | Package Path | Media URL | Role | Entity/Frame | Segments |
| --- | --- | --- | --- | --- | --- |
| 参考视频 | (H3 <Video 1>) | http://10.42.1.1:30100/v1/assets/asset_13a9ed64612548b2a0f1bd8c80e8c701/content | motion_camera_timing_reference | VS001 | all |
| 人物1 | assets/person_1.png | http://10.42.1.1:30100/v1/assets/asset_8e6bcab6481942dc92b975e1ef2d51cc/content | person_reference | ge_person_001 / frame_person_001 | all |
| 场景1 | assets/scene_1.png | http://10.42.1.1:30100/v1/assets/asset_9decf1b059164c70b1e7516071696b81/content | scene_reference | ge_scene_001 / frame_scene_001 | tu_001 |
| 场景2 | assets/scene_2.png | http://10.42.1.1:30100/v1/assets/asset_2772f4fe6ea04966b44fa1022d8e8be7/content | scene_reference | ge_scene_002 / frame_scene_002 | tu_002-tu_008 |
| 全局素材1 | assets/global_material_1.png | http://10.42.1.1:30100/v1/assets/asset_e19e3a65f9d442428c4cc224e5799858/content | target_nail_art_pattern_reference | h3_asset_user_001 / ge_subject_001 | all |

## material name -> source
- 人物1: generated pure person reference (frame_person_001 -> ge_person_001)
- 场景1: generated pure scene reference (frame_scene_001 -> ge_scene_001)
- 场景2: generated pure scene reference (frame_scene_002 -> ge_scene_002)
- 全局素材1: user asset test_data/nail-5/user_input/shangpin-3.png (h3_asset_user_001)
- 参考视频: test_data/nail-5/nail-5.mp4 first 15.0s (h3_asset_reference_video_excerpt)

- global_material_1 packaged copy is a 768x768 resize of the original 1639x1639 user asset (packager 720p-level rule); H3 request uses the resized upload URL: http://10.42.1.1:30100/v1/assets/asset_c312d5e2650f41258b8483c0c3aeeb48/content
