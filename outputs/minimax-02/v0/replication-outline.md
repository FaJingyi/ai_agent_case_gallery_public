# 复刻大纲人工审阅稿

- schema: `common_replication_outline.v2`
- status: `ready_with_assumptions` / generation_scope: `single_generation_task`
- 目标视频: 3D 动漫风格的小镇清晨：先观察小镇清晨街景，再聚焦到街角卖花女孩与她的花摊
- 时长: 15.0s / 镜头数: 4 / 画幅: 16:9
- 风格来源: user_declared（3D anime render with dimensional geometry, volumetric morning light and physically coherent materials）
- 参考视频: 2560x1440 / 24fps / 前 15 秒截断；H3 素材白名单首项为参考视频输入
- 时间精度: 截断到小数点后一位（truncate）

## 目标与参考差异锚点
- 场景由城市高层街道改为小镇低层街道
- 风格由写实实拍改为 3D 动漫渲染
- 主体由标识载体与成年女性改为花摊与卖花女孩
- 主色由城市米白改为暖金 + 柔粉 + 花叶绿

## 强继承与参考继承概览

| 分类 | 数量 | 说明 |
| --- | --- | --- |
| strong_inheritance | 15 | 时间结构、镜头顺序、镜头语言、节奏、空间关系、特殊版式/转场、形式型记忆点 |
| reference_inheritance | 11 | 主体运动、姿态、动作语汇、道具操作、交互、场景内容、人物内容 |
| downgraded | 0 | 本轮无强继承项降级 |

## 时间轴审阅

### tu_001（SC001_SH001，0.0-4.5s，4.5s）

- 主体类型: `environment`；视角: 街道行人视角；机位/运镜: 静止机位；0.0-1.0s 焦点由虚到实，1.0-3.0s 极缓慢向前推近，机位与构图中心不变
- 构图: 建立镜头（中远景），主体横置画面视觉中心，左右均衡留白；前景石板路 / 中景街角花摊 / 后景低层民居与晨空，前中后景分层；主体信息落在双圆交叠区域，两侧孔径保留无字柔和留白
- 焦点/景深: 整体偏深焦，石板路与民居可辨；0.0s 瞬间整体偏软，1.0s 后主体与背景同时清晰
- 剪辑/转场: 3.5s 起画面沿对角方向分割并带旋转位移，进入约 1s 的对角旋转擦除
- 必须有: fixed two-aperture frame with black surround, centered flower stall, left-right symmetric negative space, warm low-sun long shadows

- **seg_001_1（0.0-3.5s，3.5s）** function=`visual_display`
  - 目标功能: 建立小镇清晨与花摊母题，并建立固定观看版式
  - 画面: 3D 动漫小镇清晨石板街道，街角木质花摊居中，暖金晨光与长影，画面落在固定双圆孔径内
  - 动作节拍: 0.0-1.0s 焦点由虚到实；1.0-3.0s 极缓慢推近；无人物动作（transfer_mode=`target_action_override`）
  - 全局引用: si_003, si_007, si_008, si_012, et_002, et_006, et_007, et_012
  - 特殊机制: sm_mask_001, sm_sym_001, sm_rack_001, sm_dolly_001
  - 参考帧需求: gp_001, gp_002（merged_reference）
  - 状态: ready
- **seg_001_2（3.5-4.5s，1.0s）** function=`transition`
  - 目标功能: 以对角旋转擦除把街景交给街角布幔仰拍
  - 画面: 街景沿对角边界带旋转退出，布幔仰拍画面进入，孔径保持不动
  - 动作节拍: 3.5s 开始分割，约 4.5s 完成交接（transfer_mode=`target_action_override`）
  - 全局引用: si_010, si_007, et_009
  - 特殊机制: sm_wipe_001, sm_mask_001
  - 参考帧需求: none（none）
  - 状态: ready

### tu_002（SC001_SH002，4.5-8.5s，4.0s）

