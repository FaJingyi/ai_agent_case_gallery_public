# 复刻大纲审阅稿（common-video-replication-outline / shot_structure）

- schema_version: `common_replication_outline.v2`
- status: `ready_with_assumptions`
- replication_mode: `shot_structure`
- generation_scope: `single_generation_task`
- 时间精度: `one_decimal` / `truncate`
- 参考视频: 720x1280, 15.6s, 使用时间范围 0.0-15.0s
- 目标视频时长: 15.0s, 画幅 9:16
- timeline_unit 数（参考 shot 数）: 4
- temporal_segment 数: 10
- 参考帧: person=1, scene=3, planned=4, plan=07_reference_frame_plan/reference_frame_plan.json

## 参考元素处理决策

| element_id | element_type | decision | source_ref |
| --- | --- | --- | --- |
| ret_001 | time_structure | inherit | `reference_video_analysis.json.scenes[0].shots[] + script_construction_context.beats[]` |
| ret_002 | shot_structure | inherit | `reference_video_analysis.json.video_prompt_source.shot_timeline[].static/spatial_framing` |
| ret_003 | composition | inherit | `reference_video_analysis.json.video_prompt_source.special_mechanisms[type=picture-in-picture]` |
| ret_004 | transition | inherit | `reference_video_analysis.json.video_prompt_source.special_mechanisms[type=foreground-wipe]` |
| ret_005 | action_structure | inherit | `reference_video_analysis.json.memory_points.visual[memory_id=vm_003]` |
| ret_006 | camera | inherit | `reference_video_analysis.json.scenes[0].video_generation.camera` |
| ret_007 | subject_content | adapt | `reference_video_analysis.json.video_prompt_source.shot_timeline[].static（甲面描述）+ 04_target_asset_analysis.user_text_context_analysis.normalized.explicit_replacement_target` |
| ret_008 | person_or_body | adapt | `reference_video_analysis.json.video_prompt_source.shot_timeline[].static（人物描述）` |
| ret_009 | scene_content | adapt | `reference_video_analysis.json.scenes[0].video_generation.scene ＋ video_prompt_source.state_relation_summary[].observed_changes` |
| ret_010 | prop | adapt | `reference_video_analysis.json.video_prompt_source.shot_timeline[shot_id=shot2/shot3].static` |
| ret_011 | prop | adapt | `reference_video_analysis.json.video_prompt_source.shot_timeline[shot_id=shot4].static` |
| ret_012 | text_or_ui | adapt | `reference_video_analysis.json.scenes[0].shots[].script_generation.text_slots ＋ script_construction_context.beats[]` |
| ret_013 | dialogue_or_voiceover | discard | `reference_video_analysis.json.scenes[0].shots[].script_generation.event ＋ memory_points.script[]` |
| ret_014 | unsupported_audio | discard | `05_script_analysis/asr_alignment.json.segment_alignment[].shots[].usable_as_dialogue` |
| ret_015 | incidental_detail | discard | `reference_video_analysis.json.scenes[0].video_generation.scene.background_elements` |

### 显式替换绑定
- source_entity: 参考视频手指甲表面的美甲图案
- target_entity: <全局素材1>，素材图片中的穿戴甲图案：长尖形/杏仁尖甲片，黑与深棕/灰褐为主色，白色与银色金属质感纹理，立体珍珠与金边珍珠，立体眼睛图案（棕与黄绿虹膜），滴落状黑胶，亮面凝胶高光
- target_asset_ids: A001
- affected_source_ids: VS001:shot1, VS001:shot2, VS001:shot3, VS001:shot4
- segment 级覆盖数: 10, 未覆盖: 无
- 源实体泄漏到 prompt 字段: `False`, 结论: `passed`

## 全局外观实体（第二层 pass 去重结果）

