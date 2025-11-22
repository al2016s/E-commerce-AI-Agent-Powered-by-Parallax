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

