# 最终交付审阅稿 (minimax-replication-outline dry run)

- 状态: `ready_with_assumptions` | 生成范围: `single_generation_task` | 时长: 15.0s
- 参考视频: `test_data/minimax/minimax.mp4` (前 15.0s 截断版本)
- 用户需求: 参考视频生成一条新的视频，把视频里所有"minimax"字母换成"MetaX"，把视频中的模特换成猫咪
- timeline_unit_count: 4 | temporal_segment_count: 8 | h3_prompt_shot_count: 4
- 说明: H3 prompt 的 `[Shot N]` 是 prompt-level shots (4 个, 对应参考级 4 个 shot); 每个 shot 内保留 8 个 temporal_segments 作为 beat 级时间范围, 未合并.

## 显式替换覆盖
- `REP001`: on-screen 'minimax' lettering / MINIMAX wordmark -> **MetaX** | segments 8/8 visible | status `covered`
- `REP002`: the model / the woman appearing in the reference video -> **cat** | segments 4/4 visible | status `covered`
- binding status: `passed`

## TU001  0.0-4.0s (4.0s)  [ready_with_assumptions]
- 参考功能: `opening_hook` | 内容类型: `text_graphic`
- 生成画面: MetaX-branded bus-stop shelter on a warm city street
- 生成动作/运镜: held; only the lettering shadow drifts; static locked-off camera; eye-level observational POV
- 场景迁移: SCENE_1: ground-level urban street, beige stone building, warm daylight; structure inherited, dressing re-lettered to MetaX
- 画内文字/logo: ['in-scene physical lettering reading MetaX on the bus-stop shelter panel']
- 后期叠加: [('label', 'neutralize_allowed')]
  - 节拍 `TU001_S1` 0.0-2.5s | refer=`visual_display` target=`opening_hook` | scene=SCENE_1 | ref_frame=['FRAME_SCENE1'] | status=`ready_with_assumptions` | missing=[]
  - 节拍 `TU001_S2` 2.5-4.0s | refer=`text_overlay_or_information_reveal` target=`information_release` | scene=SCENE_1 | ref_frame=['FRAME_SCENE1'] | status=`ready_with_assumptions` | missing=['MI004']

## TU002  4.0-8.0s (4.0s)  [ready_with_assumptions]
- 参考功能: `reveal` | 内容类型: `mixed`
- 生成画面: vertical MetaX fabric banner hanging on a tall building
- 生成动作/运镜: the banner hangs and then ripples in the wind; static locked-off camera; low angle, upward
- 场景迁移: SCENE_2: building exterior above street level, cloudy daylight; structure inherited, banner re-lettered to MetaX
- 画内文字/logo: ['in-scene physical lettering reading MetaX printed down the vertical fabric banner']
- 后期叠加: [('label', 'neutralize_allowed')]
  - 节拍 `TU002_S1` 4.0-6.5s | refer=`visual_display` target=`reveal` | scene=SCENE_2 | ref_frame=['FRAME_SCENE2'] | status=`ready_with_assumptions` | missing=[]
  - 节拍 `TU002_S2` 6.5-8.0s | refer=`action_or_interaction` target=`reveal` | scene=SCENE_2 | ref_frame=['FRAME_SCENE2'] | status=`ready_with_assumptions` | missing=[]

## TU003  8.0-12.0s (4.0s)  [ready_with_assumptions]
- 参考功能: `reveal` | 内容类型: `mixed`
- 生成画面: a small ginger-and-cream cat seated at the left of the rooftop
- 生成动作/运镜: the cat is revealed seated, lifts its head and looks to the right, then holds the posture; static locked-off camera; eye-level slightly below the letters
- 场景迁移: SCENE_3: open rooftop with a parapet and a lettering structure; structure inherited, letters re-lettered to MetaX and re-scaled for a small animal
- 画内文字/logo: ['in-scene physical three-dimensional lettering reading MetaX on the rooftop structure']
- 后期叠加: [('label', 'neutralize_allowed')]
  - 节拍 `TU003_S1` 8.0-10.0s | refer=`visual_display` target=`reveal` | scene=SCENE_3 | ref_frame=['FRAME_SCENE3'] | status=`ready_with_assumptions` | missing=['MI001']
  - 节拍 `TU003_S2` 10.0-12.0s | refer=`action_or_interaction` target=`reveal` | scene=SCENE_3 | ref_frame=['FRAME_SCENE3'] | status=`ready_with_assumptions` | missing=['MI001']

## TU004  12.0-15.0s (3.0s)  [ready_with_assumptions]
- 参考功能: `closing` | 内容类型: `mixed`
- 生成画面: extreme close-up of the cat's face wearing oversized red geometric sunglasses
- 生成动作/运镜: the head is held, then rotates slightly so the reflected lettering slides inside the lenses; static locked-off camera; motion comes from the head turn; eye-level, very close
- 场景迁移: rooftop extreme close-up; background soft, no scene entity of its own
- 画内文字/logo: ['in-scene physical lettering reading MetaX reflected inside the sunglass lenses']
- 后期叠加: [('label', 'neutralize_allowed')]
  - 节拍 `TU004_S1` 12.0-13.5s | refer=`visual_display` target=`closing` | scene=None | ref_frame=[] | status=`ready_with_assumptions` | missing=['MI001']
  - 节拍 `TU004_S2` 13.5-15.0s | refer=`action_or_interaction` target=`closing` | scene=None | ref_frame=[] | status=`ready_with_assumptions` | missing=['MI001']

## 参考帧摘要
- plan_required=True person_entity_count=0 scene_entity_count=3 planned_frame_count=3
- ready_frame_ids=['FRAME_SCENE1', 'FRAME_SCENE2', 'FRAME_SCENE3'] plan_path=07_reference_frame_plan/reference_frame_plan.json

## H3 打包与视频生成状态
- H3 packager input: `09_h3_package/h3_packager_input.md` (已写入)
- H3 packager prompt: `09_h3_package/minimax_h3_prompt.md` (六段式, 校验通过 image_count=3, issues=[])
- H3 request: `10_h3_video_output/request.json` (V2 URL-only, model=MiniMax-H3, duration=15, ratio=16:9)
- H3 视频生成: `dry_run_not_submitted` — 本次为 dry-run, 未提交、未运行 H3 视频生成 (10 阶段边界)