| entity_id | 名称 | entity_type | 素材名 | merge_status |
| --- | --- | --- | --- | --- |
| E001 | 目标甲面图案（穿戴甲设计） | main_subject_appearance | <全局素材1> | merged_single_entity |
| E002 | 目标人物（不可识别身份的女性表演者） | person_appearance | <人物1> | merged_single_entity |
| E003 | 场景1 室内暗调空间 | scene_appearance | <场景1> | merged_single_entity |
| E004 | 场景2 户外暗色草地与静水 | scene_appearance | <场景2> | merged_single_entity |
| E005 | 场景3 户外暗色坡地与金属格构结构 | scene_appearance | <场景3> | merged_single_entity |
| E006 | 深色花材道具 | key_prop_appearance | <全局素材2> | merged_single_entity |
| E007 | 画中画内的深色金属小物 | key_prop_appearance | 图内描述（不单独作为全局素材） | merged_single_entity |
| E008 | 暗黑哥特亮面质感氛围 | style_atmosphere | 全片氛围 | merged_single_entity |

## 场景迁移

| transfer_id | 类型 | 目标实体 | 可见差异 |
| --- | --- | --- | --- |
| st_001 | preserve_scene_style | - | - |
| st_002 | adapt_scene_content | E003 | 主色由米色/白色高亮墙面改为近黑深灰; 光照由均匀顶光改为单一侧向低照度硬光; 背景物由门框与通风口改为暗色布帘与深色金属边框 |
| st_003 | adapt_scene_content | E004 | 天空由蓝天白云改为厚重阴云; 湖面由明亮高反射改为深色低反射静水; 草地由明亮绿改为暗绿近黑; 由清亮冷调日光改为低明度阴天散射光 |
| st_004 | adapt_scene_content | E005 | 坡地由明亮绿地改为暗色岩土与暗草坡; 格构结构由浅色金属改为深色氧化金属; 天光由直射日光改为阴云散射光 |

## 记忆点迁移

| memory_id | type | 保留机制 | 绑定 |
| --- | --- | --- | --- |
| vm_001 | composition | 主画面与子画面同时可见的多层版式; 子画面固定在画面左上角及其相对尺寸关系; 主画面保持手部特写与浅景深背景 | VS001_seg7, VS001_shot3 |
| vm_002 | transition | 前景手部贴近镜头遮挡画面的边界形态; 前后镜头都以手部为主体的动作承接 | VS001_seg3, VS001_shot1, VS001_shot2 |
| vm_003 | micro_action | 抬手展示甲面的动作顺序; 手指张开与手掌朝向镜头的关键姿态; 手靠近面部/镜头的尺度变化; 夹持小物与触碰帽檐的接触点 | VS001_shot1, VS001_shot2, VS001_shot3, VS001_shot4 |
| sm_001 | opening_hook | 开场先用第一人称文案建立情境; 把前置状态放在最前面作为对比前提 | VS001_seg1, VS001_seg2, mi_001 |
| sm_002 | information_release_sequence | 做之前→做之后→细节→搭配的信息释放顺序; 每个阶段只增加一层新信息 | VS001_shot1, VS001_shot2, VS001_shot3, VS001_shot4 |
| sm_003 | comparison_contrast | 用相同展示动作承接前后两种甲面状态; 在边界处完成状态切换 | VS001_seg2, VS001_seg3, VS001_seg4 |

## 特殊机制迁移

| mechanism_id | type | where | confidence | handoff | loss_risk | segments |
| --- | --- | --- | --- | --- | --- | --- |
| M001_foreground_wipe | special_transition | ['VS001_seg3'] | - | downstream_prompt | - | VS001_seg3 |
| M002_picture_in_picture | special_composition | ['VS001_seg7'] | - | downstream_prompt | - | VS001_seg7 |
| M003_nail_display_gesture_chain | micro_action | ['VS001_seg1', 'VS001_seg2', 'VS001_seg3', 'VS001_seg4', 'VS001_seg5', 'VS001_seg6', 'VS001_seg7', 'VS001_seg8', 'VS001_seg9', 'VS001_seg10'] | - | downstream_prompt | - | VS001_seg1, VS001_seg2, VS001_seg3, VS001_seg4, VS001_seg5, VS001_seg6, VS001_seg7, VS001_seg8, VS001_seg9, VS001_seg10 |

## 时间轴

### VS001_shot1  0.0-3.5s  （function: opening_hook）

