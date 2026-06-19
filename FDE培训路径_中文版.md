# 从零成为 Forward Deployed Engineer(FDE):完整真实培训路径(先国内,约 6 个月后冲美国)

> 本文为英文研究报告的中文版。所有薪资、公司、网址、面试真题均为真实数据,原样保留;讲解部分译为中文。

## 一句话总结
- **FDE(Forward Deployed Engineer,前向部署工程师)= 一名亲自写代码、嵌入到客户环境里、在客户的真实系统中交付生产级代码的软件工程师**。这是 Palantir 最早开创的岗位(内部代号 "Delta"),如今 OpenAI、Anthropic、Scale AI、Glean、Decagon、Sierra 以及大量 AI 创业公司都在大量招聘。需求正在爆发:据 Indeed 数据(Business Insider 报道),FDE 岗位从 2025 年 4 月的 643 个增长到 2026 年 4 月的 5,330 个,同比增长 **729%**;ICONIQ Capital 2025 软件行业报告统计的 127 家软件公司里,FDE 月度岗位从 2024 年初的约 30 个涨到 2025 年 4 月的 375 个(约 12 倍)。这个岗位的本质是 **写代码 + 直接对接客户 + 产品理解 + 领域知识** 的混合体。
- **你的现实路径:** 以你目前的基础(Python/C++ 基础、写过简单 HTML、调 API 失败过),距离国内初/中级的"交付/解决方案/实施工程师"或"大模型应用开发工程师"岗位大约 **9–15 个月**,距离有竞争力的外企/美国 FDE 门槛大约 **12–18 个月**。最关键、最快见效的一步,就是 **先把 API 调通,然后做出 2–3 个真实的端到端 LLM 应用**——这正是国内外雇主现在筛人的核心能力(调 LLM API、RAG、评测 evals)。
- **薪资是真实而且很高的:** Palantir 的 FDSE 全美总包中位数约 **$207,500**(Levels.fyi;区间约 $155K–$295K,纽约可到约 $358K);前沿大模型实验室(OpenAI/Anthropic)的 FDE 可达 $300K–$1M+;国内 AI 应用/解决方案类岗位大致在 **¥25K–¥60K/月(¥30 万–¥72 万+/年)**,顶级实验室更高。**美国岗位对中国候选人需要 H-1B/签证赞助**——OpenAI 和 Anthropic 都明确提供签证赞助,所以"6 个月冲美国"是可行的,但时间点高度依赖 H-1B 抽签。

---

## 核心发现

### 1. FDE 究竟是什么

