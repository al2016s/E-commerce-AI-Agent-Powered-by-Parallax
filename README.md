# E-commerce-AI-Agent-Powered-by-Parallax
一个基于 Parallax 框架构建的、注重隐私保护的本地化跨境电商 AI 客服智能体。
# 🛍️ Secure Cross-Border E-commerce AI Agent (Powered by Gradient Parallax)
# 基于 Parallax 的跨境电商隐私保护 AI 客服

> 🌍 **A privacy-first, locally deployed AI customer service agent for high-ticket furniture e-commerce.**
>
> 🔒 **一个基于 Parallax 框架构建的、注重隐私保护的本地化跨境电商 AI 客服智能体。**

<img width="3840" height="2160" alt="Untitled_01" src="https://github.com/user-attachments/assets/18c67422-6de5-40b1-ac15-854f68aacced" />

## 📖 Introduction (项目简介)

This project demonstrates a **fully local AI customer support solution** designed for cross-border e-commerce businesses. It leverages **Gradient Network's Parallax framework** to run the Qwen3 model effectively on consumer hardware (Mac mini).

本项目展示了一个专为跨境电商业务设计的**全本地化 AI 客服解决方案**。利用 **Gradient Network 的 Parallax 框架**，我在消费级硬件（Mac mini）上成功运行了 Qwen3 模型。

### The Core Problem (痛点)
In the high-ticket furniture market, **data privacy is paramount**.
* **Supply Chain Risks**: Relying on public cloud LLMs risks leaking product selection logic. In China, supply chains (e.g., 1688) are transparent, and data leaks can lead to immediate copycats.
* **Cost Control**: Traditional AI APIs can be costly for high-volume inquiries.

**跨境电商（特别是高客单价家具）最怕什么？**
* **怕泄露**：云端大模型可能存在数据隐私风险。国内供应链透明，一旦选品被同行通过数据分析摸透，很容易被跟卖复制。
* **成本高**：商业 API 调用成本随着咨询量增加而增加。

**Solution**: By deploying locally with Parallax, we ensure data stays local to protect business privacy, while automatically handling 80% of pre-sales and after-sales inquiries to reduce customer service workload.
**解决方案**：通过 Parallax 实现本地部署，确保数据不出本地，保护业务隐私，拦截 80% 的售前售后咨询，降低客服工作压力。

---

## 🚀 Tech Stack (技术栈)

