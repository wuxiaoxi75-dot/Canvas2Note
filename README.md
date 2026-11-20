# Canvas2Note

一个面向 Codex 的中文 skill，将 Canvas 课程资料增量归档到 OneDrive。新 lecture 的课件 PDF 交给 Poe NoteTakerShenxu 起草，再由 agent 核对、配图与补高亮，发布为 Notation 详细笔记。

## 工作流

1. 发现本学期所有选课的可访问教学附件，核查遗漏。
2. 比较来源、版本与内容哈希，将新增资料按课程及 lec、lab、tut 等分类归档。
3. 按 [Poe 草稿流程](references/poe-drafting.md) 为尚未建页的 lecture 起草；逐页复核后补齐解释、高亮、原课件示意图与真实代码效果图，按 [Notation 发布与排版](references/notation-publishing.md) 落版。
   可参考已归档 final past papers 调整讲解深度和行内强调，不标注考点或出题记录；用户要求时也可复审深化旧笔记，保留个人稿件与批注。详见 [笔记质量与复审](references/note-quality.md)。
4. 验证归档和笔记，保存续跑状态，仅清理本次产生的临时文件。

这是供 agent 执行的工作流说明，不是独立爬虫或后台服务。需要可用的 Canvas 会话或连接器、已连接的 Notation Codex 插件及本地 OneDrive 目录。新讲次还需要可向指定 Poe Bot 发送课件 PDF 的途径；选择 API 时，运行环境缺少 `POE_API_KEY` 就通过安全渠道向用户请求配置。

## 使用前配置

参照 [目标配置说明](references/targets-template.md) 提供 Canvas 地址、学期、OneDrive 路径和 Notation 学期父页标题或 ID。个人映射可保存在仅供本机使用、已被 Git 忽略的 `references/personal-targets.md`。

技能入口为 [SKILL.md](SKILL.md)，显示元数据位于 [agents/openai.yaml](agents/openai.yaml)。安装后的调用示例：

> 使用 $canvas2note 同步本学期课件和笔记。

公开仓库仅包含技能说明与配置模板，不包含个人路径、Notation 页面 ID、课件、笔记或同步状态。不会自动创建定时任务，也不会静默覆盖已有资料或整页替换用户笔记。
