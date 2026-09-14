# H3 生成前校验清单

## 参考视频绑定

- 状态: 已绑定.
- 参考视频 URL: http://10.42.1.1:30100/v1/assets/asset_5811419d16594adfbf8cca2096cbde3c/content
- 包内副本: assets/reference_video_first15s.mp4 (源视频 15.083s, 使用前 15.0s 截断版本, 满足 <=15s 策略).
- 只参考范围: 构图/运镜/转场/动作机制/镜头顺序/时间节奏/空间关系/前后连续性/信息揭示结构.

## 素材计数

- H3 输入白名单素材总数: 4 (参考视频 1 + 生成参考帧 3).
- 参考图数量: 3 / 上限 5, 未超限.
- 参考图尺寸: 每张 1376x768 (16:9, 短边 768, 接近 720p 级别).
- 人物参考帧: 0 (无人物实体; 模特已替换为猫, 猫为 main_subject 不入人物参考帧).
- 场景参考帧: 3 (SCENE_1 / SCENE_2 / SCENE_3).
- 无图片素材实体: 全局素材1 (猫), 全局素材2 (MetaX 字母), 全局素材3 (红色墨镜) —— 均为生成假设/用户文字, 无可用图片, 已在全局素材段标记 图片路径无.

## 分镜计数

- 参考级镜头 (timeline_units): 4.
- 内部节拍 (temporal_segments): 8.
- handoff 分镜句: 4 (分镜1-4, 顺序与时间轴 0-4s / 4-8s / 8-12s / 12-15s 一致).
- 说明: packager 若为模型可读性把 8 个 temporal_segments 标为 `[Shot N]`, 那些是 prompt-level shots, 不是 reference-level shots.

## 显式替换覆盖

- 替换 REP001: 所有 "minimax" 字母 -> "MetaX"; 分镜1-4 均出现 MetaX 可见.
- 替换 REP002: 模特 (女性) -> 猫; 分镜3、分镜4 句中出现猫作为可见主体.
- 特殊机制: M001 双圆孔遮罩几何、M002 三处硬切 prompt_sentence 已逐分镜写入 handoff.

## 缺失 / 阻塞项

- 阻塞项: 无 (`05_replication_readiness/replication_readiness_check.json` overall=ready_with_assumptions).
- 缺口 (非阻塞): 无猫图、无 MetaX logo 资产、无场景覆盖说明; 均以生成假设/用户文字进入 H3 prompt.
- 待处理: 参考视频边缘等宽 UI 文案未确认 -> 生成 clean plate, 由后期叠加中性红层, 不在 H3 视频内渲染可读 UI 文案.

## 结论

- 素材路径、标签、分镜和时间轴一致; H3 request 可进入生成阶段, 但本次运行为 dry-run, 不提交 H3 视频生成.