- 主体类型: `environment`；视角: 街面仰视低层建筑上方；机位/运镜: 静止仰拍机位，无推拉摇移
- 构图: 全景，低角度仰拍，竖向布幔中部偏右，晨空填充孔径上缘；前景无遮挡 / 中景竖向布幔 / 后景低层民居与晨空
- 焦点/景深: 布幔清楚，远景晨空与屋檐略软
- 剪辑/转场: 7.5s 起画面沿对角方向分割，进入与前一过渡方向一致的对角旋转擦除
- 必须有: fixed two-aperture frame, low-angle vertical banner mid-right, sky filling the upper aperture edge

- **seg_002_1（4.5-7.5s，3.0s）** function=`visual_display`
  - 目标功能: 以低角度仰拍展示小镇街角竖向布幔与晨空，并延续固定观看版式
  - 画面: 3D 动漫小镇街角低角度仰拍，无字悬挂布幔位于画面中部偏右，晨空填充上缘，布幔在晨风中翻动，无人物
  - 动作节拍: 4.5-7.0s 布幔持续翻动；7.0-7.5s 收束并准备进入转场（transfer_mode=`target_action_override`）
  - 全局引用: si_002, si_004, si_007, si_015, et_003, et_006
  - 特殊机制: sm_mask_001
  - 参考帧需求: gp_002（scene_reference）
  - 状态: ready
- **seg_002_2（7.5-8.5s，1.0s）** function=`transition`
  - 目标功能: 以对角旋转擦除把街角布幔交给花摊中景
  - 画面: 布幔仰拍画面沿对角边界带旋转退出，花摊中景自另一侧进入，孔径保持不动
  - 动作节拍: 7.5s 开始分割，约 8.5s 完成交接（transfer_mode=`target_action_override`）
  - 全局引用: si_010, si_007, et_010
  - 特殊机制: sm_wipe_002, sm_mask_001
  - 参考帧需求: gp_002（scene_reference）
  - 状态: ready

### tu_003（SC001_SH003，8.5-11.5s，3.0s）

- 主体类型: `human`；视角: 观察者侧前方视角；机位/运镜: 基本静止中景，无推拉摇移
- 构图: 中景（腰部以上至大腿），人物偏画面左侧，右侧由花箱与街景构成平衡；前景无遮挡 / 中景女孩与花摊 / 后景低层民居轻微虚化
- 焦点/景深: 女孩清楚，远景民居轻微虚化
- 剪辑/转场: 结尾 11.5s 无过渡帧直接硬切到面部特写
- 必须有: fixed two-aperture frame, medium shot, girl placed left of center, flower crates filling the right, wide-brim straw hat

- **seg_003_1（8.5-9.0s，0.5s）** function=`visual_display`
  - 目标功能: 以中景与偏左构图建立卖花女孩在花摊前的存在
  - 画面: 3D 动漫卖花女孩站在花摊木箱旁，中景，人物偏画面左侧，头部微低看向花朵；右侧由花箱与街景平衡
  - 动作节拍: 8.5-9.0s 女孩静止站立，头部微低，尚未起步（transfer_mode=`beat_structure_only`）
  - 全局引用: si_002, si_005, si_007, si_009, si_015, et_004, et_006, et_008, et_014
  - 特殊机制: sm_mask_001, sm_offset_001
  - 参考帧需求: gp_001, gp_002（merged_reference）
  - 状态: ready
- **seg_003_2（9.0-11.5s，2.5s）** function=`action_or_interaction`
  - 目标功能: 卖花女孩在花箱间慢走并轻托花篮，结束于硬切边界
  - 画面: 女孩在花摊木箱间缓慢行走，双手轻托花篮，头部微低；11.5s 直接硬切到面部特写
  - 动作节拍: 9.0-11.0s 缓慢行走、重心转移、身体轻微起伏；11.0-11.5s 收束停在硬切边界（transfer_mode=`beat_structure_only`）
  - 全局引用: si_005, si_007, si_009, si_011, et_004, et_008, et_011, et_014
  - 特殊机制: sm_mask_001, sm_offset_001, sm_cut_001
  - 参考帧需求: gp_001, gp_002（merged_reference）
  - 状态: ready

### tu_004（SC001_SH004，11.5-15.0s，3.5s）