- 参考镜头: `VS001:shot1`
- 生成画面: 室内中景到双手特写，先建立前置状态并把双手推向镜头，用前景遮挡触发转场
- 必须可见: <人物1>; <全局素材1> 目标穿戴甲设计; <场景1>（室内暗调空间，深灰近黑哑光墙面与暗色布帘，保留一侧门框/镜框作竖向边界，单一侧向低照度硬光，低明度冷色偏移）
- 使用素材: `reference_video_excerpt`(motion_camera_timing_reference), `A001`(nail_pattern_source_and_style_reference), `RF001`(person_reference), `RF002`(scene_reference)
- 参考帧决策: RF001, RF002 (entity: E002, E003)
- 后期叠加: O001
- 缺失项: mi_001 / 生成假设: asm_002, asm_003, asm_005

#### VS001_seg1  0.0-1.0s (1.0s)

- 参考功能 / 目标功能: `visual_display` / `visual_display`
- 生成画面（主体）: <人物1> 与双手（甲面呈基础凝胶基底状态）
- 动作/运镜: 叉腰→放下→准备抬手的起始阶段；基本静止的手持镜头，极慢运动，轻微手持晃动
- 构图/景别: 中景，主体居中偏下，双手位于画面下缘信息区; 平视机位，9:16 竖屏，主体与手部集中在中下区域
- 场景迁移: [E003] <场景1>（室内暗调空间，深灰近黑哑光墙面与暗色布帘，保留一侧门框/镜框作竖向边界，单一侧向低照度硬光，低明度冷色偏移）
- 甲面可见状态: 目标穿戴甲的基础凝胶基底状态（<全局素材1> 的黑色与深棕亮面基底，带银色金属细线纹理，不含立体珍珠与立体眼睛装饰）
- 画面文字: 开场画面文字层占位（文案缺失），保留顶部出现位置与时间节拍
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: O001(caption, missing_required_input, 顶部居中安全区)
- 参考帧: RF001, RF002
- 特殊机制: M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: 无 / mi_001
- status: `ready_with_assumptions`

#### VS001_seg2  1.0-2.5s (1.5s)

- 参考功能 / 目标功能: `action_or_interaction` / `action_or_interaction`
- 生成画面（主体）: <人物1> 抬起的双手（甲面朝向镜头）
- 动作/运镜: 抬起左手→抬起双手→手指张开→把甲面朝向镜头；基本静止的手持镜头，轻微晃动
- 构图/景别: 中景过渡到双手特写，双手进入画面中央信息区; 平视，浅景深开始分离手部与背景
- 场景迁移: [E003] <场景1>（室内暗调空间，深灰近黑哑光墙面与暗色布帘，保留一侧门框/镜框作竖向边界，单一侧向低照度硬光，低明度冷色偏移）
- 甲面可见状态: 目标穿戴甲的基础凝胶基底状态（<全局素材1> 的黑色与深棕亮面基底，带银色金属细线纹理，不含立体珍珠与立体眼睛装饰）
- 画面文字: 无画面文字变化
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: 无
- 参考帧: RF001, RF002
- 特殊机制: M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: 无 / 无
- status: `ready_with_assumptions`

#### VS001_seg3  2.5-3.5s (1.0s)

- 参考功能 / 目标功能: `transition` / `transition`
- 生成画面（主体）: 双手快速贴近镜头形成的运动模糊遮挡层
- 动作/运镜: 双手持续靠近镜头→出现明显运动模糊→几乎填满画面→在遮挡边界处切出；镜头基本静止，主体快速向镜头推进形成运动模糊
- 构图/景别: 双手特写逐步填满画面，主体占据画面绝大部分面积; 平视，镜头静止，靠主体靠近镜头放大
- 场景迁移: [E003] <场景1>（室内暗调空间，深灰近黑哑光墙面与暗色布帘，保留一侧门框/镜框作竖向边界，单一侧向低照度硬光，低明度冷色偏移）
- 甲面可见状态: 目标穿戴甲的基础凝胶基底状态（<全局素材1> 的黑色与深棕亮面基底，带银色金属细线纹理，不含立体珍珠与立体眼睛装饰）
- 画面文字: 顶部文字层在镜头结束时淡出（文案缺失）
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: 无
- 参考帧: RF001, RF002
- 特殊机制: M001_foreground_wipe[special_transition]; M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: composition_conflict:nc_keep_occlusion_boundary / 无
- status: `ready_with_assumptions`

