# 模式判定与基础输出结构

成稿前第一步。**按用户手里的素材路由五种生成模式**——素材不全或模式拿不准先问清用户，不猜。

## 一、模式判定

MiniMax H3 按用户手里的素材路由五种生成模式：

| 生成模式 | 素材条件与用途 |
| --- | --- |
| T2VA | 纯文本构建完整视听时间轴 |
| I2VA | 有首帧图，从首帧向前发展 |
| FL2VA | 有首尾两帧图，补齐两帧之间的连续路径 |
| L2VA | 只有尾帧图，反推合理开场并收束到尾帧 |
| Ref2VA | 全参考模式，参考素材含图片/视频/音频任意组合（角色参考、场景参考、源视频剪辑或续写、音频复用或音色参考）时用 |

- 素材不全或模式拿不准先问清用户，不猜
- **视频总时长 4–15 秒，描述的动作总时长必须与请求时长匹配**
- 同一角色跨 ≥2 个镜头、或用户明确要求跨镜一致时，先按第六节走「角色设定图 → 首帧静帧 → 视频提示词」三步，再按本表路由模式

## 二、基础模式输出结构（三字段）

基础模式输出结构（T2VA/I2VA/FL2VA/L2VA，**字段名、顺序、标签拼写逐字一致，禁止改写**）：

1. **第一行是关键帧对齐指令**——
   - T2VA 无指令直接进核心字段
   - I2VA 固定写 'For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.'
   - FL2VA 写 'How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot N) aligns with the S.SS-second mark of the target video.'
   - L2VA 写 'How the reference pictures align with the target video — <Picture 1> (from [Shot N]) aligns with the S.SS-second mark of the target video.'
   - **N 是实际结尾镜头号，S.SS 是视频有效时长、必须精确到两位小数**
2. **指令行后空一行，再依次给三个核心字段：integrated_multimodal_description（沿时间轴写视觉、动作、镜头、说话人、对白、歌唱与画内音）、overall_soundscape、non_diegetic_music**

## 三、integrated_multimodal_description 写法

- [Shot 1] 开头声明整体风格与初始构图，**风格从 Cinematic / live-action / 2D-animated / 3D CG / claymation / watercolor / vintage film 中选**，关键帧任务从参考图推导、T2VA 从用户文本取
- **首镜不加时间戳，后续镜头用 [Shot N] At MM:SS.mmm 格式，切点时间严格递增且落在总时长内**
- 普通剪辑用 'the camera cuts to' 家族表达，cross-dissolve/fade/wipe 只在用户明确要求时用
- **每次切镜必须引入新信息**（主体、空间、状态、视点或时间），只想改距离或微调角度时优先用运镜不切镜
- **运镜写全三维**——运动类型（Zoom In/Out、Push In/Pull Out、Pan Left/Right、Truck Left/Right、Tilt Up/Down、Pedestal Up/Down、Arc Shot、Tracking Shot、Static Shot、Shake Slightly/Strongly、POV、Roll Clockwise/Counterclockwise）+ 幅度（with small amplitude / with large amplitude）+ 速度（at slow speed / at fast speed），**中等幅度与常速通常省略，必须写成自然英文动作句**（如 'The camera pushes in with small amplitude at slow speed toward the folded letter in her hands.'），**不在句尾堆标签**
  - 反例（句尾堆标签）：'The camera moves. Zoom In. small amplitude. slow speed.' → 正例：'The camera pushes in with small amplitude at slow speed toward the letter.'

## 四、关键帧衔接

- **I2VA** 按「首帧锚点 → 动作开始 → 连续发展 → 结果或反应」，先立住图中的风格、主体、构图、场景锚点再写下一步动作，角色身份、服装、颜色、关键道具、空间关系全程一致
- **FL2VA** 按「首帧状态 → 可观察的中间变化 → 差异逐步收窄 → 尾帧状态」，**正文不重复两张图的静态描述、只供给连接二者的运动路径**（主体如何移动、姿态如何变化、道具如何被操作、构图如何演变、光影如何过渡），**一般倾向单镜头利于连续插值，尾帧必须由结尾镜头在视频结束时抵达**
- **L2VA** 按「合理前态 → 明确动作与过渡路径 → 结尾镜头逐步收敛 → 尾帧落定」，**尾帧图属于结尾镜头、不天然属于 Shot 1**

