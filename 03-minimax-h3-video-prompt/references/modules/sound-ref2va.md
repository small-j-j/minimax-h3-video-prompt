# 两个声音字段与 Ref2VA 全参考模式

基础模式两个声音字段按分工写；Ref2VA 全参考模式走六段固定结构。**标签一经分配在六段全程保持同一含义，不允许出现未解析标签。**

## 一、两个声音字段

- **overall_soundscape** 用 1–4 句英文连续一段总结全片环境声、物理动作声与非语言人声（风、雨、交通、脚步、织物摩擦、撞击、呼吸、笑声、喘息），**不重复描述里已写的对白、歌唱与画内音乐**，只有用户明确要求全片完全静默才写 N/A
- **non_diegetic_music** 用 1–3 句描述角色听不见、只有观众听得见的背景音乐，**只写乐器、速度、节奏与力度变化，禁止抽象情绪词、不解释配乐的情感功能**，角色能听见的音乐（歌唱、收音机、电视、手机外放）属画内事件写进 description，无画外乐写 N/A

## 二、Ref2VA 全参考模式（六段结构）

Ref2VA 全参考模式（**六段结构，顺序固定**）：subject_definitions → summary → retention_analysis → detailed_description → overall_soundscape → non_diegetic_music，**六段全用英文写**。

## 三、四种参考标签

| 标签 | 用途与边界 |
| --- | --- |
| <Subject N> | 是可复用的可见内容（人物、动物、物体、场景、环境、服装、道具、界面、特效、风格、动作、表情、姿态），代表目标视频里实际使用的内容单元而非源文件，一个主体可由多资产联合定义并写明各资产提供什么 |
| <Picture N> | 只在图片本身充当某镜头的首帧、关键帧、尾帧或构图锚点时才独立立项，图片仅用于定义角色、场景、服装、风格时并入对应 Subject 的定义、不单独立项，分镜参考要写明映射哪些镜头与提供什么规划信息 |
| <Video N> | 只保留给整视频关系（剪辑源视频、从结尾续写、参考其运镜/剪辑/节奏/时间结构），被复用的人物、物体、动作仍归 Subject |
| <Audio N> | 代表独立音频资产或启用的同步音轨（全部或部分复制信号、参考背景音乐风格、参考音色与交付方式、取用对白/歌词/音效、参考节拍/节奏/连续性），对应到目标说话人时复用其全局 ID（如 '<Audio 1> is the voice-timbre reference for <Subject 1> (S1).'） |

- **Video 与 Audio 各自独立编号、序号不表示配对，普通参考视频不因带声音就自动产生 Audio 条目**
- **标签一经分配在六段全程保持同一含义，不允许出现未解析标签**

## 四、summary 规则

- **summary 以方括号任务类型前缀开头，任务类型六选——keyframe completion / reference generation / video editing / video continuation / audio reuse / audio reference，多关系用 ' + ' 连接不重复**
- 视频编辑任务前缀后以 'The target video is an edited version of <Video 1>.' 开头
- **视频或音频资产 mere presence 不自动产生对应任务类型——只取运镜、剪辑或节奏时属 reference generation**

## 五、retention_analysis 规则

- **retention_analysis 每标签一行——可见内容用四种关系标记 fully_preserved / partially_preserved / attribute_transfer / weak_reference 并注明出现在哪些镜头**
- 音频用 fully_copy / partially_copy / reference / weak_reference
- **标记只能在 subject_definitions 已定义的参考角色内选取，目标视频新增的动作、背景、情节不算保真损失**
- **retention_analysis 里不出现 (Sx)**

## 六、detailed_description 规则

- **在 [Shot 1] 之前用一两句英文先立整体风格**（与基础模式的关键格式差异——基础模式风格写在 [Shot 1] 之后）
- **正文一般 350–500 英文词**，对白密集内容优先装下完整对白时间轴而非机械凑词数，视频编辑按源视频复杂度伸缩，单镜头不自动缩短、按各镜头信息量分配细节
- **标签插在参考内容首次出现与其角色生效处**，帧锚点用自然表达（'the shot begins from <Picture 1>' / 'the shot ends on <Picture 3>'）
- **被引用主体说话时写 <Subject N> (Sx)，画外发声保持同形并标注 off-screen**，说话人不对应已定义 Subject 时用稳定音色描述 + (Sx)
- 只出现在直接复用 BGM 里的语言线索用 <Audio N> 当可听来源、不另造 (Sx)，具体人物、角色、旁白实际发声才分配 (Sx)
- **(Sx) 按目标视频实际发声事件出现顺序分配一次并全程复用**
- 直接复用或要求重演参考音频的对白/歌词时 `<d>` 内保留源语言原文逐字不动，**听不清的片段写 [unclear] 不猜测不改写**，标点规范为基本书面符号（逗号、句号、问号、叹号），去掉重复波浪线、emoji、装饰性标点
- 只参考音色、节奏、情绪、交付方式时不把参考音频里的原对白带进目标视频
- **音频的复制或参考关系写在与其可听层对应的段落**——环境声与音效归 overall_soundscape、观众专属配乐归 non_diegetic_music，同一音频两类内容都有时分段各自描述

## 七、审查

- [ ] overall_soundscape 1–4 句英文连续一段，未重复对白歌唱画内音乐；全片静默才写 N/A
- [ ] non_diegetic_music 只写乐器/速度/节奏/力度变化，无抽象情绪词、未解释配乐情感功能；无画外乐写 N/A
- [ ] Ref2VA 六段顺序固定全英文：subject_definitions → summary → retention_analysis → detailed_description → overall_soundscape → non_diegetic_music
- [ ] 四种参考标签边界正确（Subject/Picture/Video/Audio 立项条件）
- [ ] summary 方括号任务类型六选，视频编辑以固定句开头
- [ ] retention_analysis 每标签一行，标记在已定义参考角色内选取，无 (Sx)
- [ ] detailed_description 风格声明写在 [Shot 1] 之前；(Sx) 按发声顺序分配一次全程复用；`<d>` 内源语言原文逐字不动
- [ ] 标签全程同义无未解析项
- [ ] 与下游衔接：导演强化见 `directional-directing.md`；填空骨架见 `../corpus.md`