### VS001_shot2  3.5-9.0s  （function: reveal_and_proof）

- 参考镜头: `VS001:shot2`
- 生成画面: 户外中近景，揭开完整的目标甲面设计并给出名称信息，随后用靠近面部与夹持动作补充展示
- 必须可见: <人物1>; <全局素材1> 目标穿戴甲设计; <场景2>（户外暗色草地与静水，前中后景层次保留，水面低反射深色静水，天空厚重阴云，冷色低明度散射光，轻微薄雾）
- 使用素材: `reference_video_excerpt`(motion_camera_timing_reference), `A001`(nail_pattern_source_and_style_reference), `RF001`(person_reference), `RF003`(scene_reference)
- 参考帧决策: RF001, RF003 (entity: E002, E004)
- 后期叠加: O002
- 缺失项: mi_001 / 生成假设: asm_002, asm_003, asm_004, asm_005

#### VS001_seg4  3.5-5.5s (2.0s)

- 参考功能 / 目标功能: `visual_display` / `visual_display`
- 生成画面（主体）: <人物1> 在 <场景2> 中抬起的双手（呈现完整目标穿戴甲设计）
- 动作/运镜: 双手抬起→多角度展示甲面→手掌转向镜头；基本静止的手持镜头，轻微晃动
- 构图/景别: 中近景，主体居中，双手进入画面上部; 平视机位，浅景深使背景草地与水面柔和虚化
- 场景迁移: [E004] <场景2>（户外暗色草地与静水，前中后景层次保留，水面低反射深色静水，天空厚重阴云，冷色低明度散射光，轻微薄雾）
- 甲面可见状态: 完整的<全局素材1>：黑与深棕基底、银色金属纹理、立体珍珠与金边珍珠、立体眼睛图案（棕与黄绿虹膜）、滴落状黑胶
- 画面文字: 无画面文字变化（名称标签自 5.5s 起出现，位于下一 segment）
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: 无
- 参考帧: RF001, RF003
- 特殊机制: M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: 无 / 无
- status: `ready_with_assumptions`

#### VS001_seg5  5.5-7.0s (1.5s)

- 参考功能 / 目标功能: `text_overlay_or_information_reveal` / `text_overlay_or_information_reveal`
- 生成画面（主体）: <人物1> 手部靠近面部、部分遮挡面部的手势
- 动作/运镜: 双手抬起后靠近面部→部分遮挡面部；基本静止的手持镜头，轻微晃动
- 构图/景别: 中近景，面部与手部同为信息区; 平视机位，浅景深
- 场景迁移: [E004] <场景2>（户外暗色草地与静水，前中后景层次保留，水面低反射深色静水，天空厚重阴云，冷色低明度散射光，轻微薄雾）
- 甲面可见状态: 完整的<全局素材1>：黑与深棕基底、银色金属纹理、立体珍珠与金边珍珠、立体眼睛图案（棕与黄绿虹膜）、滴落状黑胶
- 画面文字: 顶部标签层占位（文案缺失），保留 5.5s 出现时间与顶部位置
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: O002(label, missing_required_input, 顶部居中安全区)
- 参考帧: RF001, RF003
- 特殊机制: M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: unconfirmed_text_logo:nc_no_invented_readable_text / mi_001
- status: `ready_with_assumptions`

#### VS001_seg6  7.0-9.0s (2.0s)

- 参考功能 / 目标功能: `action_or_interaction` / `action_or_interaction`
- 生成画面（主体）: <人物1> 口中叼深色花材、双手再次抬起展示甲面
- 动作/运镜: 侧脸→双手再次抬起展示甲面→口部叼住深色花材；基本静止的手持镜头，轻微晃动
- 构图/景别: 中近景，面部与手部同为信息区; 平视机位，浅景深
- 场景迁移: [E004] <场景2>（户外暗色草地与静水，前中后景层次保留，水面低反射深色静水，天空厚重阴云，冷色低明度散射光，轻微薄雾）
- 甲面可见状态: 完整的<全局素材1>：黑与深棕基底、银色金属纹理、立体珍珠与金边珍珠、立体眼睛图案（棕与黄绿虹膜）、滴落状黑胶
- 画面文字: 无画面文字变化
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: 无
- 参考帧: RF001, RF003
- 特殊机制: M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: 无 / 无
- status: `ready_with_assumptions`

