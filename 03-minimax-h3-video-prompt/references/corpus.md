# 五模式填空模板

五种模式的逐字骨架语料。**尖括号处替换、字段名与标签拼写不得改写**；匹配到模式后按本文件骨架填充，成稿后对照三字段结构（首行对齐指令 + 空行 + 三字段）逐项自检（见 `modules/mode-routing.md` 第二节）。成品末尾须原样附上【强制声明】（见 `output-template.md`）。

## 速查索引

| # | 模式 | 首行对齐指令 | 结构 |
|---|------|--------------|------|
| 01 | T2VA（纯文本） | 无对齐指令直接进核心字段 | 三字段 |
| 02 | I2VA（首帧图） | 固定句，Picture 1 锁 0.00 秒 | 三字段 |
| 03 | FL2VA（首尾帧图） | 固定句，Picture 1/2 各锁一位 | 三字段 |
| 04 | L2VA（尾帧图） | 固定句，Picture 1 锁 S.SS 秒 | 三字段 |
| 05 | Ref2VA（全参考） | 无首行对齐指令 | 六段结构 |

## 01 · T2VA（纯文本）

逐字骨架（尖括号处替换、字段名与标签拼写不得改写）：

```text
integrated_multimodal_description:
[Shot 1] <整体风格，从 Cinematic / live-action / 2D-animated / 3D CG / claymation / watercolor / vintage film 中选>. <初始构图与主体>. <动作与运镜：The camera pushes in with small amplitude at slow speed toward ...>. <说话人：The young woman with a quiet, breathy voice (S1) says: <d>[Chinese] 对白原文</d>>
[Shot 2] At 00:04.000, the camera cuts to <新信息>. ...
overall_soundscape: <1–4 句英文：环境声+物理动作声+非语言人声>
non_diegetic_music: <1–3 句英文：乐器/速度/节奏/力度，或 N/A>
```

## 02 · I2VA（首帧图）

首行固定 'For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.'，空一行后进三字段：

```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description:
[Shot 1] <整体风格>. The shot begins from <Picture 1> exactly as given — <主体、服装、道具、空间关系锚点>. Then <动作开始 → 连续发展 → 结果或反应；不重复描述图中的静态内容>. <运镜三维>
[Shot 2] At MM:SS.mmm, the camera cuts to <新信息>. ...
overall_soundscape: <1–4 句英文>
non_diegetic_music: <1–3 句英文，或 N/A>
```

## 03 · FL2VA（首尾帧图）

首行固定 'How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot N) aligns with the S.SS-second mark of the target video.'（S.SS 为有效时长两位小数；注意 FL2VA 对齐句里 Picture 1/2 与 Shot N 均不带尖括号/方括号，与 I2VA/L2VA 写法不同），空一行后进三字段：

```text
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot N) aligns with the S.SS-second mark of the target video.

integrated_multimodal_description:
[Shot 1] <整体风格>. The shot begins from <Picture 1> and ends on <Picture 2> — <只写连接两帧的运动路径：主体移动 / 姿态变化 / 道具操作 / 构图演变 / 光影过渡；倾向单镜头>. <运镜三维>
overall_soundscape: <1–4 句英文>
non_diegetic_music: <1–3 句英文，或 N/A>
```

## 04 · L2VA（尾帧图）

首行固定 'How the reference pictures align with the target video — <Picture 1> (from [Shot N]) aligns with the S.SS-second mark of the target video.'，空一行后进三字段：

```text
How the reference pictures align with the target video — <Picture 1> (from [Shot N]) aligns with the S.SS-second mark of the target video.

integrated_multimodal_description:
[Shot 1] <整体风格>. <合理前态>. <明确动作与过渡路径，结尾镜头逐步收敛>. The shot ends on <Picture 1> at the end of the video. <运镜三维>
overall_soundscape: <1–4 句英文>
non_diegetic_music: <1–3 句英文，或 N/A>
```

尾帧图属于结尾镜头、不天然属于 Shot 1。

## 05 · Ref2VA（全参考，六段顺序固定全英文）

逐字骨架：

