# 回复批注（@eduwork/dsh-annotation）

> 选中回复里的文字加批注，编号回挂到原回复，并随下一条问题一起发送。
>
> Select text in a finished reply, annotate it, keep numbered anchors, and send them with your next question.

## 功能

复用 DSH 原生 composer 引用、草稿保存与发送机制，不引入第二套输入框；批注以编号锚点显示在原回复底部，可编辑、可删除。

## 安装

```bash
# 在 DSH 中把本目录作为本地 bundle 安装（绝对路径）
```

安装后由 DSH 插件系统加载，条目 id 为 `dsh-annotation`。

## 依赖

- `@deepseek-ai/dsh-client-ui-primitives`
- `@deepseek-ai/dsh-client-ui-conversation`
- `@deepseek-ai/dsh-client-ui-input-trigger`
- `react`
- `@deepseek-ai/dsh-client-ui-chat`

## 兼容性

- `engines.dsh`: `>=0.2.1 <0.3.0`
- 与 EduWork 发行版同源，来源于 ECNU/EduWork 仓库。

## 许可

MulanPSL-2.0 AND MIT（与上游 EduWork 一致）。

## 入口修正


- 移除悬空声明：files: docs/**/*（目录不存在）
