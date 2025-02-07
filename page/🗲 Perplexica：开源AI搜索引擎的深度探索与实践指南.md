# 🗲 Perplexica：开源AI搜索引擎的深度探索与实践指南

## 📚 内容导览
- [核心功能解析](#核心功能解析)
- [系统部署指南](#系统部署指南)
- [进阶应用方案](#进阶应用方案)
- [社区支持计划](#社区支持计划)

## 🌐 核心功能解析
Perplexica作为基于AI的元搜索引擎，完美融合检索增强生成技术（RAG）与语义关联分析，通过以下创新功能重塑搜索体验：

### 架构优势
- **实时索引机制**：基于SearxNG元架构建立动态信息抓取系统，规避传统AI引擎的静态知识库时效性痛点
- **混合推理模式**：整合相似度分析+语义嵌入技术，构建三维检索验证体系

### 主要功能亮点
1. **双模智能检索**
   - 常规模式：快速响应查询需求
   - 进阶模式（开发中）：深度遍历网页资源

2. **垂直场景适配**
   | 场景模式         | 功能定位              |
   |------------------|-----------------------|
   | 学术研究         | 期刊论文精准溯源      |
   | 视频解析         | YouTube内容定向抓取  |
   | 社区洞察         | Reddit舆情分析        |
   | 数值计算         | Wolfram Alpha集成     |

3. **AI模型兼容性**
   - 支持主流LLM接口：Llama3、Mixtral等通过Ollama本地部署
   - 无缝对接云端API：OpenAI/Groq/Anthropic

👉 [野卡 | 一分钟注册，轻松订阅海外线上服务](https://bbtdd.com/yeka)

## 🛠️ 系统部署指南
### Docker推荐方案（5步快速部署）
bash
git clone https://github.com/ItzCrazyKns/Perplexica.git
cd Perplexica
cp sample.config.toml config.toml
# 配置API密钥（选择性启用）
docker compose up -d


### 参数配置要点
- OpenAI/Groq密钥：仅需在启用对应服务时填写
- Ollama设置注意：
  toml
  [OLLAMA]
  url = "http://host.docker.internal:11434"  # Windows/Mac适用
  
- Linux系统需调整防火墙策略，开放11434端口

## 🚀 进阶应用方案
### 浏览器集成配置
1. 访问`chrome://settings/searchEngines`
2. 新增搜索引擎：
   - 名称：Perplexica
   - 关键词：p
   - URL模板：`http://[部署地址]:3000/?q=%s`

### API整合开发
提供标准化接口支持：
python
import requests

def perplexica_search(query, mode='all'):
    params = {'q': query, 'focus_mode': mode}
    return requests.get('http://localhost:3000/api/search', params=params)


## 🤝 社区支持计划
- 开发者可通过GitHub Issues提交功能建议
- 项目进展追踪：定期查看[版本更新日志](https://github.com/ItzCrazyKns/Perplexica/releases)
- 用户交流群组：Discord技术讨论社区（搜索`itzcrazykns`加入）

> 提示：项目的持续优化需要社区力量支持，欢迎通过GitHub Sponsors参与开源共建

![系统预览交互图](https://bbtdd.com/wp-content/uploads/img/1733563429.webp)

👉 [野卡 | 开发者首选全球支付解决方案](https://bbtdd.com/yeka)