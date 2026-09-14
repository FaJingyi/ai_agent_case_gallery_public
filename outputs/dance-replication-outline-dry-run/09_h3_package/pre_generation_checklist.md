# H3 生成前检查清单（Step 9）

## 参考视频绑定

- [x] `参考视频` 行置顶, 并包含可访问 URL。
- [x] 只参考范围限定为构图/运镜/转场/动作机制/镜头顺序/时间节奏/空间关系/前后连续性/信息揭示结构。
- [x] `音乐: 跟随参考视频音乐风格.` 已写入, 未推导歌词/音效/卡点/唱歌/声音情绪。

## 素材计数

- [x] H3 输入素材共 3 项：1 个参考视频 + 2 张生成参考帧（人物1、场景1）。
- [x] 用户素材为 0（`user_assets: none`）。
- [x] 生成参考帧均通过提交前质检且 `generation_status=succeeded`, 已纳入 `03_asset_inventory/h3_input_asset_inventory.json.eligible_h3_input_assets[]`。
- [x] 参考帧数量未超过 5 张上限。
- [x] 包内图片副本已复制到 `09_h3_package/assets/`。
- [x] 包内参考帧已按 H3 参考图尺寸建议从 1536 短边预处理为 768 短边（768x1360），主图仍保留在 `08_reference_frames/`。

## 分镜计数

- [x] 参考级镜头数（timeline_units）：1（单镜头连续）。
- [x] 内部节拍数（temporal_segments）：5（0-1s, 1-2s, 2-4s, 4-7s, 7-10.1s）。
- [x] 分镜 handoff 行数：5，与 temporal_segments 一一对应；这些是 prompt-level beats，不是新增/拆分参考镜头。
- [x] 每个分镜句子均以 <人物1> 为可见主体、以 <场景1> 为可见场景，并包含动作/构图/运镜/连贯性/素材绑定。

## 文字与叠加

- [x] `post_overlay_plan` 为空, H3 生成 clean plate, 不渲染文字层。
- [x] `in_scene_text_logo_plan` 为空, 不生成可读文字/logo/品牌标识。

## 缺失/阻塞项

- 缺失输入：`mi_001 actor_identity`（生成回退, 不阻塞）、`mi_002 post_overlay_text`（省略/中性化, 不阻塞）。
- 阻塞项：无。

## 待处理

- [ ] 步骤 10：提交 H3 请求（本次 dry-run 未提交）。

## Packager（Ref2VA）校验

- [x] `minimax_h3_prompt.md` 正文只包含固定 6 字段：`subject_definitions` / `summary` / `retention_analysis` / `detailed_description` / `overall_soundscape` / `non_diegetic_music`。
- [x] `summary` 以 `[reference generation]` 开头。
- [x] `[Shot 1]` 无时间戳，后续 shot 时间严格递增（00:01.000 / 00:02.000 / 00:04.000 / 00:07.000），覆盖 0-10.1s。
- [x] `[Shot 1]-[Shot 5]` 与上游 5 个 `temporal_segments` 一一对应；这些是 prompt-level beats，不是新增/拆分参考镜头。
- [x] 单镜头连续结构已在 prompt 中声明 `single continuous shot, no cuts and no transitions`。
- [x] `detailed_description` 中 <Subject 1>/<Subject 2>/<Subject 3> 首次出现均带可见细节；后续复用标签。
- [x] `picture n` 映射：`picture 1` = `assets/rf_person_001.png`，`picture 2` = `assets/rf_scene_001.png`；prompt 中 `<Picture N>` 均可映射。
- [x] 参考图数量 2 ≤ 5；两张参考图短边 768px，落在 640-900px 建议区间。
- [x] 未新增文字/字幕/价格/联系方式/商业声明；画面保持 clean、unbranded。
- [x] prompt 长度约 5.0k 字符，未接近 7k 上限。
- [x] 上游 `special_mechanism_transfer[]` 为空，无特殊构图/运镜/转场机制需要保留；固定机位未被泛化。
- [x] 声音字段：`overall_soundscape: N/A`、`non_diegetic_music: N/A`；音乐/音效/唱歌按 `unsupported_skipped` 不复刻。
