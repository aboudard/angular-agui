# server

NestJS application exposing an **AG-UI endpoint** (`POST /agent`, Server-Sent Events).
Scaffolded in **Step 1**.

The endpoint delegates to an `AgentRunner` abstraction:

```ts
interface AgentRunner {
  run(input: RunAgentInput): Observable<BaseEvent>;
}
```

| Implementation      | Used in    | Description                                   |
|---------------------|------------|-----------------------------------------------|
| `MockAgentRunner`   | Steps 1–5  | Replays scripted AG-UI event scenarios        |
| `MastraAgentRunner` | Steps 6+   | Real Mastra agent backed by OpenAI            |

The implementation is selected through dependency injection (environment variable `AGENT_RUNNER=mock|mastra`).
Controller and front end stay unchanged when switching — demonstrating that AG-UI is backend-agnostic.