- **起源:** Palantir 在 2010 年代初创造了 "Forward Deployed Software Engineer"(FDSE)这一岗位,内部昵称 **"Delta"**;"forward deployed(前向部署)"借自军事术语,意思是"在最前线、最接近行动点的地方作战"。在 2016 年前,Palantir 的 FDE 数量甚至超过传统("Dev")软件工程师。核心思路是:把一名工程师嵌入到客户那套混乱的真实环境里,让软件在现实中真正跑起来,然后把反复出现的模式抽象、沉淀回产品(Foundry、Gotham、AIP)。
- **与相邻岗位最清晰的分界线:** 看 **谁在客户的基础设施上写生产代码**——只有 FDE 会写。售前/解决方案工程师做售前演示和 POC;解决方案架构师出设计文档然后交接;客户/实施工程师做配置和支持;ML 工程师在公司内部做模型,基本不直接面对客户;咨询顾问只给建议、不拥有生产代码。Palantir 自己的说法:FDE 的职责"看起来很像一家创业公司 CTO 的职责"。
- **日常工作 / 交付生命周期:** 调研 → 范围界定(scoping)→ 系统设计 → 构建 → 上生产 → 把经验反馈给产品。典型的一天(据 Palantir 的 "Day in the Life" 和 Pragmatic Engineer):上午客户站会,下午在客户的基础设施/数据/权限体系里写生产代码,傍晚把学到的东西反馈给总部的产品/研究团队。
- **混合属性:** 据 Bloomberry 对 1,000 份 FDE 招聘信息的分析,技术栈分布为 Python 66%、TypeScript 35%、AWS 32%、LLM 31%、AI Agent 35%,出差 25–50% 需到客户现场。现代"Forward Deployed AI Engineer"岗位还会加上提示词工程、RAG、Agent、评测(evals)、向量数据库。
- **不同公司的"流派":**
  - **Palantir FDSE:** 部署 Foundry/Gotham/AIP;数据集成、本体(ontology)、数据管道;国防/政府/商业客户;出差可达 25%+;通过和核心工程师同样的技术面门槛。
  - **OpenAI FDE("Model Deployment for Business"):** 负责把前沿模型端到端部署到战略客户;全栈(Python/JavaScript);成功的衡量标准是"生产环境采用率、可量化的工作流影响、以及由评测驱动的反馈";出差可达 50%;覆盖政府、生命科学等垂直行业。高级 FDSWE 岗位要求 7+ 年经验。
  - **Anthropic FDE(Applied AI 团队):** "用 Claude 模型构建生产级应用",交付 "MCP servers、sub-agents 和 agent skills";要求有生产环境的 LLM 经验(提示词工程、Agent、规模化评测);3–4+ 年;出差 25–50%;提供签证赞助。
  - **创业公司(Decagon、Glean、Sierra、Scale AI 等):** 接近"创始工程师"的状态;从 0 到 1 自己做;配置 Agent、集成、护栏(guardrails);通常对资历的硬门槛更低。
  - **中国对应岗位:** 交付工程师、解决方案工程师/架构师、实施工程师、售前工程师,以及越来越多的 **大模型应用开发工程师**。在字节跳动的火山引擎、阿里云、腾讯,以及智谱/MiniMax 等实验室,这些岗位把 POC、现场调试、部署/交付、客户培训结合在一起——最接近 FDE 的职能。

### 2. 在招公司与薪资(已核实)

**谁在招(规模):** 据 JobsByCulture 平台实时数据(2026 年 5 月 30 日):118 家公司共 224 个在招 FDE 岗位,招聘量最大的是 Palantir(51)、OpenAI(31)、Databricks(12)、Mistral(11)、Cohere(10)、Cresta(10)、Scale AI(8)、DevRev(8)、Snowflake(7)。更广的名单还包括 Anthropic、Sierra、Decagon、Glean、Hebbia、Harvey、Writer、Cursor/Anysphere,以及大多数 YC 系 AI 应用公司。

**美国/全球 FDE 薪资:**
- **Palantir FDSE:** 招聘信息上的 base 区间 $135K–$200K;Levels.fyi(2025/7/10 更新)全美 **总包中位数 $207,500**(区间 $155K–$295K);纽约地区中位数 $211K(区间 $171K–$358K,2025/11/3 更新);Staff 级别可超 $630K。6figr 报告平均 $231K,前 10% 超 $307K,最高 $631K。Glassdoor base 估计约 $156K。
- **OpenAI FDE:** 据行业报道,旧金山中级 base 约 $160K–$280K;Levels.fyi 显示高级/principal FDE 总包(L5)可超 $1.0M,L6 接近约 $1.28M。
- **Anthropic FDE/Applied AI:** 招聘信息上的 base 区间 **$200K–$300K** 和 **$280K–$320K**(Federal Civilian)。DigiTech Bytes(2026 年 5 月)报告 Anthropic 的 Applied AI Engineer(即 FDE 对应岗)总包中位数 **$582,500**;Perspective AI 报告称大多数 FDE 岗位为 L4–L5,总包 $665K–$750K,股权占 60–70%。
- **整体市场:** Bloomberry 对 1,000 份 FDE 招聘信息(数据来自 Revealera)的分析发现:"中位数为 $173,816……70% 的 FDE 岗位提到股权,只有 8% 提到 OTE,完全没有(0%)是背销售指标的岗位",股权包在 0.1%–1.5%。Perspective AI 的《2026 薪酬报告》(1,200 个数据点):"2026 年中级 FDE 总包中位数 $385K;Staff 级 $610K;前沿实验室的 principal FDE 突破 $1.2M。"