* **Inference Engine (推理引擎)**: [Gradient Parallax](https://github.com/GradientHQ/parallax/)
    * Running **Qwen3-0.6B**. The core distributed AI framework that breaks hardware limits.
    * 运行 **Qwen3** 模型。Gradient 的去中心化分布式框架，打破单机硬件瓶颈。
* **Embedding Engine (向量引擎)**: [Ollama](https://ollama.com/)
    * Running **Qwen3-Embedding-4B** for RAG.
    * 运行 **Qwen3-Embedding-4B** 模型用于处理知识库的向量化。
* **Orchestration (工作流编排)**: [Dify](https://dify.ai/)
    * Workflow & Knowledge Base Management.
    * 用于集成模型与搭建客服工作流。
* **Hardware (硬件)**: Mac mini M4 16GB/256GB

---

## 🛠️ Architecture & Workflow (架构与工作流)

1.  **Parallax Node**: Acts as the local LLM provider, utilizing distributed computing to run complex models efficiently.
2.  **Ollama**: Converts the "Furniture Q&A Knowledge Base" into vector embeddings.
3.  **Dify**: Connects the Parallax LLM and Ollama Embeddings to build the chat interface.

**工作流逻辑：**
1.  **Parallax 节点**：作为本地 LLM 提供商，利用分布式计算高效运行复杂模型。
2.  **Ollama**：将“家具问答知识库”转化为向量数据。
3.  **Dify**：连接 Parallax 的大模型能力和 Ollama 的知识库，构建最终的聊天界面。

<img width="3838" height="1936" alt="image" src="https://github.com/user-attachments/assets/1f1b23d3-b2ae-44b5-a1ef-b7f9df53288f" />

*(Screenshot: Dify orchestration flow / Dify 工作流编排界面)*

## ⚡️ Execution Log & Implementation Process (运行过程记录)

*This section records the actual steps I took to deploy the system on my Mac mini.*
*本节记录了我在 Mac mini 上部署该系统的实际操作步骤。*

### Step 1: Running Parallax Framework (启动 Parallax 框架)
I used the VS Code terminal to initialize the Parallax framework and loaded the **Qwen3-0.6B** model as the primary inference engine.
我使用 VS Code 命令行工具初始化了 Parallax 框架，加载 **Qwen3-0.6B** 模型作为主要推理引擎。

```bash
# The exact command I used / 我实际使用的命令
parallax run 
parallax join
```

<img width="3840" height="2110" alt="image" src="https://github.com/user-attachments/assets/e78b9190-3fe6-4990-9a4e-4d42e8cb2975" />
(Screenshot: Parallax node running successfully in VS Code / 截图：Parallax 节点在 VS Code 中成功运行)


<img width="3838" height="2110" alt="image" src="https://github.com/user-attachments/assets/d4f1594e-371d-4517-a25b-5c7e1fc74cbd" />
(Screenshot: Parallax node running successfully in VS Code / 截图：Parallax 节点在 VS Code 中成功运行)

### Step 2: Preparing Embedding Model (准备向量模型)
To ensure the knowledge base (RAG) works efficiently with Chinese context, I used Ollama to run the qwen3-embedding:4b model.
为了确保知识库（RAG）在中文语境下高效工作，我使用 Ollama 运行了 qwen3-embedding:4b 模型。

```bash
# I pulled the embedding model for vectorization / 我拉取了用于向量化的模型
ollama pull qwen3-embedding:4b
```

<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/1c7aa80d-2f81-4940-95c1-569dc35e5205" />
( Screenshot of Ollama terminal / Ollama 终端运行截图)

### Step 3: Dify Integration & Workflow Setup (Dify 集成与工作流搭建)
Finally, I connected the components within Dify. This involved pointing the model provider to my local Parallax endpoint, uploading the business knowledge base file, 和 configuring the orchestration workflow.
最后，我在 Dify 中完成了组件连接。这包括将模型供应商指向我的本地 Parallax 端点，上传业务知识库文件，并配置编排工作流。

**My Configuration Steps (我的配置步骤):**

1.  **Model Provider (模型供应商)**:
    In Dify settings, I added an "OpenAI-API-compatible" provider by configuring the API endpoint to point to the local Parallax node, enabling the connection to the **Qwen3-0.6B** model. I also added the **Ollama embedding** model.
    **模型供应商**：在 Dify 设置中，我添加了一个 "OpenAI-API-compatible" 供应商，通过设置接口地址指向本地 Parallax 端点，这样我可以连接 **Qwen3-0.6B** 模型。同时我添加了 **Ollama** 的 embedding 模型。
<img width="3838" height="1926" alt="image" src="https://github.com/user-attachments/assets/14b225e7-b5c9-488d-b5aa-b2554d7d70ae" />
<img width="1758" height="870" alt="image" src="https://github.com/user-attachments/assets/949341be-8a0f-42c9-b125-eded45fd79b2" />


3.  **Knowledge Base (知识库)**:
    I uploaded the `澳洲客服指引.md` (Australian Customer Service Guide) file. This document covers comprehensive business data regarding pre-sales, mid-sales, 和 after-sales, including materials and shipping policies.
    **知识库**：我上传了覆盖售前、售中、售后，有关材质和发货政策等业务数据的 `澳洲客服指引.md` 文件。
<img width="3840" height="1932" alt="image" src="https://github.com/user-attachments/assets/99e09ff1-40e9-4cb6-8aa3-c12243782f27" />

4.  **Prompt Engineering (提示词工程)**:
    I designed a system prompt to ensure the AI acts as a professional, privacy-conscious customer service representative.
    **提示词工程**：我设计了系统提示词，确保 AI 扮演一个专业且注重隐私的客服代表。
<img width="878" height="966" alt="image" src="https://github.com/user-attachments/assets/b0767c32-a14c-4cf2-b8ff-30f242fe3a99" />


6.  **Workflow Orchestration (工作流编排)**:
    I set up the overall workflow in several steps: User queries are first processed through **Knowledge Base Retrieval**. Then, the **Qwen3-0.6B** model generates a response using the retrieved data. Finally, I added a **Code Node** to hide the "thinking process" (Chain of Thought) to improve the frontend user experience.
    **工作流编排**：我设置了整体的工作流，分为几步：客户的问题先通过**知识库检索**，使用 **Qwen3-0.6B** 模型结合检索到的数据进行回答。最后，为了前端体验，我添加了一个**代码节点**来隐藏模型的思考过程。

<img width="3840" height="1932" alt="image" src="https://github.com/user-attachments/assets/2a9dcc95-6e4b-48ce-bcfe-1ebe5c1cc037" />

*(Screenshot: Dify model provider configuration connecting to Parallax / 截图：Dify 连接到 Parallax 的模型配置界面)*

---

## 📊 Demo & Results (演示与效果)

Here is the actual performance of the agent running on my Mac mini. It successfully retrieved business knowledge from the local knowledge base without leaking data to the cloud.
这是智能体在我的 Mac mini 上运行的实际表现。它成功从本地知识库中检索了业务知识，且没有将数据泄露到云端。

<img width="3838" height="1932" alt="image" src="https://github.com/user-attachments/assets/e2169dc7-f21a-4bbe-9cff-038402f80f41" />

*(Screenshot: Final conversation interface showing the agent solving a problem / 截图：最终对话界面，展示智能体解决问题)*

---

## 🏆 Gradient Network Campaign Submission

This repository is a submission for the **Gradient Network Campaign**.

It documents my journey of building an **Intelligent AI Customer Service Agent** using **Parallax**. By running the **Qwen3-0.6B** model on a distributed edge network (my local device), I successfully **reduced customer service burden while ensuring business privacy**。

本仓库是 **Gradient Network Campaign** 的参赛作品。
它记录了我使用 **Parallax** 构建**智能 AI 客服应用**的过程。通过在分布式边缘网络（我的本地设备）上运行 **Qwen3-0.6B** 模型，我成功**降低了客服工作负担，同时确保了业务隐私**。

## 👤 Author (作者)

**Echo**
* 🛍️ Cross-border E-commerce Practitioner / 跨境电商从业者
* 🤖 AI & Web3 Enthusiast / AI 与 Web3 爱好者
