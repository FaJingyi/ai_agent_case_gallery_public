# 最终交付审阅稿（dry-run：到 H3 打包为止）

## 运行结论
- 状态: `completed_to_h3_package_dry_run`
- H3 视频生成: `skipped_dry_run`（未提交、未执行；本 dry-run 边界为 H3 request/package）
- H3 请求包: `09_h3_package/h3_request.json`（dry-run，`submitted=false`）
- 参考帧: 2 个（角色 FR_PERSON_HUSKY / 场景 FR_SCENE_LAWN），均已生成并进入 H3 白名单

## 计数
- `timeline_unit_count`: 1（单一参考镜头 SC001）
- `temporal_segment_count`: 6（SEG001-SEG006）
- `h3_prompt_shot_count`: 1（`[Shot 1]`）；另含 `h3_prompt_beat_count`: 6（Beat 1-6，同一连续镜头内部节拍，非参考级镜头拆分）

## 时间轴
| 时间 | 参考功能 | 目标功能 | 生成画面/动作 | 运镜/构图 | 参考帧 | 状态 |
| --- | --- | --- | --- | --- | --- | --- |
| 0.0-0.5s | visual_display | opening_hook | 三只哈士奇并排等距站立面向镜头 | 中远景平视，起幅 | 人物1/场景1 | ready_with_assumptions |
| 0.5-1.5s | action_or_interaction | reveal | 三只同时下蹲、重心下降 | 开始推近 | 人物1/场景1 | ready_with_assumptions |
| 1.5-3.0s | action_or_interaction | 行为推进 | 三只朝镜头小跑汇聚，右侧加速 | 缓慢推近/跟拍，中远景收紧到中景 | 人物1/场景1 | ready_with_assumptions |
| 3.0-4.0s | action_or_interaction | proof 起始 | 右侧哈士奇上抬前爪搭背、开始承重 | 中景，推近收尾 | 人物1/场景1 | ready_with_assumptions |
| 4.0-5.0s | action_or_interaction | proof | 横向队形重组为纵向叠站造型 | 中景，推近停止，构图横→纵 | 人物1/场景1 | ready_with_assumptions |
| 5.0-5.8s | closing_or_prompt | closing | 叠站造型保持并面向镜头 | 静止机位 | 人物1/场景1 | ready_with_assumptions |

## 场景迁移摘要
- `preserve_scene_style`: 自然日光方向、前中后景空间深度、背景密度、真实纪实质感
- `adapt_scene_content`: 室内公共休息区 → 户外公园草坪（绿色草地、自然日光、远景树冠与浅蓝天空）
- 丢弃参考专属内容: 白色圆圈地板标记、灰色沙发、黄色木椅、自动售货机、绿植、红披风卡通立牌、女性背影

## 使用素材
- `参考视频`: test_data/animal/2_2_case4-H3-original.mp4（仅参考构图/运镜/转场/动作机制/镜头顺序/时间节奏/空间关系/连续性/信息揭示结构）
- `人物1`: 08_reference_frames/FR_PERSON_HUSKY.png（生成的角色锚点）
- `场景1`: 08_reference_frames/FR_SCENE_LAWN.png（生成的场景锚点）
- `全局素材1`: test_data/animal/user_input/dog.jpeg（用户主体照片，个体A真实外观）

## 文本/logo 与音频
- 画面内实体文字/logo: 无（参考视频无可读文字；已中性化/省略）
- 后期叠加: `post_overlay_plan` 为空；H3 输出 clean frame
- 台词/口播/旁白: `no_effective_speech`，保留信息节奏不新增文案
- 音乐/BGM/音效: `unsupported_skipped`（仅按固定行交接，不做音频判断）

## 缺失项与禁止项
- 缺失输入: MI001/MI004（两只哈士奇与表演动作按已确认假设生成）、MI002（场景以用户文本声明）、MI003（后期叠加内容缺失，非阻塞）
- 阻塞项: 无
- 负向约束: 全局记录于 `professional_prompt_context`；进入 prompt 的 `compact_guardrails` 共 2 条

## 下一步
- 若需正式出片: 在 `10_h3_video_output/` 下按 `tool-minimax-h3-video-generation-skill` 提交 `09_h3_package/h3_request.json` 的 payload（本 dry-run 未执行）。