**中国对应岗位与薪资(人民币):**
- 大模型应用 / 大模型应用开发岗:本科/硕士约 ¥25K–¥30K+/月(深信服曾报出 25k 本科 / 30k 硕士);顶级实验室(DeepSeek、字节)校招包据报可达约 ¥50K/月 / ¥75 万/年;大模型算法岗 ¥50K–¥200K/年,但偏资深/算法方向。
- 实施/交付/解决方案岗:区间很宽。初级实施工程师中等水平,且常需出差;解决方案架构师在火山引擎/阿里云的招聘信息显示约 ¥30K–¥60K/月(例如字节/火山引擎"产品解决方案架构师"深圳岗 30–60k·15 薪;阿里云"公共云解决方案架构师"约 35–40k)。
- 注意:国内"实施工程师"口碑两极分化——低端的"装软件 + 培训"工作薪资一般;高价值端(AI 公司的大模型/解决方案/交付)才是 FDE 对应职能里钱多、成长快的地方。

**招聘门槛 / 资历:** 西方 FDE 岗位整体偏资深(3–8 年),且偏爱前创业者/创业公司早期工程师;创业公司则愿意要"作品集亮眼的强通才"。国内岗位(尤其大模型应用/实施)有校招入口。无论中外,核心都是双重筛选:**你能不能既写代码、又能扛住一场客户对话。**

### 3. 技术技能树 + 真实资源

**(A)Python 深度** —— CS50P / CS50x(哈佛,freeCodeCamp YouTube 免费;2026 版新增 AI 章节);Real Python 教程。必须掌握的库:`requests`、`pandas`、`pydantic`、`fastapi`、`sqlalchemy`、`openai`/`anthropic` SDK。

**(B)API 集成 —— 你卡住的那一步。** 具体修复路径:
- 读 **Real Python 的 "Python's Requests Library (Guide)"**(realpython.com/python-requests)和 **"Python and REST APIs: Interacting With Web Services"**(realpython.com/api-integration-in-python)。先用免费的 **JSONPlaceholder**(无需鉴权)练习 GET/POST、headers、`response.raise_for_status()` 和 `response.json()`。
- 学鉴权:header 里的 API key、Bearer token、Basic Auth、OAuth。NetworkLessons 的 "REST API Authentication" 讲得很清楚。
- **真正调通一次 LLM:** DeepSeek 官方文档("Your First API Call",api-docs.deepseek.com)给了可直接复制的 curl + Python 代码(`pip install openai`,设置 `base_url="https://api.deepseek.com"`)。新手最常见的失败原因:① API key 环境变量没设/没 export;② base_url 写错;③ 没设 `Content-Type: application/json`;④ 没处理 429 限流(要用指数退避 backoff)。DeepSeek 兼容 OpenAI API,所以同一套代码只要换 base_url + key 就能用于 OpenAI/大多数厂商。
- 工具:**Postman**(有 DeepSeek 的 collection),先用它把请求可视化地测通,再写代码。

**(C)数据:SQL、pandas、ETL** —— **哈佛 CS50 的 "Introduction to Databases with SQL"**(免费,freeCodeCamp 有完整课程);用 pandas 在真实脏数据上练手。掌握 join、窗口函数、索引、范式(这些在 Palantir 的线上笔试里会出现)。

**(D)后端** —— **FastAPI**(官方教程 fastapi.tiangolo.com/learn + freeCodeCamp 的 FastAPI 课程,包括 Sanjeev Thiyagarajan 的 19 小时 API 课)。Flask 作为备选。然后学 **Docker** 基础和一个云(AWS/GCP/Azure 免费额度)——把一个服务真正公开部署出去。

**(E)做演示用的前端** —— 会一点 React,能搭个 dashboard 就行;**Streamlit** 或 **Gradio** 是最快把 LLM 应用包成 UI 的方式(下面大多数 LLM 课程都会教)。