### VS001_shot3  9.0-10.5s  （function: detail_proof）

- 参考镜头: `VS001:shot3`
- 生成画面: 手部浅景深特写，叠加左上画中画子画面补展示甲面细节
- 必须可见: <人物1>; <全局素材1> 目标穿戴甲设计; <场景2>（户外暗色草地与静水，前中后景层次保留，水面低反射深色静水，天空厚重阴云，冷色低明度散射光，轻微薄雾）
- 使用素材: `reference_video_excerpt`(motion_camera_timing_reference), `A001`(nail_pattern_source_and_style_reference), `RF001`(person_reference), `RF003`(scene_reference)
- 参考帧决策: RF001, RF003 (entity: E002, E004)
- 后期叠加: O003
- 缺失项: mi_001 / 生成假设: asm_002, asm_003, asm_004

#### VS001_seg7  9.0-10.5s (1.5s)

- 参考功能 / 目标功能: `visual_display` / `visual_display`
- 生成画面（主体）: 单手浅景深特写夹持 <全局素材2> 深色花材，完整目标甲面清晰可见
- 动作/运镜: 夹花静止→仅轻微移动，主画面与子画面同时保持；基本静止的手持镜头，极慢运动
- 构图/景别: 手部浅景深特写，单手位于画面中央; 画面左上角固定一个独立子画面小窗，形成主画面＋子画面的多层版式
- 场景迁移: [E004] <场景2>（户外暗色草地与静水，前中后景层次保留，水面低反射深色静水，天空厚重阴云，冷色低明度散射光，轻微薄雾）
- 甲面可见状态: 完整的<全局素材1>：黑与深棕基底、银色金属纹理、立体珍珠与金边珍珠、立体眼睛图案（棕与黄绿虹膜）、滴落状黑胶
- 画面文字: 底部说明文字层占位（文案缺失），保留底部位置与整段持续时间
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: O003(caption, missing_required_input, 底部居中安全区)
- 参考帧: RF001, RF003
- 特殊机制: M002_picture_in_picture[special_composition]; M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: composition_conflict:nc_keep_picture_in_picture_layout; unconfirmed_text_logo:nc_no_invented_readable_text / mi_001
- status: `ready_with_assumptions`

### VS001_shot4  10.5-15.0s  （function: closing）

- 参考镜头: `VS001:shot4`
- 生成画面: 暗色坡地与金属格构结构前的中景，换装后继续展示同一套甲面，并以正俯拍收束
- 必须可见: <人物1>; <全局素材1> 目标穿戴甲设计; <场景3>（户外暗色坡地与深色金属格构结构，暗色岩土与暗草坡，远景格构框架作几何锚点，阴云散射光）
- 使用素材: `reference_video_excerpt`(motion_camera_timing_reference), `A001`(nail_pattern_source_and_style_reference), `RF001`(person_reference), `RF004`(scene_reference)
- 参考帧决策: RF001, RF004 (entity: E002, E005)
- 后期叠加: 无
- 缺失项: 无 / 生成假设: asm_002, asm_003

#### VS001_seg8  10.5-12.5s (2.0s)

- 参考功能 / 目标功能: `action_or_interaction` / `action_or_interaction`
- 生成画面（主体）: <人物1> 在 <场景3> 中以炭黑色长外套与深色宽檐帽造型抬手展示完整甲面
- 动作/运镜: 抬手展示甲面→手触碰帽檐；基本静止的手持镜头，轻微晃动
- 构图/景别: 中景，主体居中，手部为信息区; 平视机位，背景格构结构位于远景
- 场景迁移: [E005] <场景3>（户外暗色坡地与深色金属格构结构，暗色岩土与暗草坡，远景格构框架作几何锚点，阴云散射光）
- 甲面可见状态: 完整的<全局素材1>：黑与深棕基底、银色金属纹理、立体珍珠与金边珍珠、立体眼睛图案（棕与黄绿虹膜）、滴落状黑胶
- 画面文字: 无画面文字层
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: 无
- 参考帧: RF001, RF004
- 特殊机制: M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: 无 / 无
- status: `ready_with_assumptions`

