# Canvas2Note

一个面向 Codex 的中文 skill，将 Canvas 课程资料增量归档到 OneDrive，并为新 lecture 生成带课件原图的 Notion 详细笔记。

## 工作流

1. 发现本学期所有选课的可访问教学附件，核查遗漏。
2. 比较来源、版本与内容哈希，将新增资料按课程及 lec、lab、tut 等分类归档。
3. 为新增或待完成 lecture 创建或补全分层 Notion 笔记，展开原理、推导、示例、概念辨析与自检，在对应知识点插入原课件示意图。
   可参考已归档 final past papers 调整讲解深度，但不在笔记中标出考点或出题记录；用户要求时也可复审深化旧笔记，保留个人稿件与批注。详见 [笔记质量与复审](references/note-quality.md)。
4. 验证归档和笔记，保存续跑状态，仅清理本次产生的临时文件。

这是供 agent 执行的工作流说明，不是独立爬虫或后台服务。需要可用的 Canvas、Notion 访问方式及本地 OneDrive 目录；执行时仍需遵守登录、授权和工具能力限制。

## 使用前配置

参照 [目标配置说明](references/targets-template.md) 提供 Canvas 地址、学期、OneDrive 路径和 Notion 学期父页。个人映射可保存在仅供本机使用、已被 Git 忽略的 `references/personal-targets.md`。

技能入口为 [SKILL.md](SKILL.md)，显示元数据位于 [agents/openai.yaml](agents/openai.yaml)。安装后的调用示例：

> 使用 $canvas2note 同步本学期课件和笔记。

公开仓库仅包含技能说明与配置模板，不包含个人路径、Notion 页面 ID、课件、笔记或同步状态。不会自动创建定时任务，也不会静默覆盖已有资料或整页替换用户笔记。