**(F)LLM/AI 应用技能(现在是核心):**
- **DeepLearning.AI 短课**(免费/低价):"Building Agentic RAG with LlamaIndex"、"Knowledge Graphs for RAG"(配 Neo4j)、"Functions, Tools and Agents with LangChain"、"Building and Evaluating Advanced RAG"、"Evaluating and Debugging Generative AI"。
- **免费 RAG 路线**(Turing Post 整理):Activeloop 的 LangChain+LlamaIndex 课、DeepLearning.AI 的 agentic/多模态 RAG、Duke(Coursera)实战项目、Google Cloud Vertex AI RAG、Weights & Biases 的 "RAG++: From POC to Production"。
- **IBM "Fundamentals of AI Agents Using RAG and LangChain"**(Coursera,可免费旁听)。
- 向量数据库:Chroma、FAISS、Weaviate、Qdrant、Pinecone。评测:搭一套 **LLM-as-Judge** 评测体系并带回归测试(据多个指南,这是 2026 年 FDE 面试里权重最高的单项技能)。Agent:LangGraph、LangChain、CrewAI、OpenAI Agents SDK;MCP(Model Context Protocol)servers。
- 国内专属:小林 coding 的免费 AI 面试题站(xiaolinnote.com)覆盖 Agent/RAG/LLM 工具链面试题;牛客网 niumianoffer.com 的 AI 题库。

**(G)系统思维 & 在陌生代码库里 debug** —— 通过给开源项目提 PR(找 "good first issue" 标签)、复现并修 bug、读大型仓库来练。这是会被明确考察的(Palantir 的重构/debug 轮;有阿里面试官据说会丢给候选人一个带活 bug 的 GitHub 仓库,要求 10 分钟内定位)。

### 4. 软技能 / 客户面向能力

- **需求收集 & 干系人管理:** FDE 面试第一大失败点是"还没界定清楚范围就急着给方案"。练习开口先问:"在动手设计之前,你会问客户哪些问题?"把 干系人 → 成功指标 → 数据源/约束 → 方案(带明确取舍)→ 失败模式 串起来。
- **把业务问题翻译成技术方案:** 学 To-B(B 端)业务分析(知乎上 B 端业务调研的中文指南:组织架构 → 经营策略 → 整体流程 → 详细流程)。
- **演示 & 技术讲故事:** OpenAI 的带回家作业要求 **录一段视频讲解**——反复练"如何向非技术听众解释你的技术决策"。行为面用 "STAR" 结构。
- **应对模糊性:** 这是 OpenAI/Anthropic 的明确门槛("在模糊中也能干得好"、"high agency / 高自驱")。资源:技术写作与沟通;Palantir 公开的 "Navigating Open-Ended Questions" 指南。

### 5. 面试准备(真实流程 & 真题)

**Palantir FDE 流程:** 招聘官初筛(30 分钟,重在筛"使命认同"——你要能讲出对 Palantir 政府/国防业务的真实看法,别给"问题很有意思"这种表面答案)→ 线上笔试(约 90 分钟:编程 + SQL + 一道 REST-API 任务,做分页和数据处理)→ 虚拟现场 3–5 轮,从以下里选:**Decomposition(招牌轮)**——把一个模糊命题(如"为伦敦设计一个出租车调度系统"或"医院病房分配")拆解成数据模型、API 契约、逻辑,不写代码;**Re-engineering/debug 轮**——在 80–250 行代码里找 bug;**编程轮**(60 分钟 CodePair,图/DP/树,中间穿插约 20 分钟行为面);**系统设计轮**;外加 FDE 专属的 **客户场景轮** → 用人经理终面。行为面贯穿每一轮;ownership(主人翁意识)和使命认同是硬性要求。全程约 3–4 周。

**OpenAI FDE 流程(目前核实度最高,gaijineer.co 有第一人称记录):** 招聘官初筛(30 分钟,"为什么专门要做 FDE?")→ **约 5 小时的带回家作业**,基于 OpenAI 的 API 构建,**外加一段录屏讲解**(当作一次客户演示来对待)→ 60 分钟技术面深挖作业(例如"你会怎么排查 LLM 推理管道里的高延迟?")→ 虚拟现场(3 场约 3–4 小时):用人经理(模糊性、向非技术干系人解释局限)、**方案设计**(开放式客户场景——面试官会逼问"动手设计前你会问客户哪些问题?")、技术深挖(RAG 的 embedding/分块/检索/重排、微调取舍、护栏;"你怎么知道你的 AI 系统真的工作得好?")。全程约 3 周。OpenAI 官方面试指南:终轮 = "4–6 小时、4–6 人、1–2 天",不靠学历背书。(注:有聚合站声称固定"7 轮",未经证实。)

