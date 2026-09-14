# Reference Mapping

最多 5 张参考图（Ref2VA 硬约束）。图片顺序与 `minimax_h3_prompt.md` 中 `<Picture N>` 一致。

| Label | File | Role | Segment | Purpose |
| --- | --- | --- | --- | --- |
| picture 1 | assets/user_asset_001_product.jpg | `<Subject 1>` 商品主体权威图 | 全部分镜 | 保持东方树叶 500ml 瓶型/瓶盖/茶汤颜色/标签版式，产品在每镜可见 |
| picture 2 | assets/person_001.png | `<Subject 2>` 人物外观锚点 | 全部分镜 | 目标人物一致外观（不可识别表演者），非参考片人物 |
| picture 3 | assets/scene_001.png | `<Subject 3>` 场景参考 | 分镜 1-2 | 明亮居家客厅，开场场景外观锚点 |
| picture 4 | assets/scene_005.png | `<Subject 4>` 场景参考 | 分镜 6、8 | 现代健身工作室，蒙太奇中段场景外观锚点 |
| picture 5 | assets/scene_007.png | `<Subject 5>` 场景参考 | 分镜 10-11 | 现代简约室内，结尾饮用与收束场景外观锚点 |

## 视频参考

| Label | File | Role | Segment | Purpose |
| --- | --- | --- | --- | --- |
| `<Video 1>` | http://10.42.1.1:30100/v1/assets/asset_555aee1bcb974186839d6bf436619f3c/content | 运动/运镜/时序结构参考 | 全部分镜 | 只提供构图/运镜/转场/动作机制/镜头顺序/时间节奏/空间关系/前后连续性/信息揭示结构 |

## 未映射的已生成参考帧（超出 5 图上限，写文本描述，不进 mapping）

以下 Step 8 生成帧已质检通过并保存在 `08_reference_frames/`，但 Ref2VA 一次最多 5 张参考图，未进入本次 mapping，其场景外观在 `minimax_h3_prompt.md` 与 `h3_packager_input.md` 中以文本描述承接：

- 场景2 街角现代茶饮店：`assets/scene_002.png`（分镜 3）
- 场景3 现代商场中庭：`assets/scene_003.png`（分镜 4、7）
- 场景4 城市户外绿荫步道：`assets/scene_004.png`（分镜 5）
- 场景6 现代城市广场：`assets/scene_006.png`（分镜 9）