- 主体类型: `human`；视角: 近距离正面观察视角；机位/运镜: 基本静止特写，无推拉摇移
- 构图: 近景/特写，面部偏画面右侧，左侧由抬起的手与虚化花影填充；前景花瓣柔影 / 中景面部与草帽 / 后景明显虚化的花摊与街景
- 焦点/景深: 浅景深，面部与草帽锐利，背景明显虚化
- 剪辑/转场: 由 11.5s 直接硬切进入，切点两侧同场景同光线；段内无剪辑点，为同一特写镜头的状态延续
- 必须有: fixed two-aperture frame, close-up face offset right, wide-brim straw hat with warm band and flower, shallow depth of field

- **seg_004_1（11.5-13.0s，1.5s）** function=`visual_display`
  - 目标功能: 硬切进入卖花女孩面部特写，建立偏右构图与浅景深
  - 画面: 卖花女孩面部近景/特写，面部偏画面右侧，宽檐草帽与暖色帽带可见，浅景深背景虚化，前景花瓣柔影
  - 动作节拍: 11.5s 直接硬切进入；11.5-13.0s 面部静止，目光微垂，背景保持虚化（transfer_mode=`beat_structure_only`）
  - 全局引用: si_006, si_007, si_009, si_011, si_015, et_005, et_006, et_008, et_011
  - 特殊机制: sm_mask_001, sm_offset_001, sm_cut_001
  - 参考帧需求: gp_001, gp_002（merged_reference）
  - 状态: ready
- **seg_004_2（13.0-14.0s，1.0s）** function=`action_or_interaction`
  - 目标功能: 女孩右手自画面左侧进入，轻推草帽帽檐与帽带花朵后短暂保持，头部向另一侧轻倾
  - 画面: 女孩右手自画面左侧进入，指尖轻推草帽帽檐与帽带上的花朵后短暂保持贴合，同期头部向另一侧轻微倾斜
  - 动作节拍: 13.0-13.4s 手自左侧进入；13.4-13.7s 指尖接触并小幅推扶；13.7-14.0s 短暂保持贴合，头部向另一侧轻倾（transfer_mode=`beat_structure_only`）
  - 全局引用: si_007, si_009, et_005, et_008, et_013
  - 特殊机制: sm_mask_001, sm_offset_001, sm_micro_001
  - 参考帧需求: gp_001（person_reference）
  - 状态: ready
- **seg_004_3（14.0-15.0s，1.0s）** function=`closing_or_prompt`
  - 目标功能: 以花瓣虚化与晨光细节回收“清晨花朵”母题并静止收束
  - 画面: 女孩面部边缘与前景花瓣虚化交叠，晨光穿过花瓣形成柔和高光，回收“清晨花朵”母题；无旁白、无文字、无口型
  - 动作节拍: 14.0-15.0s 画面几乎静止，仅花瓣与散景极轻微浮动，缓慢收束（transfer_mode=`target_action_override`）
  - 全局引用: si_007, si_015, et_005, et_006
  - 特殊机制: sm_mask_001, sm_offset_001
  - 参考帧需求: gp_001, gp_002（merged_reference）
  - 状态: ready

## 文字与旁白策略
- speech_status: `no_confirmed_speech`
- 源侧文本槽位: 11 个（全部移除/审计，不进入目标 prompt）
- 目标侧文本项: 0 个
- 说明: source voiceover slot is a channel-transition sentence; every source screen_text slot is source branding/overlay, so no target dialogue, voiceover or screen text is generated

## 记忆点迁移