**Anthropic FDE/Applied AI:** 官方岗位确认 FDE 构建生产级 Claude 应用,并交付 "MCP servers、sub-agents 和 agent skills"。编程筛用 **CodeSignal**(IGotAnOffer 给的例子:内存版 KV 数据库、可扩展的银行系统、带约束的文件缓存、模拟云数据库);高分"必要但不充分"。Anthropic 的候选人 AI 使用指南:带回家作业默认不许用 AI,除非题目写明 "You may use Claude for this coding challenge";现场面试不许用 AI;常做 2 次背景调查;非常看重价值观/使命认同(去读他们的 Core Views on AI Safety / Responsible Scaling Policy)。(独立的"客户对话模拟"轮是合理的、也符合岗位,但只出现在未经证实的聚合内容里。)

**真实的 FDE 案例/拆解题(广泛流传,源自 Palantir 风格):**
- "某大城市想缩短 911 急救响应时间。他们有报警数据、交通数据、救护车 GPS 数据。给你 60 分钟,开始。"
- "一家物流公司想要一个 AI Agent 来自动处理货运改道……你会怎么搭一套评测体系,既保证 Agent 不在运费上超支,又维持 99% 的送达率?"
- "一家区域性银行想把三套通过并购得来的遗留系统的反欺诈能力统一起来。所有数据的标注口径都不一致。头 90 天你会怎么界定范围?"
- "一个医疗客户部署了你们的 AI 平台,90 天后采用率只有 12%。他们怪产品不行。你怎么办?"
- "为一个客户 CRM 和你们平台的 API 设计集成。客户用 OAuth 1.0,你们用 OAuth 2.0。"

**LeetCode 难度:** 中等–困难;重点放在 图/BFS-DFS、树、动态规划、堆、滑动窗口、哈希表;Palantir 喜欢把题目包装成真实场景(解析脏数据、最大并发用户数)。目标约 150–250 题,侧重上述主题。

**国内面试备战(真实渠道):** 牛客网(nowcoder.com——字节/阿里/腾讯面经)、一亩三分地(1point3acres.com——海外 + 国内)、小林 coding(xiaolincoding.com——530+ AI 面试题,RAG/Agent)、LeetCode-CN。国内真实被问到的题更偏:项目深挖("你这个项目上线了吗?多少用户?最大技术挑战是什么?")、RAG("RAG 里最难的是什么?文档切割;怎么解决幻觉?微调和 RAG 区别?")、Agent(ReAct、Reflexion、工具调用失败怎么处理)、手写 SQL,再加上 C++/Java 八股(如相关)。2026 趋势:面试官弱化死记硬背的八股文,重点考真实项目 + 你能不能 hold 住非确定性的 LLM 系统。

### 6. 作品集 / 项目

各家 FDE 招聘指南的共识:**做一个完整、公开、有生产意识的作品**(而不是一堆玩具 demo),展示完整闭环——调研 → 架构 → 部署 → 评测 → 运维,并配一份 **架构决策记录(ADR)** 说明成本/延迟/隐私上的取舍。要包含:线上云部署 + API 端点 + 鉴权 + 日志;CI/CD + 测试 + 错误处理;一个真实数据库,理想情况下还有队列/流;对 AI 项目还要有向量数据库 + 检索策略 + 一套 **带回归测试的评测体系**;理想情况下再加一个 **MCP server 集成**。

**具体项目点子(就做这些):**
1. **企业级 RAG"和你的文档对话"** —— 摄取脏 PDF/CSV,分块 + embedding(Chroma/FAISS),检索 + 重排 + 引用标注,FastAPI 后端,Streamlit/Gradio UI,部署到云上,带一套 LLM-as-Judge 评测。用 DeepSeek/OpenAI API。
2. **客服 / 工作流 Agent** —— 多步工具调用的 Agent(LangGraph 或 OpenAI Agents SDK),会调外部 API + 数据库,带护栏和可观测性(延迟/成本/质量看板)。
3. **脏数据集成管道** —— 一个 ETL,摄取口径不一致的客户数据(解析坏日期、去重、归一化),写入 SQL,暴露一个查询 API;对标 Palantir Foundry 风格的工作。
4. **MCP server + sub-agent** —— 完全对应 Anthropic 的交付物形态。

