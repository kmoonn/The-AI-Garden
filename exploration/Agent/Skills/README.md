# Agent Skills 

开放标准（open standard）

Agent **Skills** 定义“**能力**”，**MCP** 提供“**工具**”，**A2A** 实现“**协作**”。

![](https://image.kmoon.fun/20260202-504145.png)

>引用：https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

核心目标：封装与复用“怎么做”的专业知识和流程

核心定位：可复用的业务技能包

解决问题：技能固化、prompt 冗长、缺乏专业流程

MCP 急加载：连接建立后，请求返回所有 tool，立即加载到上下文

Skills 懒加载：先加载元数据，根据用户请求匹配技能，加载完整文档，按需加载脚本

## 优势

- 渐进式披露

先给目录，再分章节，最后附上详细附录。

在处理特定任务时，无需一次性将某个技能的全部内容读入上下文窗口。

解决了 **Token 浪费、上下文干扰**问题。

- LLM不是万能的

有些操作（输入输出明确）还是交给传统代码来执行更合适。

很多实际应用需要确定性的可靠结果，而这只有代码才能保证。

## Skills 结构

```markdown
skill-name/
|—— SKILL.md    # 必需
|—— references/
|   |—— api-doc.md
|   |—— best-practices.md
|—— examples/
|   |—— example1.java
|—— scripts/
|   |—— process.py
```

核心是需要写 SKILL.md。

![](https://image.kmoon.fun/20260202-556439.png)

必需字段:
- name - 技能的名字（小写字母、数字、下划线）
- description - 技能功能和使用场景描述，帮助AI判断何时使用

## 价值

Agent Skills 是一个从单体架构到微服务 ，从过程式脚本到组件化框架转型的标准化接口。

定义了一种可组合、可复用的 “能力单元” 设计范式。

Skills 就像单体模型的**包管理器**（Skill 生态）
