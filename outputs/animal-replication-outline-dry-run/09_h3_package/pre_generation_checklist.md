# H3 生成前检查清单

## 参考视频绑定
- 参考视频路径: `test_data/animal/2_2_case4-H3-original.mp4`
- 服务地址: `http://10.42.1.1:30100/v1/assets/asset_6a7143e4263944d9b66003792c363b92/content`
- 绑定状态: `bound`（<=15s 完整参考视频，作为 `<Video 1>` motion/camera/timing 参考）
- 只参考: 构图/运镜/转场/动作机制/镜头顺序/时间节奏/空间关系/前后连续性/信息揭示结构

## 素材计数
- 参考视频: 1（video）
- 图片素材: 3（`picture 1` 角色参考帧、`picture 2` 场景参考帧、`picture 3` 用户主体照片）
- 图片上限: 5（满足）
- 图片短边: 768px（角色/场景帧 1376x768；`picture 3` 打包副本由 1242x1242 预处理降采样为 768x768），接近 720p（满足）
- 打包预处理: `assets/A001.jpeg` 为 server 可访问的 720p 级打包副本，原始用户素材保持不变

## 分镜计数
- reference-level 镜头数: 1（单一连续镜头，SC001）
- temporal_segment / prompt beat 数: 6（SEG001-SEG006）
- H3 prompt 中使用 `Beat N`，与会话说明一致：这些是同一镜头内部节拍，不是参考级镜头拆分

## 保真检查
- 动态点/转场/特殊运镜/特殊构图: 已写入（推近/跟拍 SEG003；横向→纵向叠站 SEG005-SEG006）
- 素材绑定: 每个分镜均绑定 `<参考视频>`、`<人物1>`、`<场景1>`、`<全局素材1>`
- 后期叠加: 无（`post_overlay_plan` 为空）；H3 输出 clean frame，不渲染任何文字/logo

## 缺失/阻塞
- 缺失输入: MI001（另外两只哈士奇按 GA001 生成）、MI002（场景以用户文本声明户外草坪）、MI003/MI004（后期叠加内容缺失，非阻塞）
- 阻塞项: 无
- 音乐/BGM/音效: `unsupported_skipped`，仅按固定行交接，不做音频分析

## 提交状态
- 视频生成: `not_submitted`（dry-run 边界：仅产出 request/package，未调用 H3 视频生成）