每个项目都配 README、ADR、一段 3–5 分钟录屏讲解(直接演练 OpenAI 的带回家作业),并用业务影响来包装表达。

### 7. 简历 & 投递策略

- **简历:** 开头突出生产部署、客户成效、RAG/评测系统、跨职能 ownership;Python/TypeScript + 一个云;塞入精确匹配的岗位名("Forward Deployed Engineer"、"Solutions Engineer"、"实施/交付/解决方案工程师")。量化(延迟降低 X%、采用率 Y%)。
- **投递渠道(美国/全球):** 公司招聘页(openai.com/careers、Anthropic 的 Greenhouse、scale.com/careers、Glean/Decagon 的 Greenhouse 招聘板)、FDE 专门招聘板 fwddeploy.com、LinkedIn、YC 的 Work at a Startup。H-1B 追踪:h1b-connect.com。
- **投递渠道(国内):** BOSS 直聘(zhipin.com)、猎聘(liepin.com)、公司官网(火山引擎 volcengine.com/jobs、MiniMax minimaxi.com/careers、字节 jobs.bytedance.com)、牛客内推。
- **约 6 个月冲美国 —— 签证现实:** 中国候选人需要 H-1B(年度抽签,约 3 月注册,10 月 1 日入职)或 O-1/L-1/cap-exempt 路径。**OpenAI 和 Anthropic 明确表示提供签证赞助**(Anthropic 原话:"我们确实赞助签证!但并非每个岗位、每个候选人都能成功办下来")。实务提醒:很多政府/国防类 FDE 岗位(Palantir 政府线、OpenAI for Gov、Deloitte-OpenAI)要求美国工作身份/安全许可,**不会**赞助签证——要瞄准商业/企业 FDE 团队。现实的 6 个月美国计划 = 现在就开始做作品集 + 面试那些会赞助的岗位,并对 H-1B 时间线有预期;也可以考虑先进入该公司的非美国办公室(OpenAI 在东京/新加坡/伦敦/都柏林/慕尼黑/巴黎/悉尼都有 FDE 岗),再内部转岗。

---

## 详解:分阶段课程

**第 0 阶段 —— 打基础 & 修好"API 调不通"(第 1–4 周)**
- CS50P/CS50x 打 Python 深度;Git/GitHub。
- Real Python 的 requests + REST 指南;先对 JSONPlaceholder 调通,再对 DeepSeek 调通(`pip install openai`,设 base_url + key)。处理鉴权、JSON、错误、重试。*产出:* 一个能调 LLM API、解析 JSON、并处理失败的小脚本。

**第 1 阶段 —— 核心技术(第 5–12 周)**
- SQL(CS50 Databases)、用 pandas 处理脏数据、ETL 基础。
- FastAPI(官方 + freeCodeCamp),搭并部署一个 CRUD API;Docker;一个云的免费额度。*产出:* 项目 #3(脏数据集成管道)。

**第 2 阶段 —— LLM/AI 应用技能(第 13–22 周)**
- DeepLearning.AI 的 RAG/Agent/评测短课;向量数据库;LangGraph/OpenAI Agents SDK;MCP。
- *产出:* 项目 #1(RAG)和项目 #2(Agent),都带评测体系、ADR、录屏讲解。

**第 3 阶段 —— 客户面向能力(持续进行,第 13–26 周)**
- 练需求收集、演示讲故事、应对模糊性。录演示视频。学 B 端业务分析。

**第 4 阶段 —— 面试准备(第 20–28 周)**
- LeetCode 中等–困难(图/DP/树/堆/滑动窗口)、SQL 刷题、REST-API 编程任务。
- 用上面的真实题目做拆解/案例轮模拟;重点练客户同理心轮 + LLM 系统设计轮(这两个是最常见的失败点)。
- 国内:刷牛客/一亩三分地/小林 coding 题库;准备项目深挖 + RAG/Agent 问答。