```text
subject_definitions: <Subject 1> is a ... defined by <Picture 1> (identity) and <Video 1> (motion trajectory only). <Audio 1> is the voice-timbre reference for <Subject 1> (S1).
summary: [keyframe completion + audio reference] The target video is ...（视频编辑任务以 'The target video is an edited version of <Video 1>.' 开头）
retention_analysis: <Subject 1>: fully_preserved, appears in Shots 1–3. <Audio 1>: reference (timbre only).
detailed_description: <一两句整体风格声明，写在 [Shot 1] 之前>. [Shot 1] ... （350–500 英文词，标签插在首次出现与生效处，帧锚点用 'the shot begins from <Picture 1>' 类自然表达）
overall_soundscape: ...
non_diegetic_music: ...
```

## 06 · 通用提醒

说话人 (S1)(S2) 按实际发声顺序分配一次全程复用；`<d>` 内只放语言标签+对白原文逐字不翻译；旁白固定 'says in an off-screen voiceover' 且 `<d>` 后紧跟画内角色双唇紧闭说明；跨剪辑点延续的声音用 `<scenetrans>`；结束截断用 `<cutoff>`；画面可见文字用英文双引号包裹原文。

**成品末尾硬约束**：提示词全文末尾原样附上——禁止项: 文字/UI/水印/Logo/角标/可读文字/真实UI。【强制声明】无背景音乐，仅保留环境音与人声；画面禁字幕/文字/水印/Logo；禁止可读文字；禁止超现实夸张；禁止无反作用力动作。

**字符硬上限**：整篇提示词（首行对齐指令 + 三字段/六段结构 + 末尾强制声明，全部字符计入）合计不得超过 2000 字符。逼近上限时按此顺序取舍：先删可省的运镜幅度与速度修饰、再合并信息重复的相邻镜头，最后才压缩描述句；任何时候不压缩字段名、标签拼写、时间码精度与 `<d>` 内对白/歌词原文。交付前数一遍全文字符数，超限先精简再出稿。

## 07 · 完整填充示例（T2VA，可对照改写）

```text
integrated_multimodal_description:
[Shot 1] Cinematic. A narrow bookstore aisle at closing time, warm tungsten light, a young woman in a charcoal coat standing beside a tall bookshelf. The camera holds at eye level, static. The young woman with a quiet, breathy voice (S1) says: <d>[Chinese] 我要找的那本书，昨天还在这里。</d>
[Shot 2] At 00:04.000, the camera cuts to a close-up of a handwritten note tucked between two worn paperbacks, dust floating in the light. The camera pushes in with small amplitude at slow speed toward the note.
[Shot 3] At 00:08.500, the camera cuts to her hand lifting the note; she reads it and her shoulders ease. She says: <d>[Chinese] 原来你把它放错了。</d>
overall_soundscape: Quiet bookstore interior with a soft fluorescent hum, the rustle of a coat, a faint page turn, and distant footsteps on wood.
non_diegetic_music: Solo piano, slow tempo, soft dynamics, a single sustained note held under the final line.

禁止项: 文字/UI/水印/Logo/角标/可读文字/真实UI。【强制声明】无背景音乐，仅保留环境音与人声；画面禁字幕/文字/水印/Logo；禁止可读文字；禁止超现实夸张；禁止无反作用力动作。
```

## 08 · 典型案例库

四种典型范式各配一条完整原创示例。示例为原创虚构重构，写法上分别启发于 ZeroLu/awesome-minimax-h3、ofoxai/awesome-ai-video-prompts、xianyu110/awesome-minimax-h3-prompts 三个外部案例集（仅作节奏与结构启发，人物、场景、台词均未照抄）；字段名、标签拼写、时间码规则与本文件其他骨架逐字一致；生成参数一律不进代码块，参数行写法见 `modules/mode-routing.md` 第七节。

### 案例 A · 情景喜剧对白节奏（T2VA；启发自 ofoxai/awesome-ai-video-prompts 的对白节奏类案例）

范式要点：双人一来一回、短句快切、笑点落在反应拍；说话人 ID 全局稳定、每镜一句短对白，节拍压缩在 10 秒内。

```text
integrated_multimodal_description:
[Shot 1] Live-action. A small rental kitchen on a bright morning, a man in a rumpled shirt (S1) holding a smoking frying pan, a woman at the dining table (S2) looking up. The camera holds at eye level, static. (S1) says: <d>[Chinese] 粥糊了，你还有心情喝咖啡？</d>
[Shot 2] At 00:03.000, the camera cuts to S2 slowly sipping coffee, deadpan. The camera holds, static. (S2) says: <d>[Chinese] 至少咖啡是清醒的。</d>
[Shot 3] At 00:06.500, the camera cuts back to S1 waving the pan, smoke drifting up. (S1) says: <d>[Chinese] 那它比这个家先醒了。</d>
overall_soundscape: Sputtering frying pan, a kettle hissing, a spoon tapping a mug, chairs creaking on a kitchen floor.
non_diegetic_music: N/A.

禁止项: 文字/UI/水印/Logo/角标/可读文字/真实UI。【强制声明】无背景音乐，仅保留环境音与人声；画面禁字幕/文字/水印/Logo；禁止可读文字；禁止超现实夸张；禁止无反作用力动作。
```

