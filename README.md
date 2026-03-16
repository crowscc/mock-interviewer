# Mock Interviewer - AI 模拟面试官

基于你的简历（可选配合 JD）进行深度模拟面试练习的 AI 技能。支持 6 种不同级别的面试官角色，通过动态追问、压力测试和苏格拉底式教练引导，帮你在实战中提升面试能力。

兼容 [Claude Code](https://docs.anthropic.com/en/docs/claude-code) 和 [OpenClaw](https://docs.openclaw.ai)。

## 核心能力

- **6 种面试官角色** — P7 同级工程师、P8 Tech Lead、P9 架构师、P8 业务负责人、P9 总监、VP/CTO
- **简历 + JD 联合分析** — 自动做匹配度速评，围绕 gap 区域精准出题
- **动态追问** — 根据你的回答实时决定下一个问题，不是照题单念
- **教练模式** — 卡住时随时喊"提示"，苏格拉底式引导帮你找到思路（不给答案）
- **多维度复盘** — 逐题评分（技术深度/表达结构/业务 sense/应变能力）+ level 对标 + JD 匹配度分析

## 快速安装

### Claude Code

**方式一：通过 Marketplace 配置（推荐）**

编辑 `~/.claude/settings.json`，添加：

```json
{
  "extraKnownMarketplaces": {
    "mock-interviewer": {
      "source": {
        "source": "github",
        "repo": "你的用户名/mock-interviewer"
      }
    }
  }
}
```

重启 Claude Code 后即可使用。

**方式二：手动安装**

```bash
# 克隆到任意项目的 .claude/skills/ 目录
git clone https://github.com/你的用户名/mock-interviewer.git
cp -r mock-interviewer/mock-interviewer .claude/skills/mock-interviewer
```

### OpenClaw

**方式一：克隆到 managed skills 目录**

```bash
git clone https://github.com/你的用户名/mock-interviewer.git /tmp/mock-interviewer
cp -r /tmp/mock-interviewer/mock-interviewer ~/.openclaw/skills/mock-interviewer
```

**方式二：通过 extraDirs 配置**

```bash
# 克隆仓库
git clone https://github.com/你的用户名/mock-interviewer.git ~/skills/mock-interviewer

# 编辑 ~/.openclaw/openclaw.json，添加到 skills.load.extraDirs
```

```json
{
  "skills": {
    "load": {
      "extraDirs": ["~/skills/mock-interviewer"]
    }
  }
}
```

## 使用方式

安装完成后，以下任何表达都会自动触发技能：

```
帮我模拟面试，简历在 resume.pdf
我后天面大厂，帮我练练
帮我面一下，用 P8 Tech Lead 视角
我想专门练系统设计
简历上写了带团队但其实经验不多，被问到怎么办
```

也可以同时提供 JD 获得更精准的面试体验：

```
简历在 resume.pdf，JD 在 jd.txt，帮我针对性准备一下
```

### 面试流程

```
启动 → 读简历(+JD) → 选模式 → 选面试官 → 面试循环 → 复盘总评
                                              ↕
                                          教练模式（按需）
```

1. **启动** — 提供简历文件路径，可选提供 JD。技能会输出候选人画像和匹配度速评
2. **选模式** — 完整模拟（~60分钟）或单项专练（~30分钟）
3. **选面试官** — 从 6 种角色中选择，技能会根据你的情况给出推荐
4. **面试循环** — 真实的追问式面试，随时可触发教练模式
5. **复盘总评** — 逐题评分 + 综合评级 + 改进建议 + JD 匹配度分析

### 教练模式

面试中随时说 **"提示"**、**"help"** 或 **"引导我"** 进入教练模式。教练不会给你答案，而是用提问帮你自己找到思路。说 **"继续"** 回到面试。

## 文件结构

```
mock-interviewer/
├── SKILL.md                    # 主技能定义（流程控制 + 行为规则）
└── references/
    ├── 面试官画像.md             # 6 种面试官的人格、视角、提问风格
    ├── 出题策略.md               # 锚点提取、追问模式、JD 分析、压力题库
    └── 评分标准.md               # 四维度评分细则、level 对标特征
```

## 适用场景

- 准备技术面试（后端/前端/全栈/架构/管理）
- 针对特定 JD 做定向准备
- 练习被追问时的应变能力
- 练习行为面试（STAR 框架）
- 模拟不同级别面试官的压力

## License

MIT
