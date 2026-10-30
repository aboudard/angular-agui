# Roadmap

Principle: **AG-UI is the pipe, A2UI is one kind of payload.** We build the pipe first,
then push richer and richer things through it. Real LLM calls only arrive in Step 6:
everything before is driven by a mock runner so the protocol stays fully visible.

Backend architecture: a single **NestJS** app exposes `POST /agent` (AG-UI over SSE) and delegates
to an injected `AgentRunner`. Switching from `MockAgentRunner` to `MastraAgentRunner` is a provider
swap — controller and front end do not change.

| Step | Topic | Backend | Frontend | Demo |
|------|-------|---------|----------|------|
| 0 | Concepts | – | – | `docs/00-concepts.md` |
| 1 | Foundations & raw event stream | NestJS + `MockAgentRunner` (SSE, scripted scenarios) | Angular event inspector | Watch AG-UI events flow live |
| 2 | AG-UI client & streaming chat | Mock | `@ag-ui/client` wrapped in a signals-based service | Token-by-token chat, cancellation |
| 3 | Tool calls & static generative UI | Mock | Tool → component registry, frontend tools | Agent "renders" an incident card |
| 4 | Shared state | Mock (`STATE_SNAPSHOT` / `STATE_DELTA`) | Incident board bound to agent state | Agent and user edit the same board |
| 5 | Human-in-the-loop | Mock (interrupt / resume) | Approval widget in the chat | Approve / reject a remediation action |
| 6 | Real agent | NestJS + **`MastraAgentRunner`** (OpenAI) — provider swap | Unchanged | Same UI, real reasoning |
| 7 | Declarative generative UI | Mastra runner emitting A2UI messages | A2UI Angular renderer | Agent composes a form/dashboard from a catalog |
| 8 | Production & comparison | NestJS + Mastra | Rewrite one demo with **CopilotKit Angular** | Auth, reconnection, errors, tests, observability |

## Where CopilotKit appears

- Steps 1–5: not used (raw protocol on purpose).
- Step 6: not required (Mastra is hosted in NestJS); the CopilotKit runtime is discussed as an alternative bridge.
- Step 7: compared with our own A2UI integration.
- Step 8: front-end SDK, compared with the hand-written version.