### 案例 B · 街头纪实（I2VA；启发自 xianyu110/awesome-minimax-h3-prompts 的市井纪实类案例）

范式要点：以首帧静帧为锚，手持跟拍、环境声铺满，只写锚点之后的人流变化与镜头移动，不复述画面静态内容。

```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description:
[Shot 1] Vintage film. The shot begins from <Picture 1> exactly as given. Then the camera holds behind the noodle vendor for two beats, a passerby steps into frame and takes the paper bowl, steam drifting between them. The camera follows with small amplitude at slow speed over the vendor's shoulder.
[Shot 2] At 00:05.000, the camera cuts to a close handheld shot of rain on a vinyl awning, blurred pedestrians passing behind it. The camera holds, static.
overall_soundscape: Rain on canvas, sizzling broth, scooter engines passing, vendors calling to each other.
non_diegetic_music: N/A.

禁止项: 文字/UI/水印/Logo/角标/可读文字/真实UI。【强制声明】无背景音乐，仅保留环境音与人声；画面禁字幕/文字/水印/Logo；禁止可读文字；禁止超现实夸张；禁止无反作用力动作。
```

### 案例 C · 电影动作（T2VA；启发自 ZeroLu/awesome-minimax-h3 的动作场面临本）

范式要点：先立戏剧目标（甩脱追捕），弹药/门闩等资源连续可追，运镜跟紧主体，动作落点有反作用力。

```text
integrated_multimodal_description:
[Shot 1] Cinematic. A narrow rooftop corridor at dusk, a runner in a dark jacket sprinting toward a metal door, a second man ten meters behind him. The camera tracks with large amplitude at fast speed beside the runner.
[Shot 2] At 00:04.000, the camera cuts to the runner's hand slamming the door bolt home; the pursuer crashes into the door from the other side, dust shaking loose above the frame. The camera pushes in with small amplitude at slow speed toward the bolt.
[Shot 3] At 00:08.000, the camera cuts to the runner pressing his back against the door, chest heaving, then breaking into a run toward the far edge of the rooftop.
overall_soundscape: Scuffing footsteps on concrete, a metal door rattling under impact, labored breathing, a distant siren fading in.
non_diegetic_music: Low strings, fast tempo, heavy dynamics, a two-beat impact under the door slam.

禁止项: 文字/UI/水印/Logo/角标/可读文字/真实UI。【强制声明】无背景音乐，仅保留环境音与人声；画面禁字幕/文字/水印/Logo；禁止可读文字；禁止超现实夸张；禁止无反作用力动作。
```

### 案例 D · 节拍卡点（T2VA；启发自 ofoxai/awesome-ai-video-prompts 的卡点剪辑类案例）

范式要点：切点对齐鼓点，每镜一个定格动作单元；非叙事音乐只写速度、力度与鼓点间隔，不写情绪词。

```text
integrated_multimodal_description:
[Shot 1] 2D-animated. A dancer in a neon-lit alley, holding a mid-frame pose as the downbeat lands. The camera holds, static.
[Shot 2] At 00:02.500, the camera cuts on a snare hit to the dancer jumping into the air, limbs spread wide. The camera holds, static.
[Shot 3] At 00:05.000, the camera cuts on the next snare hit to a floor spin, the coat flaring around the body. The camera holds, static.
[Shot 4] At 00:07.500, the camera cuts on the final beat to a frozen landing pose, smoke exhaling from the mouth. The camera pushes in with small amplitude at slow speed toward the dancer.
overall_soundscape: Street echo, shoe squeaks on pavement, coat fabric snapping, a distant city rumble.
non_diegetic_music: Electronic drum loop, fast tempo, strong dynamics, snare hits every 2.5 seconds under each cut.

禁止项: 文字/UI/水印/Logo/角标/可读文字/真实UI。【强制声明】无背景音乐，仅保留环境音与人声；画面禁字幕/文字/水印/Logo；禁止可读文字；禁止超现实夸张；禁止无反作用力动作。
```
