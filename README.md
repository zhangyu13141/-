阶段 1：基础工具练手（1-2 周）—— 熟悉 LangChain 核心功能
目标：用 LangChain 搭建 “最小可用的 RAG 应用”，掌握文档加载、Embedding、向量数据库、生成串联。

项目示例：“个人知识库问答工具”（如 “上传自己的 CV 笔记，可提问‘目标检测的 mAP 如何计算’，工具自动检索笔记并回答”）。
关键步骤：
文档加载：用 LangChain 的PyPDFLoader加载 PDF 笔记（对应 CV 的 “读取图像数据”）；
Chunking：用RecursiveCharacterTextSplitter拆分文本（测试不同 Chunk 大小：如 500token、1000token，对比检索精度）；
Embedding：用SentenceTransformerEmbeddings（模型选all-MiniLM-L6-v2）将文本转向量（类似 CV 的 “用 ResNet 提取图像特征”）；
向量数据库：用本地Chroma（轻量）存储向量（类似 CV 的 “用 FAISS 存储特征”）；
生成：用ChatOpenAI（或开源的LlamaCpp调用本地 LLaMA-3）+RetrievalQA Chain，实现 “检索 + 生成”；
重点积累：记录 “Chunk 大小、Embedding 模型” 对回答准确率的影响（如 Chunk 太小会丢失上下文，太大则检索精度低），这就是 “RAG 实践经验”