| memory_id | 类型 | 保留机制 | 目标绑定 | 状态 |
| --- | --- | --- | --- | --- |
| vm_001 | composition | 两个水平相交的圆形孔径 + 黑色外围；框架几何与位置全片不变；主体信息始终落在孔径内 | target_video, tu_001, tu_002, tu_003, tu_004 | active |
| vm_002 | composition | 开口镜头的左右对称与中心放置；主体横置居中且周围留白 | tu_001, seg_001_1 | active |
| vm_003 | transition | 对角分割式擦除边界；旧场景旋转位移退出、新场景自对侧进入；约 1s 时长；过渡期间遮罩不动 | tu_001, seg_001_2 | active |
| vm_004 | transition | 与前一过渡方向一致的对角擦除；中间态两场景同时可见；约 1s 时长 | tu_002, seg_002_2 | active |
| vm_005 | transition | 无过渡帧的直接硬切；景别由中景阶跃到特写形成尺度反差；切点两侧同场景同光线 | tu_003, tu_004, seg_003_2, seg_004_1 | active |
| vm_006 | camera_motion | 开场约 1s 由虚到实的焦点变化；变化期间机位与构图保持不动 | tu_001, seg_001_1 | active |
| vm_007 | composition | 明显偏置而非居中；偏置一侧由环境或手部动作填充；两镜偏置方向相对 | tu_003, tu_004, seg_003_1, seg_003_2, seg_004_1, seg_004_2 | active |
| vm_008 | micro_action | 手自画面左侧进入；指尖接触目标物后小幅推扶；短暂保持贴合；同期头部向另一侧轻倾 | tu_004, seg_004_2 | active |
| sm_001 | opening_hook | 开场不做铺垫，直接把主线语汇放在画面中心的环境载体上；开场同时建立固定的观看版式 | tu_001, seg_001_1 | active |
| sm_002 | information_release_sequence | 环境 → 建筑/空间 → 人物 → 细节回收的四层信息释放顺序；每层只更换承载载体；最后一层用细节方式回收主线语汇 | target_video, tu_001, tu_002, tu_003, tu_004 | active |
| sm_003 | emotional_arc | 由远及近的观察距离推进；克制平静、不制造强情绪转折的基调 | tu_002, tu_003, tu_004 | active |
| sm_004 | closing_cta | 结尾停在最靠近主体的细节层；用收束方式结束 | tu_004, seg_004_3 | adapted_without_speech |

## 全局外观库（第二层去重）

| entity_id | 名称 | 类型 | 参考帧需求 | 引用分镜 |
| --- | --- | --- | --- | --- |
| gp_001 | 3D 动漫卖花女孩 | person_appearance | required_visual_anchor | seg_003_1, seg_003_2, seg_004_1, seg_004_2, seg_004_3 |
| gp_002 | 小镇清晨街道与街角花摊 | scene_appearance | required_visual_anchor | seg_001_1, seg_002_1, seg_002_2, seg_003_1, seg_003_2, seg_004_1, seg_004_3 |
| gp_003 | 3D 动漫暖调清晨氛围 | style_atmosphere | style_atmosphere_not_a_frame_entity | seg_001_1, seg_002_1, seg_003_1, seg_004_1 |

## 参考帧摘要
- plan_required: `True` / summary_status: `ready` / frame_requirement_level: `required_visual_anchor`
- 人物实体: 1 / 场景实体: 1 / 状态帧: 0 / 计划帧: 2 / H3 图片预算: 8
- 触发规则: person_reference_entity_present, scene_reference_entity_present
- plan_path: `07_reference_frame_plan/reference_frame_plan.json`

## 准备度与缺口
- overall_status: `ready_with_assumptions` / blocking_item_ids: []
- missing_input_ids: mi_001, mi_002, mi_003, mi_004
  - mi_001 `target_visible_text_logo` → neutralize_allowed（omit_or_neutralize）
  - mi_002 `target_dialogue_or_voiceover_text` → neutralize_allowed（omit_or_neutralize）
  - mi_003 `actor_asset_image` → missing_generate_fallback（generate_with_confirmed_assumption）
  - mi_004 `scene_reference_image` → missing_generate_fallback（generate_with_confirmed_assumption）

## 审计项与约束
- text_logo_policy: 画内文字仅在用户确认时生成；后期叠加由 ffmpeg/opencv 承载；不生成未确认可读文字
- negative_constraint_policy: 源侧品牌字样、源人物身份、源旁白只作为 `audit_only` 约束
- unsupported_audio: `unsupported_skipped`（music_bgm_sfx, sound_emotion, beat_sync, singing）

## 校验标记
- outline_rebuilt_from_archived_reference_analysis
- reference_video_duration_exceeds_15s_using_first_15s_excerpt
- no_user_target_assets_provided
- target_visible_text_not_provided
- target_dialogue_or_voiceover_text_not_provided
- reference_profiles_script_directory_empty
- strong_inheritance_preserved_with_no_downgrades
