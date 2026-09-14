| Label | File | Role | Segment | Purpose |
| --- | --- | --- | --- | --- |
| picture 1 | assets/FR_PERSON_HUSKY.png | person_reference (generated) | SEG001-SEG006 | 三只哈士奇角色外观锚点（个体A对齐 全局素材1） |
| picture 2 | assets/FR_SCENE_LAWN.png | scene_reference (generated) | SEG001-SEG006 | 户外草坪场景锚点（草地/日光/色调/空间层次） |
| picture 3 | assets/A001.jpeg | primary_subject_reference (user asset) | SEG001-SEG006 | 用户提供主体照片，个体A真实外观参考 |
| video 1 | test_data/animal/2_2_case4-H3-original.mp4 | motion_camera_timing_reference (reference video) | SEG001-SEG006 | 构图/运镜/动作机制/镜头顺序/时间节奏/连续性参考 |

备注：参考视频服务地址 `http://10.42.1.1:30100/v1/assets/asset_6a7143e4263944d9b66003792c363b92/content`；`picture 1`/`picture 2` 为步骤 8 生成并通过提交前质检的纯人物/纯场景参考帧；`picture 3` 为用户素材，包内 `assets/A001.jpeg` 为 768x768 的 720p 级打包副本（原图 1242x1242，仅用于打包尺寸规范）。
本包仅为 H3 打包输入与 dry-run request，未提交视频生成。
