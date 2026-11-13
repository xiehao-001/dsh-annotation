# Response Annotations

`@eduwork/dsh-annotation` · v0.1.5 · MulanPSL-2.0 AND MIT

Response Annotations lets you select text in a finished assistant reply, attach an annotation, keep numbered anchors under that reply, and send the excerpt and comment with your next question. Quoting, draft persistence and sending all reuse the native DSH mechanisms; the plugin adds per-selection comments, numbering and editing.

It is meant for review-style conversations where several passages of a long answer need to be questioned or commented on without copying them into the prompt by hand. The plugin keeps no second conversation or draft store: pending annotations live in the native draft, and sent ones are restored from the user message itself.

## Highlights

- Select text in a completed final reply and choose "Annotate" in the hover bar; the reply keeps a numbered anchor at its bottom.
- Keeps the native quote block in the composer, with an "N annotations" summary; send the question, the annotations, or both.
- Adds UI through the official `conversation.chat.turnTail`, `conversation.input.left`, `conversation.input.overlay` and `conversation.chat.user.decorate` slots.
- Reads pending annotations and their order from the public `InputState.occurrences`, and edits through versioned native input-range operations instead of rewriting the draft.
- On send, host `agent/pre-step` folds segments from the same user message into one fixed prompt, an `<eduwork-response-annotations>` JSON block and the question body; a retry does not wrap twice.
- Restores sent annotations from the structured prefix in the user message and shows "Annotation 1, 2..." above the bubble, while the bubble contains only the question.
- Optional: install `@eduwork/dsh-side-chat@0.1.0` to add "ask in side chat" to the same selection bar; excerpts become unsent annotations in the side chat.

## Install

Install this directory as a local DSH plugin bundle. From a shell:

```bash
dsh plugin --profile web add /absolute/path/to/dsh-annotation
```

Or add the directory through the **Plugins** panel in DSH (local bundle). Restart the DSH app after installation; plugins are activated from the bundle patch (`cordis.patch.yml`).

## Configuration

No configuration keys: the bundle patch inserts the plugin with defaults.

## Requirements

- DeepSeek Harness `>=0.2.1 <0.3.0`
- Node `>=24.18.0`
- Peer packages: `@deepseek-ai/dsh-client-ui-primitives`, `@deepseek-ai/dsh-client-ui-conversation`, `@deepseek-ai/dsh-client-ui-input-trigger`, `react`, `@deepseek-ai/dsh-client-ui-chat`

## Notes and limits

- Numbered anchors are bound to completed final replies only: streaming content, tool output, user input and sidebar files are never annotated.
- An excerpt is a snapshot; new quotes also store the source message ID and up to 320 visible characters before and after the selection, not the full source.
- Hosts without `conversation.chat.user.decorate` fall back to a text card through the official text slot; sent annotations still display, but the in-bubble numbering is unavailable.
- Editing depends on the input facade `draftSnapshot` getter, which is not yet part of the public `SessionInput` type contract; when it is missing or inconsistent, edits are refused and the draft is kept.

## 中文文档

[README.zh-CN.md](./README.zh-CN.md)

## License

MulanPSL-2.0 AND MIT — see [LICENSE](./LICENSE) and, where present, [LICENSE-MIT](./LICENSE-MIT). Extracted from the ECNU EduWork distribution (https://github.com/ECNU/EduWork); upstream copyright and license notices are preserved.