## 五、审查

- [ ] 模式已按素材路由（T2VA/I2VA/FL2VA/L2VA/Ref2VA），素材不全已问清用户、未猜
- [ ] 总时长在 4–15 秒，描述的动作总时长与请求时长匹配
- [ ] 对齐指令在第一行（T2VA 无对齐指令直接进核心字段），N 为实际结尾镜头号、S.SS 精确到两位小数
- [ ] 指令行后空一行，再依次给 integrated_multimodal_description / overall_soundscape / non_diegetic_music 三字段
- [ ] [Shot 1] 声明整体风格与初始构图；后续镜头 [Shot N] At MM:SS.mmm 严格递增且落在总时长内
- [ ] 每次切镜引入新信息；运镜写全三维、为自然英文动作句、未在句尾堆标签
- [ ] FL2VA 未重复两图静态描述、倾向单镜头；L2VA 尾帧属于结尾镜头
- [ ] 与下游衔接：对白与画面文字见 `speaker-dialogue.md`；Ref2VA 六段结构见 `sound-ref2va.md`
- [ ] 跨镜一致性：多镜跨人物片段已先过第六节角色设定图三步，或已注明交 07-consistency-check 闭环
- [ ] 正文未写模型名/版本/时长/分辨率/比例/API 参数名（首行对齐指令与时间戳为明确例外）；生成参数在提示词外单独成行「Recommended parameters」
- [ ] I2VA/FL2VA/L2VA/Ref2VA 参考图只作视觉锚点，未详细复述图中静态画面内容

## 六、跨镜一致性前置三步（角色设定图 → 首帧静帧 → 视频提示词）

同一角色跨 ≥2 个镜头、或用户明确要求跨镜一致（脸不变、换装不漂移、道具不变色）时，按此三步前置再进模式路由：

1. **角色设定图（character sheet）**：先出一张角色设定图，覆盖正面/侧面/背面、服装主色与形制、发型、关键道具——它是全片身份基准，后续所有镜头的角色外观以它为锁面来源
2. **首帧静帧**：从设定图派生第一镜的首帧静帧（I2VA 的 Picture 1），把设定图的身份基准落进具体场景、构图与光线
3. **视频提示词**：按第一节路由模式、按第二节三字段结构写提示词；角色身份、服装、颜色、关键道具在 [Shot 1] 按设定图复述一次，后续镜头不再重新描述外观，只写动作与状态变化

- 设定图与首帧静帧是上游图像产出，本技能只负责把它们锁进提示词；用户没给时先建议补齐、不猜
- 设定图作角色参考进生成时走 Ref2VA（四种参考标签见 `sound-ref2va.md`）
- **一致性自查闭环**：设定图、首帧静帧与视频提示词在提交生成前，交 `../../../07-consistency-check/SKILL.md` 的五道清单（机械检查→语义审查→连续性锁核对→镜头覆盖→成片比对）逐项过一遍，专抓跨镜换脸、换装、道具变色、场景漂移；成片生成后疑似穿帮时按同一闭环回定位到具体提示词句再修订

## 七、全局视频提示词规则

- **正文不写参数**：提示词正文（首行对齐指令 + 三字段/六段）内不出现模型名、模型版本、时长数值、分辨率、画幅比例、任何 API 参数名——**明确例外**：首行关键帧对齐指令与 [Shot N] At MM:SS.mmm 时间戳照常写
- **参数单独成行、附在提示词外**：时长、分辨率、画幅等生成参数不写进代码块，在代码块外单独一行写「Recommended parameters: ...」（如 Recommended parameters: duration 10s, aspect 9:16），并注明以生成端当前支持的可选值为准
- **参考图只当视觉锚点**：I2VA/FL2VA/L2VA/Ref2VA 的参考图是已给定的视觉锚点，正文以 'the shot begins from <Picture 1> exactly as given' 类自然句引用，不详细复述图中静态画面内容；正文只写图无法预知的发展——动作、运动路径、姿态变化、结果与反应