**第 5 阶段 —— 投递(第 24 周起)**
- 国内优先,现在就投(BOSS 直聘/猎聘/内推,瞄准交付/解决方案/大模型应用岗)。同时并行投外企/跨国公司。
- 美国:投会赞助签证的商业 FDE 团队;对齐 H-1B 时间线;把非美国办公室当作入口。

---

## 建议(分阶段,带通过门槛)

1. **现在 → 第 1 个月:** 修好 API 集成。进阶门槛:你能独立写出一个脚本,完成鉴权、调 DeepSeek/OpenAI、解析 JSON、用退避处理 429。*如果两周后还卡住,就从裸 `requests` 换成官方 SDK + Postman 来定位问题。*
2. **第 2–3 个月:** 交付项目 #3(数据管道 + API,已部署)。门槛:它在线运行、上了 GitHub、有测试和 README。
3. **第 4–6 个月:** 交付项目 #1 和 #2(RAG + Agent,带评测体系、ADR、录屏讲解)。门槛:一套 LLM-as-Judge 评测体系,至少 1 个回归测试。**这是让你具备面试国内 AI 应用/交付岗资格的关键关卡。**
4. **第 5 个月起(国内优先):** 一边收尾项目,一边开始投国内交付/解决方案/大模型应用岗;用内推。投递门槛:2 个已部署项目 + 约 100 道 LeetCode 中等题。
5. **第 6 个月(美国/外企):** 开始投外企/跨国公司 + 美国会赞助签证的商业 FDE 团队;如果已有赞助方在推进,就在 3 月窗口注册 H-1B。要在前沿实验室有竞争力的门槛:3 个扎实项目、一个 MCP 集成、能流利应对客户场景题、英文演示流利。*如果到 H-1B 截止前美国 offer 还没着落,就瞄准 OpenAI/Anthropic 的非美国办公室(东京/新加坡/伦敦)作为转岗入口。*
6. **决策触发条件:** 如果国内进展很快,就先攒 1–2 年真实的交付/解决方案经验——这会大幅增强日后冲美国的竞争力(西方 FDE 岗偏好 3+ 年客户面向经验)。如果你在编程面试上卡住,就把精力从"求广"转向 LeetCode + 系统设计。

## 注意事项

- **薪资数字** 是时点数据(多为 2026 年中),来自 Levels.fyi、Glassdoor、6figr、公开招聘信息,以及综合行业报告(Bloomberry/Revealera、Perspective AI、DigiTech Bytes)——区间仅供参考,不构成保证;前沿实验室那些以股权为主的数字取决于估值/流动性。
- **需求增长数字** 因来源和时间窗不同而异:Indeed/Business Insider 称同比 729%(2025 年 4 月→2026 年 4 月);Bloomberry 称 1,165%(2025 年 1–10 月);ICONIQ 称约 12 倍(2024 年初→2025 年 4 月)。都指向同一个爆发趋势,只是基线不同。
- **面试流程细节:** OpenAI FDE 流程很大程度依赖一份可信的第一人称记录(gaijineer.co);关于固定"7 轮"以及 Anthropic 独立"客户对话模拟"轮的说法来自 SEO 聚合站,**未经证实**。已确认的官方事实:岗位确实存在,OpenAI 用约 5 小时 API 带回家作业 + 视频,Anthropic 用 CodeSignal 并赞助签证。
- **国内薪资数据** 噪声更大(CSDN/知乎/招聘聚合);FDE 对应岗位的命名(交付/解决方案/实施/大模型应用)很分散,薪资因公司层级和出差强度差异巨大。
- **签证风险:** 6 个月冲美国的时间线受 H-1B 抽签(不确定)制约,且很多高知名度 FDE 岗属政府/国防、不赞助签证。请按"国内优先、美国作为 6–18 个月的中期目标"来规划。
- 一些被引用的备考/培训站(fde.academy、schoolofcoreai、sundeepteki、paraform)是商业站点;它们的*事实*与官方来源吻合,但把它们的课程当作可选、而非必需——上面的免费资源已经足够。
