# Pre-Generation Checklist

## 参考视频绑定
- [x] `参考视频` 绑定: `test_data/nail-6/nail-6.mp4` (12.6s, 1080x1920, full_video_reference; media_url 可用)。
- [x] 只参考范围: 构图/运镜/转场/动作机制/镜头顺序/时间节奏/空间关系/前后连续性/信息揭示结构。
- [x] 单一连续镜头: 全片 1 个 `timeline_unit` / 4 个 `temporal_segments`; 无剪辑、无转场。
- [x] `prompt_shots_from_temporal_segments`: prompt 中的 Beat 1-4 是单镜头内部节拍，不是参考级多镜头。

## 素材数量与上限
- [x] H3 图片参考数量 3/5 (ASSET_001, RF_PERSON_001, RF_SCENE_001); 视频参考 1。
- [x] 每张图片短边落在 640-900px: ASSET_001 768x768 (由商品原图 1639x1639 缩放), RF_PERSON_001 768x1024, RF_SCENE_001 768x1376。
- [x] 所有 `assets/` 文件存在且路径可用。

## 标签一致性
- [x] `<Picture 1>`/`<Picture 2>`/`<Picture 3>` 在 mapping 中均可找到。
- [x] `<Subject 1>`/`<Subject 2>`/`<Subject 3>` 均由对应 `<Picture N>` 定义。
- [x] `<Video 1>` 在 `content[]` 中为 `video_url`/`reference_video`。

## 素材绑定与显式替换
- [x] 显式替换绑定: 参考美甲图案 -> `<Subject 1>` (`ASSET_001`); 已出现在全部 4 个分镜句中(SEG4 以延续/回置绑定)。
- [x] 人物身份中性化: 使用非特定身份表演者, 不复现参考人物身份。
- [x] 场景适配且可见差异: 车内 -> 暗调室内(空间类型/主色调/背景结构均不同)。

## 声音与文字
- [x] 音乐行固定为 `音乐: 跟随参考视频音乐风格.`; 未推断歌词/音效/卡点/唱歌/声音情绪。
- [x] 画面无未确认可读文字/logo; 目标台词缺失, 仅保留口型与互动结构。
- [x] 无后期叠加项 (`post_overlay_plan=[]`), H3 生成 clean plate。

## 待处理问题
- [ ] 无阻塞项。`missing_inputs` `MI_001`(actor_identity)/`MI_002`(scene) 均为 `generate_with_confirmed_assumption`, 已在 `GA_002`/`GA_003` 中以生成假设处理。
- [ ] `h3_request.json` 已生成但**未提交** (dry-run 边界)。

## Prompt 结构
- [x] `minimax_h3_prompt.md` 六段式字段顺序: `subject_definitions` / `summary` / `retention_analysis` / `detailed_description` / `overall_soundscape` / `non_diegetic_music`。
- [x] `summary` 以 `[reference generation]` 开头。
- [x] 保真: 镜头结构、动作阶段、接触点、遮挡揭示、素材绑定均未丢失。