#### VS001_seg9  12.5-13.5s (1.0s)

- 参考功能 / 目标功能: `action_or_interaction` / `action_or_interaction`
- 生成画面（主体）: <人物1> 蹲坐在 <场景3> 暗色坡地上、双手靠近面部
- 动作/运镜: 蹲坐→手靠近面部→机位转为正俯拍；机位发生一次明显变化：由平视中景转为垂直向下的正俯拍
- 构图/景别: 中景转为正俯拍，人物在画面中呈现地图式空间关系; 俯拍时人物位于画面中央，双手向镜头方向抬起
- 场景迁移: [E005] <场景3>（户外暗色坡地与深色金属格构结构，暗色岩土与暗草坡，远景格构框架作几何锚点，阴云散射光）
- 甲面可见状态: 完整的<全局素材1>：黑与深棕基底、银色金属纹理、立体珍珠与金边珍珠、立体眼睛图案（棕与黄绿虹膜）、滴落状黑胶
- 画面文字: 无画面文字层
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: 无
- 参考帧: RF001, RF004
- 特殊机制: M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: 无 / 无
- status: `ready_with_assumptions`

#### VS001_seg10  13.5-15.0s (1.5s)

- 参考功能 / 目标功能: `closing_or_prompt` / `closing_or_prompt`
- 生成画面（主体）: 正俯拍下 <人物1> 双手抬起展示完整甲面
- 动作/运镜: 俯拍展示→双手朝镜头抬起展示甲面→镜头结束；镜头基本静止，极慢运动，轻微手持晃动
- 构图/景别: 正俯拍，双手占据画面中央并成为唯一信息区; 9:16 竖屏，主体居中
- 场景迁移: [E005] <场景3>（户外暗色坡地与深色金属格构结构，暗色岩土与暗草坡，远景格构框架作几何锚点，阴云散射光）
- 甲面可见状态: 完整的<全局素材1>：黑与深棕基底、银色金属纹理、立体珍珠与金边珍珠、立体眼睛图案（棕与黄绿虹膜）、滴落状黑胶
- 画面文字: 无画面文字层
- 画面内实体文字/logo: 无（未确认内容，不生成可读文字）
- 后期叠加状态: 无
- 参考帧: RF001, RF004
- 特殊机制: M003_nail_display_gesture_chain[micro_action]
- 禁止项/缺失项: 无 / 无
- status: `ready_with_assumptions`

## 脚本文案与音频

- script_copy.status: `missing_inputs`
- 画面文字槽: txt_001=missing_required_input; txt_002=missing_required_input; txt_003=missing_required_input
- 台词/口播/旁白: 无（参考视频无口播，画面无口型）
- unsupported_audio.status: `unsupported_skipped`
- 交付指令: 音乐: 跟随参考视频音乐风格.

## 缺失项与生成假设

- missing_inputs: mi_001(on_screen_captions), mi_002(worn_state_carrier), mi_003(person_or_body), mi_004(scene_content), mi_005(supporting_props)
- generation_assumptions: asm_001(nail_pattern_on_worn_state), asm_002(person_appearance), asm_003(scene_content), asm_004(supporting_props), asm_005(comparison_contrast_state)
- blocking_items: 无

## H3 状态

- H3 packager input: `09_h3_package/h3_packager_input.md`（步骤 9 生成）
- H3 prompt package: `09_h3_package/minimax_h3_prompt.md`（packager-minimax-h3 生成）
- H3 request: 由本 dry-run 在 H3 提交边界前生成，未提交、未运行 H3 视频生成
- H3 视频生成状态: `not_submitted_dry_run_boundary`

## 说明

- downstream prompt 若把 temporal_segments 渲染为多个 `[Shot N]`，那是 prompt 层段落标签；参考层仍是 4 个 shot。
- 画面文字与字幕属后期叠加层，H3 只生成 clean plate 并预留顶部/底部安全区。
- 音乐、BGM、音效与声音节奏保持 `unsupported_skipped`。
