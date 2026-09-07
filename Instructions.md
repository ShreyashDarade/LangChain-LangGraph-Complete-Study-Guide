# LangChain, LangGraph, LangSmith, and Langfuse: feature and library inventory

This inventory separates framework capabilities, platform services, installable libraries, integrations, and legacy components. It covers Python and JavaScript/TypeScript where documented; the two languages do not necessarily have identical capabilities.

**Coverage:** the accompanying catalog records the official documentation indexes, sitemap additions, API references, package registry checks, and retrieval failures. Thousands of pages were retrieved and parsed; the feature lists below are a synthesis of product guides, reference overviews, and selected detailed pages. This is not a claim that every line of every historical document was manually reviewed. Unindexed community packages, private features, transitive dependencies, and future changes cannot be guaranteed complete. Package existence does not prove ownership, maintenance quality, or compatibility with a particular application version.

**Reading the list:** each numbered item is a feature family; the semicolon-separated items enumerate its capabilities. Linked documentation is the source for that family. Features marked beta, legacy, hosted, enterprise, or integration-dependent retain those distinctions. Consult the linked page for exact version and plan requirements.

**Collection results:** 73 index files; 5,695 discovered URLs, consolidated into 5,686 canonical documentation/reference pages; 5,680 successful page retrievals and 6 unavailable links; 105 feature families; 305 package records with both registry and package-specific source evidence; 126 Langfuse HTTP API operations. Python and npm distributions with the same name count separately. All 205 distinct source links in this feature inventory resolved during validation. The six collection failures remain visible in the searchable catalog.

## 1. How the four products fit together

| Product | Main responsibility | Relationship |
|---|---|---|
| LangChain | Model interfaces, application components, configurable tool-using agents | Its current agent implementation uses LangGraph. |
| LangGraph | Stateful orchestration and execution | Can orchestrate custom code and model calls; LangChain is optional for graph design. |
| LangSmith | Tracing, evaluation, prompt/context management, deployment, and additional agent platform services | Supports LangChain/LangGraph and other frameworks. |
| Langfuse | Tracing, evaluation, prompt management, analytics, and an open data platform | A separate project that integrates with LangChain/LangGraph and other frameworks. |

Sources: [LangChain](https://docs.langchain.com/oss/python/langchain/overview), [LangGraph](https://docs.langchain.com/oss/python/langgraph/overview), [LangSmith](https://docs.langchain.com/langsmith/observability), [Langfuse](https://langfuse.com/docs).

## 2. LangChain features

1. **Model interfaces:** provider-independent chat-model invocation; model initialization by provider/name; synchronous and asynchronous calls; batching and concurrency; token streaming; configurable model parameters; local and hosted models; runtime model selection; retries and rate limiting; connection and proxy configuration. [Models](https://docs.langchain.com/oss/python/langchain/models)
2. **Model capabilities:** tool binding and tool choice; provider-native tools; structured responses; model capability profiles; text/image/audio/video content where supported; exposed reasoning content; token accounting; prompt caching; log probabilities where providers expose them. These capabilities vary by model/provider. [Model guide](https://docs.langchain.com/oss/python/langchain/models)
3. **Messages:** system, human, AI, and tool messages; standardized content blocks; provider-native payloads; message metadata; tool-call identifiers and results; usage metadata; stream chunks; serialization and deserialization. [Messages](https://docs.langchain.com/oss/python/langchain/messages)
4. **Prompt building:** string and chat templates; variables and partial variables; conversation placeholders; few-shot examples; example selection; prompt composition and formatting. These lower-level components remain in the core library. [Prompt APIs](https://reference.langchain.com/python/langchain-core/prompts)
5. **Runnable composition:** sequential pipelines; parallel branches; conditional routing; lambda adapters; passthrough and assignment; sync/async invocation, batching, and streaming; configuration binding; fallbacks; retries; callbacks and execution events. [Runnable APIs](https://reference.langchain.com/python/langchain-core/runnables)
6. **Tool construction:** functions/decorators and explicit tool classes; typed input schemas; descriptions; asynchronous tools; structured tool responses and artifacts; error handling; access to runtime context, state, stores, and stream writers; tool-driven state updates. [Tools](https://docs.langchain.com/oss/python/langchain/tools)
7. **Agent execution:** `create_agent`/`createAgent`; repeated model/tool execution; system prompts; configurable state; dynamic model and tool selection; structured final responses; streaming; persistent conversations; custom middleware; integration with graph execution. [Agents](https://docs.langchain.com/oss/python/langchain/agents)
8. **Structured output:** provider-native schema enforcement or tool-call strategy; Pydantic/dataclass/TypedDict/JSON Schema options where documented; validation feedback; retry handling; custom tool messages; handling multiple structured outputs. [Structured output](https://docs.langchain.com/oss/python/langchain/structured-output)
9. **Short-term memory:** thread state; checkpoint-backed conversations; custom state fields; message trimming, deletion, and summarization; memory reads and writes in tools and middleware. [Short-term memory](https://docs.langchain.com/oss/python/langchain/short-term-memory)
10. **Long-term memory:** namespace-organized storage across conversations; lookup and update from tools; semantic retrieval through an appropriately configured store. [Long-term memory](https://docs.langchain.com/oss/python/langchain/long-term-memory)
11. **Context engineering:** modify system prompts, message history, available tools, model selection, response schemas, and tool context at runtime; separate persistent state from per-invocation context; lifecycle hooks for context updates. [Context engineering](https://docs.langchain.com/oss/python/langchain/context-engineering)
12. **Custom middleware:** before/after agent and model hooks; wrappers around model/tool calls; decorator and class implementations; state extensions; ordered composition; conditional jumps; tracing controls; custom stream transformers. [Custom middleware](https://docs.langchain.com/oss/python/langchain/middleware/custom)
13. **Prebuilt middleware:** tool exception handling; tool retries; model retries; model fallbacks; conversation summarization; human review; model/tool call limits; PII handling; task lists; LLM-based tool selection; provider-side tool discovery; shell access; filesystem support; subagent delegation; rubric grading (beta); file search; context editing; simulated tool execution. Some entries are supplied by Deep Agents rather than the minimal LangChain package. [Middleware catalog](https://docs.langchain.com/oss/python/langchain/middleware/built-in)
14. **Guardrails and human review:** deterministic or model-based checks; PII detection and redaction/masking/blocking strategies; custom pre/post execution checks; approve, reject, or edit pending tool actions; conditional approvals; persisted pause/resume; batched decisions. [Guardrails](https://docs.langchain.com/oss/python/langchain/guardrails), [human review](https://docs.langchain.com/oss/python/langchain/human-in-the-loop)
15. **Retrieval building blocks:** documents and metadata; document loaders; transformations; chunking/text splitting; embedding models; vector stores; retrievers; similarity queries and scores; provider-specific filtering and search modes. [Retrieval](https://docs.langchain.com/oss/python/langchain/retrieval), [semantic search](https://docs.langchain.com/oss/python/langchain/knowledge-base)
16. **Retrieval architectures:** fixed two-step RAG; agent-selected retrieval; hybrid RAG; reranking and compression through integrations; query transformation and specialized retrievers in the wider/legacy component ecosystem; SQL and graph-database integrations. [Retrieval patterns](https://docs.langchain.com/oss/python/langchain/retrieval), [integration catalog](https://docs.langchain.com/oss/python/integrations/providers/overview)
17. **Multi-agent patterns:** supervisor/subagents; agent handoffs; routers; on-demand skills; custom workflows; isolated context; synchronous or asynchronous delegation; selecting what conversation data enters and leaves each agent. [Multi-agent guide](https://docs.langchain.com/oss/python/langchain/multi-agent/index), [subagents](https://docs.langchain.com/oss/python/langchain/multi-agent/subagents)
18. **MCP:** connect tools from MCP servers; local/in-process, subprocess, or remote HTTP transports where supported; adapter libraries; MCP tool discovery and conversion. Prompts/resources and authentication support depend on the adapter/API version. [MCP](https://docs.langchain.com/oss/python/langchain/mcp), [adapter reference](https://reference.langchain.com/python/langchain-mcp-adapters)
19. **Streaming:** token/message output; execution progress; custom application updates; multiple stream projections; reasoning/tool-call content; subagent streams; interrupted runs; event-stream transformations and protocol events. [Streaming](https://docs.langchain.com/oss/python/langchain/streaming), [event streaming](https://docs.langchain.com/oss/python/langchain/event-streaming)
20. **Frontend support:** React, Vue, Svelte, and Angular SDKs in the current reference catalog; chat state and streamed messages; tool rendering; structured responses; human review; branching/time travel; stream reconnect; queues; generative UI patterns; integrations with external UI libraries. [Frontend](https://docs.langchain.com/oss/python/langchain/frontend/overview), [JS package catalog](https://reference.langchain.com/llms.txt)
21. **Development and validation:** unit and integration tests; standard provider test suites; agent trajectory evaluations; LangSmith traces; Studio graph inspection; Agent Chat UI; local servers and deployment guides. [Testing](https://docs.langchain.com/oss/python/langchain/test/index), [observability](https://docs.langchain.com/oss/python/langchain/observability)
22. **Classic/legacy component families:** older chain abstractions; retrieval QA and document-combination chains; conversational retrieval; older agent executors; classic memory classes; output parsers; query construction; indexing utilities; older evaluation helpers. Their presence in `langchain-classic` does not make them the current recommended agent API. [Classic](https://reference.langchain.com/python/langchain-classic), [core](https://reference.langchain.com/python/langchain-core)

## 3. LangGraph features

1. **Graph construction:** state schemas; nodes; ordinary/conditional edges; entry and exit points; compilation; cyclic and acyclic workflows; visualization. [Graph API](https://docs.langchain.com/oss/python/langgraph/graph-api)
2. **State updates:** reducers; message-aware reducers; multiple input/output/internal schemas; overwrite/reset semantics; untracked values; typed node/update interfaces. [State model](https://docs.langchain.com/oss/python/langgraph/graph-api)
3. **Dynamic control flow:** conditional routing; `Send` for dynamically scheduled work; fan-out/fan-in; `Command` for state updates and routing; parent/subgraph routing; loops and recursion limits. [Graph execution](https://docs.langchain.com/oss/python/langgraph/use-graph-api)
4. **Functional API:** entrypoint/task decorators; ordinary control flow with checkpointed tasks; async and parallel tasks; resume; previous state; separate return and saved state; explicit handling of side effects and nondeterminism. [Functional API](https://docs.langchain.com/oss/python/langgraph/functional-api)
5. **Runtime:** Pregel-style execution in supersteps; actors and channels; channel update semantics; `LastValue`, `Topic`, aggregation channels, and delta channels; execution scheduling. [Runtime](https://docs.langchain.com/oss/python/langgraph/pregel)
6. **Persistence/checkpointing:** state snapshots; threads; checkpoint identifiers/namespaces; state history; state mutation; task writes; pluggable savers; serialization; persistence across application invocations. [Checkpointers](https://docs.langchain.com/oss/python/langgraph/checkpointers)
7. **Durability and recovery:** resume from saved progress; retain successful parallel work after another task fails; task-level recovery; configurable persistence behavior; idempotency and deterministic replay requirements. External side effects still need appropriate application design. [Checkpointers](https://docs.langchain.com/oss/python/langgraph/checkpointers), [functional execution](https://docs.langchain.com/oss/python/langgraph/functional-api)
8. **Fault handling:** configurable retries/backoff; retry-state inspection; execution and idle timeouts; progress heartbeats; node error handlers; routing after errors; resumable failures; graph-level defaults; graceful draining/shutdown. Consult the version-specific applicability matrix. [Fault tolerance](https://docs.langchain.com/oss/python/langgraph/fault-tolerance)
9. **Human-in-the-loop:** dynamic interrupts carrying application data; persisted suspension; resume values; review/edit/approval patterns; multiple interrupts; subgraph interactions; breakpoints for debugging. [Interrupts](https://docs.langchain.com/oss/python/langgraph/interrupts)
10. **Time travel:** inspect historical state; replay from checkpoints; edit state and fork alternative execution paths; explore different outcomes. [Time travel](https://docs.langchain.com/oss/python/langgraph/use-time-travel)
11. **Memory stores:** cross-thread key/value memory; namespaces; item listing and filtering; semantic search; chosen embedding fields; custom store implementations; separate store and checkpoint contracts. [Stores](https://docs.langchain.com/oss/python/langgraph/stores)
12. **Conversation memory:** persisted messages; history trimming/deletion/summarization; thread-scoped and long-term memory; production database backends. [Memory](https://docs.langchain.com/oss/python/langgraph/add-memory)
13. **Subgraphs:** reusable compiled components; shared or transformed state; nested graphs; per-invocation or persistent subgraph state where supported; inspection and streaming of nested execution. [Subgraphs](https://docs.langchain.com/oss/python/langgraph/use-subgraphs)
14. **Workflow patterns:** prompt chaining; routing; parallelization; orchestrator/worker patterns; evaluator/optimizer loops; tool-using agents; custom RAG and SQL agents. These are supported designs, not separate mandatory packages. [Workflow patterns](https://docs.langchain.com/oss/python/langgraph/workflows-agents)
15. **Caching and context:** node output caching with configurable keys/TTL; runtime context/dependency access; access to stores and stream writers; graph migration considerations. [Graph API](https://docs.langchain.com/oss/python/langgraph/graph-api)
16. **Streaming:** state values/deltas; model messages/tokens; custom data; checkpoints; task events; debugging; subgraph namespaces; multiple modes; node/tag filtering; unified v2 output formats where documented. [Streaming](https://docs.langchain.com/oss/python/langgraph/streaming)
17. **Event streaming:** channel lifecycle events; message/tool projections; custom transformers; simultaneous projections; interrupt/resume handling; custom stream channels. [Event streaming](https://docs.langchain.com/oss/python/langgraph/event-streaming)
18. **Testing and development:** individual node tests; partial graph execution; graph visualization; local server; Studio; Agent Chat UI; traces and evaluations through LangSmith. [Testing](https://docs.langchain.com/oss/python/langgraph/test), [local server](https://docs.langchain.com/oss/python/langgraph/local-server)
19. **Remote execution:** deployed graph invocation via Python/JS SDKs and `RemoteGraph`; threads, runs, assistants, scheduling, authentication, and server-managed persistence belong to the Agent Server/LangSmith Deployment layer. [Deployment components](https://docs.langchain.com/langsmith/components)

## 4. LangSmith features

### Observability and investigation

1. **Trace collection:** runs/spans and nested traces; model, chain, tool, retriever, and custom operations; automatic framework integrations; custom decorators/wrappers; direct API ingestion; OpenTelemetry; sync/async and generator instrumentation. [Instrumentation](https://docs.langchain.com/langsmith/annotate-code), [OpenTelemetry](https://docs.langchain.com/langsmith/trace-with-opentelemetry)
2. **Trace context:** projects; run IDs; parent/child context; distributed traces; tags and metadata; session/thread grouping; model parameters; input/output and errors; attachments and multimodal content. [Concepts](https://docs.langchain.com/langsmith/observability-concepts), [multimodal traces](https://docs.langchain.com/langsmith/log-multimodal-traces)
3. **Trace inspection:** hierarchical run views; messages; timing and latency; tool/retriever inspection; run metadata; custom previews; custom output rendering; trace sharing/management; trace-to-playground workflows. [Trace viewer](https://docs.langchain.com/langsmith/view-traces), [custom rendering](https://docs.langchain.com/langsmith/custom-output-rendering)
4. **Search and analysis:** structured query/filter syntax; SDK queries; thread queries; semantic trace search; filtering by application attributes and feedback; cross-run analysis. [Query syntax](https://docs.langchain.com/langsmith/trace-query-syntax), [semantic search](https://docs.langchain.com/langsmith/semantic-search)
5. **Cost and usage:** token/cost capture; model pricing configuration; latency/error/volume monitoring; project dashboards; custom monitoring views; alerts; granular billable usage. [Costs](https://docs.langchain.com/langsmith/cost-tracking), [dashboards](https://docs.langchain.com/langsmith/dashboards), [alerts](https://docs.langchain.com/langsmith/alerts)
6. **Feedback and production automation:** numerical/categorical feedback; end-user feedback; presigned feedback tokens; manual annotations; rule-based evaluation or queue routing; webhooks. [Feedback](https://docs.langchain.com/langsmith/attach-user-feedback), [rules](https://docs.langchain.com/langsmith/rules)
7. **Data controls:** selective tracing; sampling; masking/redaction; secret filtering; retention and deletion; exporting telemetry to other backends; bulk Parquet exports and destination management. [Sampling](https://docs.langchain.com/langsmith/sample-traces), [masking](https://docs.langchain.com/langsmith/mask-inputs-outputs), [bulk export](https://docs.langchain.com/langsmith/data-export)
8. **AI-assisted investigation:** LangSmith Chat for traces, experiments, and prompts; Insights for behavior/failure categorization; Engine for recurring issue discovery, diagnosis, proposed fixes, connected-repository pull requests, regression datasets, issue tracking, and recurrence detection. [Chat](https://docs.langchain.com/langsmith/chat), [Insights](https://docs.langchain.com/langsmith/insights), [Engine](https://docs.langchain.com/langsmith/engine-overview)

### Evaluation

9. **Datasets:** UI/SDK creation; examples and reference outputs; metadata; attachments; versions and splits; schema configuration; transformations; creation from production traces; sharing and management. [Datasets](https://docs.langchain.com/langsmith/manage-datasets), [SDK dataset management](https://docs.langchain.com/langsmith/manage-datasets-programmatically)
10. **Evaluator types:** code evaluators; LLM-as-a-judge; human judgment; composite evaluators; pairwise comparison; reference-based and reference-free scoring; numerical/categorical and multiple scores; summary-level evaluation. [Evaluation types](https://docs.langchain.com/langsmith/evaluation-types), [composite evaluation](https://docs.langchain.com/langsmith/composite-evaluators-sdk)
11. **Experiment execution:** Python/JS runners; asynchronous execution; concurrency; repetitions; dataset versions/splits; local execution where supported; evaluation of existing outputs; adding evaluators to existing experiments; retries; API-only experiment uploads. [Experiments](https://docs.langchain.com/langsmith/experiment-configuration), [existing experiments](https://docs.langchain.com/langsmith/evaluate-existing-experiment)
12. **Result analysis:** per-example outputs and scores; experiment comparison; pairwise judgments; filtering; performance metrics; aggregate results; evaluation of intermediate steps and graph nodes. [Compare experiments](https://docs.langchain.com/langsmith/compare-experiment-results), [intermediate evaluation](https://docs.langchain.com/langsmith/evaluate-on-intermediate-steps)
13. **Production evaluation:** online code/LLM/composite evaluators; multi-turn evaluation; rule filters and sampling; automatic experiment evaluators; evaluator spending controls. [Online evaluation](https://docs.langchain.com/langsmith/online-evaluations-llm-as-judge), [multi-turn](https://docs.langchain.com/langsmith/online-evaluations-multi-turn), [spend controls](https://docs.langchain.com/langsmith/evaluator-spend)
14. **Agent evaluation:** final answers; tool trajectories; intermediate operations; graph/runnable evaluation; RAG and chatbot evaluation; simulated multi-turn users; backtesting revised agents. [Trajectories](https://docs.langchain.com/langsmith/trajectory-evals), [simulation](https://docs.langchain.com/langsmith/multi-turn-simulation)
15. **Human review:** annotation queues; inline annotations; configurable feedback criteria; queue access and programmatic management; assertions from reviews; auditing judge scores; improving judges with few-shot examples and human feedback. [Annotation queues](https://docs.langchain.com/langsmith/annotation-queues), [assertions](https://docs.langchain.com/langsmith/assertions), [judge improvement](https://docs.langchain.com/langsmith/improve-judge-evaluator-feedback)
16. **Test integration:** pytest; Vitest/Jest; CI/CD evaluation; OpenTelemetry-based experiments; OpenEvals general evaluators; AgentEvals trajectory checks. [pytest](https://docs.langchain.com/langsmith/pytest), [Vitest/Jest](https://docs.langchain.com/langsmith/vitest-jest), [OpenEvals](https://github.com/langchain-ai/openevals), [AgentEvals](https://github.com/langchain-ai/agentevals)

### Prompts and context

17. **Prompt management:** create/edit/pull/push prompts; commits and version tags; public/private prompt organization; model settings; tool definitions; multimodal templates; prompt webhooks. [Prompt management](https://docs.langchain.com/langsmith/manage-prompts), [programmatic access](https://docs.langchain.com/langsmith/manage-prompts-programmatically)
18. **Playground:** model/provider selection; custom endpoints; prompt variants; tool/schema configuration; multi-turn testing; multimodal input; dataset evaluation; AI assistance for prompts, tools, and output schemas. [Prompt engineering](https://docs.langchain.com/langsmith/prompt-engineering-concepts), [playground evaluations](https://docs.langchain.com/langsmith/run-evaluation-from-playground)
19. **Context Hub:** versioned instruction/tool bundles; skills and agent definitions; environment promotion; sharing/review; SDK access; signed commit webhooks. [Prompt & Context Hub](https://docs.langchain.com/langsmith/prompt-context-hub), [context concepts](https://docs.langchain.com/langsmith/context-engineering-concepts)

### Deployment, runtime, and Studio

20. **Agent Server:** API/runtime hosting; graph/agent execution; persisted threads/state; assistants and their versions; streaming; durable background work; server SDKs; `RemoteGraph`. [Agent Server](https://docs.langchain.com/langsmith/agent-server-overview), [components](https://docs.langchain.com/langsmith/components)
21. **Run management:** stateful/stateless runs; stream/wait/background invocation; joining and cancelling runs; batches; webhooks; scheduled runs/crons; thread history and copying. [Runs](https://docs.langchain.com/langsmith/runs), [cron jobs](https://docs.langchain.com/langsmith/cron-jobs), [Agent Server API](https://docs.langchain.com/langsmith/server-api-ref)
22. **Concurrent input policies:** reject another run; enqueue; interrupt; rollback; handling new user messages while an agent is working. [Double texting](https://docs.langchain.com/langsmith/double-texting)
23. **Runtime interaction:** human interrupts; state edits; time travel; configurable runtime headers; store access; TTLs; server-side caching; distributed traces. [Core capabilities](https://docs.langchain.com/langsmith/core-capabilities), [caching](https://docs.langchain.com/langsmith/caching)
24. **Extensibility/security:** custom authentication; per-resource authorization; store authorization; custom routes, middleware, and application lifespan; Docker customization; custom checkpoint/store backends; MCP and A2A endpoints. [Custom authentication](https://docs.langchain.com/langsmith/custom-auth), [MCP](https://docs.langchain.com/langsmith/server-mcp), [A2A](https://docs.langchain.com/langsmith/server-a2a)
25. **Hosting operations:** cloud deployments; revisions; preview builds; logs/metrics; horizontal scaling; workload isolation; monorepos; managed cloud, BYOC, hybrid, self-hosted control plane, or standalone servers as documented. [Deployment](https://docs.langchain.com/langsmith/deployment), [BYOC](https://docs.langchain.com/langsmith/byoc), [self-hosting](https://docs.langchain.com/langsmith/self-hosted)
26. **Other frameworks/frontends:** adapters for non-LangGraph frameworks; Google ADK and other agent framework deployment guides; full-stack examples for Next.js, Nuxt, SvelteKit, Vite, Cloudflare Workers, and Deno. [Other frameworks](https://docs.langchain.com/langsmith/deploy-other-frameworks), [full-stack deployment](https://docs.langchain.com/langsmith/deploy-frameworks-and-platforms)
27. **Studio:** graph visualization; interactive runs; traces; assistant configuration; thread/state inspection; interrupts; replay/forking; local Agent Server connection; debugging deployed agents. [Studio](https://docs.langchain.com/langsmith/studio), [using Studio](https://docs.langchain.com/langsmith/use-studio)

### Additional platform services

28. **Sandboxes:** isolated code execution and filesystems; SDK/CLI lifecycle management; commands and interactive shells; snapshots; resource configuration; stop/restart; file transfer/download links; mounts; service URLs; network/auth proxy; permissions; SSH/tunneling where documented. [Sandboxes](https://docs.langchain.com/langsmith/sandboxes), [sandbox CLI](https://docs.langchain.com/langsmith/sandbox-cli), [auth proxy](https://docs.langchain.com/langsmith/sandbox-auth-proxy)
29. **Fleet:** agent creation without code; templates; instructions; skills; persistent memory; subagents; app/MCP connections; tool approvals; agent/user identity; sharing; schedules; channel triggers; Slack/Teams integration; virtual computer access; traces; code/API invocation and export. [Fleet essentials](https://docs.langchain.com/langsmith/fleet/essentials), [computer use](https://docs.langchain.com/langsmith/fleet/computer-use), [code access](https://docs.langchain.com/langsmith/fleet/code)
30. **Managed Deep Agents (documented beta):** deployable agent definitions; tools; instructions; memory; skills; sandboxes; identity; MCP connectors; schedules/channels; middleware; local Studio development and evaluation. [Managed Deep Agents](https://docs.langchain.com/langsmith/python/managed-deep-agents-overview)
31. **LLM Gateway:** centralized provider credentials; multiple API formats; automatic traces; custom providers; model fallbacks; spend and rate policies; customer-specific header policies; access controls; coding-agent setup; data protection. [Gateway](https://docs.langchain.com/langsmith/llm-gateway), [gateway policies](https://docs.langchain.com/langsmith/llm-gateway-spend-policies)
32. **Agent Auth and Tool Server:** OAuth credentials for agents; user/agent identity; authenticated tools; custom toolkits; MCP gateway aggregation; authentication-aware tool execution. [Agent Auth](https://docs.langchain.com/langsmith/agent-auth), [Tool Server](https://docs.langchain.com/langsmith/fleet/mcp-framework)
33. **Administration:** organizations/workspaces/projects; API keys and service accounts; RBAC and ABAC; resource tags; SSO; user/group provisioning where supported; audit logs; usage/billing; regional deployment; retention/deletion; encryption and infrastructure security configuration; Terraform management. [Administration](https://docs.langchain.com/langsmith/administration-overview), [RBAC](https://docs.langchain.com/langsmith/rbac), [ABAC](https://docs.langchain.com/langsmith/abac), [audit logs](https://docs.langchain.com/langsmith/audit-logs)
34. **Programmatic platform access:** Python/JS clients; REST APIs for platform and Agent Server resources; CLI; OAuth remote MCP; legacy standalone MCP; custom apps inside LangSmith; telemetry export and collectors. [CLI](https://docs.langchain.com/langsmith/langsmith-cli), [remote MCP](https://docs.langchain.com/langsmith/langsmith-remote-mcp), [custom apps](https://docs.langchain.com/langsmith/custom-apps)

## 5. Langfuse features

### Tracing, observability, and analytics

1. **Instrumentation:** Python decorators/context managers/manual observations; JavaScript wrappers/manual spans; framework integrations; OpenTelemetry ingestion; trace nesting; asynchronous propagation; distributed trace IDs. [Instrumentation](https://langfuse.com/docs/observability/sdk/instrumentation), [distributed tracing](https://langfuse.com/docs/observability/features/trace-ids-and-distributed-tracing)
2. **Observation types:** `span`, `event`, `generation`, `agent`, `tool`, `chain`, `retriever`, `evaluator`, `embedding`, and `guardrail`. These classify recorded work; a guardrail observation does not itself enforce an application policy. [Observation types](https://langfuse.com/docs/observability/features/observation-types)
3. **Recorded context:** inputs/outputs; model names and parameters; timestamps; errors/log levels; metadata; tags; release/version identifiers; environments; users; sessions. [Data model](https://langfuse.com/docs/observability/data-model), [metadata](https://langfuse.com/docs/observability/features/metadata)
4. **Trace exploration:** nested observation view; execution timeline; trace URLs; agent graph visualization including aggregated and execution views; session replay; per-user inspection; links to external systems. [Agent graphs](https://langfuse.com/docs/observability/features/agent-graphs), [sessions](https://langfuse.com/docs/observability/features/sessions), [user tracking](https://langfuse.com/docs/observability/features/users)
5. **Multimodality:** text, images, audio, and attachments in traces; SDK media handling; multimodal evaluation/prompt workflows where supported. [Multimodality](https://langfuse.com/docs/observability/features/multi-modality)
6. **Token/cost tracking:** supplied usage and cost; automatic provider capture; model pricing definitions; custom model pricing; input/output and other usage categories when supplied; analysis by model, user, session, or environment. [Token and cost tracking](https://langfuse.com/docs/observability/features/token-and-cost-tracking)
7. **Search and filtering:** full-text search of recorded payloads; field/operator query bar; metadata and attribute filtering; aliases, wildcards, and autocomplete. [Full-text search](https://langfuse.com/docs/observability/features/full-text-search), [filter bar](https://langfuse.com/docs/observability/features/filter-search-bar)
8. **Operational analytics:** standard/custom dashboards; configurable charts and aggregates; latency, usage, cost, and quality analysis; charting the current table query; Pulse outlier/time-range exploration; metrics API. [Dashboards](https://langfuse.com/docs/metrics/features/custom-dashboards), [table charts](https://langfuse.com/docs/observability/features/events-table-charts), [Pulse](https://langfuse.com/docs/observability/features/pulse)
9. **Alerting:** metric thresholds; filtered observation/score measures; severity and notification settings; webhook/Slack/GitHub automation paths; organization spending alerts. Plan limits and server-version requirements apply. [Metric alerts](https://langfuse.com/docs/observability/features/alerts), [spend alerts](https://langfuse.com/docs/administration/spend-alerts)
10. **Collaboration and corrections:** comments on recorded resources/prompts; corrected outputs; user feedback; trace sharing through URLs; web callouts to external HTTP workflows. [Comments](https://langfuse.com/docs/observability/features/comments), [corrections](https://langfuse.com/docs/observability/features/corrections), [web callouts](https://langfuse.com/docs/observability/features/web-callouts)
11. **SDK/data controls:** sampling; background queues/batches; flushing/shutdown; attribute propagation; masking; instrumentation-scope filtering; multi-project routing; SDK logging; environment configuration. [Advanced SDK features](https://langfuse.com/docs/observability/sdk/advanced-features), [masking](https://langfuse.com/docs/observability/features/masking)
12. **MCP tracing:** capture client/server interactions and preserve trace relationships across MCP boundaries. [MCP tracing](https://langfuse.com/docs/observability/features/mcp-tracing)

### Prompt management

13. **Prompt storage:** text/chat prompt types; UI/API/SDK creation; immutable versions; movable labels for deployment; tags/folders; associated JSON configuration. [Prompt concepts](https://langfuse.com/docs/prompt-management/data-model), [versions](https://langfuse.com/docs/prompt-management/features/prompt-version-control)
14. **Prompt composition:** variable substitution; conversation/message placeholders; references to other prompts; reusable fragments; hierarchical folders. [Variables](https://langfuse.com/docs/prompt-management/features/variables), [placeholders](https://langfuse.com/docs/prompt-management/features/message-placeholders), [composition](https://langfuse.com/docs/prompt-management/features/composability)
15. **Prompt delivery:** SDK caching; cache refresh controls; fallback prompts; startup prefetch patterns; label/version selection; deployment without changing application code; A/B testing patterns. [Caching](https://langfuse.com/docs/prompt-management/features/caching), [availability patterns](https://langfuse.com/docs/prompt-management/features/guaranteed-availability), [A/B testing](https://langfuse.com/docs/prompt-management/features/a-b-testing)
16. **Prompt testing/measurement:** playground; model/prompt comparisons; tool/model configuration where supported; linking prompt versions to observations; measuring prompt-specific quality, cost, and latency. [Playground](https://langfuse.com/docs/prompt-management/features/playground), [trace links](https://langfuse.com/docs/prompt-management/features/link-to-traces)
17. **Prompt automation:** lifecycle webhooks; GitHub synchronization/CI recipes; n8n integration; agent-driven prompt management via CLI/MCP/skills. [Webhooks](https://langfuse.com/docs/prompt-management/features/webhooks-slack-integrations), [GitHub](https://langfuse.com/docs/prompt-management/features/github-integration), [agent access](https://langfuse.com/docs/prompt-management/features/agentic-access)

### Evaluation

18. **Scores:** numerical, Boolean, and categorical scores; score configurations; comments; API/SDK ingestion; manual UI scoring; user feedback; associating scores with supported observation/session/experiment entities. [Scores](https://langfuse.com/docs/evaluation/scores/overview), [score model](https://langfuse.com/docs/evaluation/scores/data-model)
19. **Model-based evaluation:** LLM judges; templates/custom rubrics; model connections; mapping input/output/reference fields; production evaluation rules; filtering/sampling; evaluation of experiments. [LLM judges](https://langfuse.com/docs/evaluation/evaluation-methods/llm-as-a-judge)
20. **Code evaluation:** hosted Python/TypeScript checks; deterministic business rules; schema/keyword/tool-call checks; one or multiple scores; live observations and experiments. Self-hosting requires the documented code-evaluator dispatcher. [Code evaluators](https://langfuse.com/docs/evaluation/evaluation-methods/code-evaluators)
21. **Human evaluation:** annotation queues; reviewer workflows; UI scoring; feedback collection; custom external evaluation pipelines through the API. [Annotation queues](https://langfuse.com/docs/evaluation/evaluation-methods/annotation-queues), [SDK scores](https://langfuse.com/docs/evaluation/evaluation-methods/scores-via-sdk)
22. **Datasets:** inputs, expected outputs, and metadata; source-trace association; dataset items and runs; hosted/local datasets; dataset versioning where documented; experiment result linkage. [Datasets](https://langfuse.com/docs/evaluation/experiments/datasets), [experiment model](https://langfuse.com/docs/evaluation/experiments/data-model)
23. **Experiments:** SDK task/evaluator runners; UI prompt/model experiments; concurrency/configuration; comparison of runs and items; experiment-level evaluation; OpenTelemetry association; CI/CD execution and quality gates. [SDK experiments](https://langfuse.com/docs/evaluation/experiments/experiments-via-sdk), [UI experiments](https://langfuse.com/docs/evaluation/experiments/experiments-via-ui), [CI/CD](https://langfuse.com/docs/evaluation/experiments/experiments-ci-cd)
24. **Score analytics:** distributions; score trends; comparisons and agreement between evaluation methods; quality monitoring alongside cost/latency. [Score analytics](https://langfuse.com/docs/evaluation/scores/score-analytics)

### APIs, administration, and self-hosting

25. **Data APIs:** project APIs for observations, traces, sessions, prompts, datasets, scores, experiments, and configuration; aggregate metrics; selective field retrieval; cursor pagination where supported; typed SDK wrappers; OpenAPI specification. [Public API](https://langfuse.com/docs/api-and-data-platform/features/public-api), [data platform](https://langfuse.com/docs/api-and-data-platform/overview)
26. **Data exports:** filtered UI downloads; scheduled blob-storage exports to supported S3/GCS/Azure configurations; observation and score exports; downstream analytics integrations including PostHog/Mixpanel. [UI export](https://langfuse.com/docs/api-and-data-platform/features/export-from-ui), [blob export](https://langfuse.com/docs/api-and-data-platform/features/export-to-blob-storage), [integrations](https://langfuse.com/integrations)
27. **Agent access:** Langfuse Assistant inside the product; API CLI; operational MCP server; coding-agent skill; separate documentation MCP/search endpoint. [Assistant](https://langfuse.com/docs/langfuse-assistant), [CLI](https://langfuse.com/docs/api-and-data-platform/features/cli), [MCP](https://langfuse.com/docs/api-and-data-platform/features/mcp-server)
28. **Organization administration:** organizations/projects; project API keys; roles and permissions; SSO/authentication; SCIM and organization provisioning APIs; audit logs; LLM connections; retention/deletion; usage and spending administration. [RBAC](https://langfuse.com/docs/administration/rbac), [SSO](https://langfuse.com/docs/administration/authentication-and-sso), [provisioning](https://langfuse.com/docs/administration/scim-and-org-api), [audit logs](https://langfuse.com/docs/administration/audit-logs)
29. **Self-hosting:** Docker/Kubernetes/cloud deployment guides; database/cache/object-storage configuration; scaling; network/security configuration; authentication; backup/restore; upgrades; monitoring; headless provisioning; instance administration. Some enterprise administration capabilities require the relevant edition/license. [Self-hosting](https://langfuse.com/self-hosting), [self-hosting index](https://langfuse.com/llms-self-hosting.txt)
30. **Security integrations:** trace guardrail execution; evaluate unsafe outputs; integrate external filtering/guardrail libraries. Langfuse observability is not a replacement for enforcement inside the application. [Security and guardrails](https://langfuse.com/docs/security-and-guardrails)

## 6. Main libraries and tools

The companion package catalog lists every registry-verified candidate found in the collected documentation and reference overviews, with its source and package description. This section explains the central packages. A Python import namespace is not always a separate distribution, and a JavaScript subpath is not always a separate npm package.

### LangChain

| Package | Language | Purpose |
|---|---|---|
| `langchain` | Python; JS/TS | Current agent construction and high-level framework APIs. |
| `langchain-core`; `@langchain/core` | Python; JS/TS | Messages, models, prompts, tools, runnables, documents, callbacks, and other base contracts. |
| `langchain-community`; `@langchain/community` | Python; JS/TS | Community integration implementations. |
| `langchain-classic`; `@langchain/classic` | Python; JS/TS | Earlier chain/agent/component APIs retained separately. |
| `langchain-text-splitters`; `@langchain/textsplitters` | Python; JS/TS | Document chunking. |
| `langchain-tests` | Python | Standard behavior tests for integrations. JavaScript also documents standard testing infrastructure; an npm registry record for `@langchain/standard-tests` could not be verified in this collection. |
| `langchain-mcp-adapters`; `@langchain/mcp-adapters` | Python; JS/TS | MCP interoperation. |
| `@langchain/react`, `@langchain/vue`, `@langchain/svelte`, `@langchain/angular` | JS/TS | Framework-specific application UI clients. |
| Provider packages | Python; JS/TS | Separate model, embedding, vector-store, tool, data-loader, sandbox, and other integrations. See the complete catalog. |

Sources: [reference catalog](https://reference.langchain.com/llms.txt), [Python integrations](https://docs.langchain.com/oss/python/integrations/providers/overview), [JS integrations](https://docs.langchain.com/oss/javascript/integrations/providers/overview).

### LangGraph

| Package or module | Language | Purpose |
|---|---|---|
| `langgraph`; `@langchain/langgraph` | Python; JS/TS | Graph/functional execution. |
| `langgraph-checkpoint`; `@langchain/langgraph-checkpoint` | Python; JS/TS | Checkpoint interfaces and baseline implementations; Python store interfaces are also exposed through this distribution. |
| `langgraph-checkpoint-postgres`; `@langchain/langgraph-checkpoint-postgres` | Python; JS/TS | PostgreSQL persistence. |
| `langgraph-checkpoint-sqlite`; `@langchain/langgraph-checkpoint-sqlite` | Python; JS/TS | SQLite persistence. |
| Additional checkpointer/store packages | Varies | MongoDB, Redis, AWS, Aerospike and other backends listed separately in the package catalog; ownership and capability vary. |
| `langgraph-prebuilt` | Python | Prebuilt agent/tool components; older agent factories may have newer replacements. |
| `langgraph.prebuilt`, `langgraph.store`, `langgraph.checkpoint` | Python modules | Import namespaces; do not count these as three extra packages in addition to their distributions. |
| `langgraph-sdk`; `@langchain/langgraph-sdk` | Python; JS/TS | Agent Server client and remote graph access. |
| `langgraph-cli`; `@langchain/langgraph-cli` | Python; JS/TS | Local development, packaging, and deployment commands. |
| `langgraph-api`; `@langchain/langgraph-api` | Python; JS/TS | Server/runtime tooling; distribution and licensing differ from the core graph library. |
| `langgraph-supervisor`; `@langchain/langgraph-supervisor` | Python; JS/TS | Supervisor orchestration helper libraries. The Python overview recommends implementing the supervisor pattern directly with tools for most new work. |
| `langgraph-swarm`; `@langchain/langgraph-swarm` | Python; JS/TS | Swarm/handoff orchestration helpers. |
| `@langchain/langgraph-checkpoint-validation` | JS/TS | Checkpointer conformance tests. |
| `@langchain/langgraph-cua` | JS/TS | Computer-use agent helper project listed in the reference catalog. |

Sources: [package reference](https://reference.langchain.com/llms.txt), [supervisor](https://reference.langchain.com/python/langgraph-supervisor), [server components](https://docs.langchain.com/langsmith/components).

### LangSmith

| Package/tool | Purpose |
|---|---|
| `langsmith` on PyPI and npm | Tracing, datasets, evaluation, prompts, feedback, and platform clients. |
| `langsmith[sandbox]` | Python installation extra for sandbox functionality; not a separately named package. JS accesses this through `langsmith/sandbox`. |
| `openevals` on PyPI and npm | Reusable output evaluators: LLM judges, structured-output checks, text comparisons, and code evaluation capabilities. |
| `agentevals` on PyPI and npm | Trajectory matching and model-judged agent behavior evaluation. |
| LangSmith CLI | Platform commands distributed as a native CLI; do not assume a similarly named Python package is the official binary. |
| `langsmith-tool-server` | Authenticated MCP tools/toolkits and MCP aggregation. |
| `langchain-cli-v2` | Tooling used by the documented Tool Server/agent platform workflows. |
| `deployments-wrap-sdk` | Adapts other agent frameworks to Agent Server deployment. |
| `fleet-deepagents-export` | Runs/exports Fleet agent definitions in code, as documented. |
| LangSmith Remote MCP | Hosted/self-hosted MCP endpoint; a service, not a required client library. |
| `langsmith-mcp-server` | Older standalone MCP implementation; current docs point to Remote MCP, retaining standalone use for specified cases. |

Sources: [LangSmith reference](https://reference.langchain.com/python/langsmith), [sandbox setup](https://docs.langchain.com/langsmith/sandboxes), [OpenEvals](https://github.com/langchain-ai/openevals), [AgentEvals](https://github.com/langchain-ai/agentevals), [CLI](https://docs.langchain.com/langsmith/langsmith-cli), [Tool Server](https://docs.langchain.com/langsmith/fleet/mcp-framework), [other frameworks](https://docs.langchain.com/langsmith/deploy-other-frameworks), [Fleet code](https://docs.langchain.com/langsmith/fleet/code), [MCP migration](https://docs.langchain.com/langsmith/langsmith-mcp-server).

### Langfuse

| Package/module/tool | Purpose |
|---|---|
| `langfuse` on PyPI | Python SDK for tracing, prompts, evaluation, and data APIs. |
| `langfuse.openai`, `langfuse.langchain` | Python SDK integration modules, not additional pip packages. |
| `@langfuse/core` | Shared JS types/utilities/logging. |
| `@langfuse/client` | JS prompt, dataset, score, and API client. |
| `@langfuse/browser` | Browser-safe public-key feedback/score ingestion. |
| `@langfuse/tracing` | JS observation and tracing functions. |
| `@langfuse/otel` | OpenTelemetry span processing/export. |
| `@langfuse/openai` | JS OpenAI SDK instrumentation. |
| `@langfuse/langchain` | JS LangChain callbacks/instrumentation. |
| `langfuse-cli` on npm | CLI generated around public API operations. |
| Older `langfuse`/`langfuse-langchain`/`langfuse-core` npm packages | Historical JS package layout; check migration documentation before using examples built around them. |
| Integration/plugin packages | Additional packages referenced by integrations, including coding-agent plugins and n8n components; listed with their evidence in the catalog. |
| Other-language OTel SDKs | Java/Kotlin, Go, .NET, Rust, Ruby, PHP, C++, and others can send telemetry. These are not all official Langfuse SDKs. |

Sources: [SDK overview](https://langfuse.com/docs/observability/sdk/overview), [upgrade path](https://langfuse.com/docs/observability/sdk/upgrade-path), [CLI](https://langfuse.com/docs/api-and-data-platform/features/cli), [integration directory](https://langfuse.com/integrations).

## 7. Adjacent ecosystem and historical components

| Component | Scope |
|---|---|
| Deep Agents (`deepagents`, Python/JS) | Higher-level agent harness: planning, filesystem/context management, skills, memory, subagents, human review, sandbox backends, and streaming. Additional capabilities such as dynamic delegation, rubrics, profiles, or interpreters have their own maturity/version labels. |
| Deep Agents Code / ACP packages | Terminal coding-agent experience and Agent Client Protocol integration; distinct from the framework libraries. |
| Sandbox/backend packages | Deep Agents execution backends for local/virtual filesystems and services such as Modal, Daytona, E2B, Runloop, Vercel, AWS AgentCore, and LangSmith. See the package and integration catalogs for exact names. |
| LangMem (`langmem`) | Memory extraction/consolidation tools and prompt refinement, with LangGraph store integration. |
| LangServe (`langserve`) | Older Runnable HTTP serving layer: invocation, batching, streaming, schemas, playground, and remote client. Separate from Agent Server. |
| `langchain-experimental` | Experimental component collection; not a guarantee of stable APIs or current recommended architecture. |
| OpenWiki | Repository/personal documentation tooling appearing in current ecosystem docs. |

Sources: [Deep Agents](https://docs.langchain.com/oss/python/deepagents/overview), [Code](https://docs.langchain.com/oss/deepagents/code/overview), [LangMem](https://github.com/langchain-ai/langmem), [LangServe](https://github.com/langchain-ai/langserve), [experimental library](https://github.com/langchain-ai/langchain-experimental), [OpenWiki](https://docs.langchain.com/oss/openwiki/overview).

## 8. Integration coverage and interpretation

The linked documentation catalog retains each discovered integration page, grouped by product and language. It includes provider libraries and recipes that use third-party instrumentation, gateways, or callbacks. An integration page does not necessarily correspond to a unique installable package.

- **LangChain:** models; embeddings; vector stores; loaders; retrievers; rerankers/transformers; tools/toolkits; caches; database/graph integrations; middleware; sandboxes; interpreters; memory/checkpoint backends; UI integrations.
- **LangSmith:** LangChain/LangGraph/Deep Agents; provider SDK wrappers; OpenTelemetry; other agent frameworks; realtime/voice frameworks; coding agents; test runners; deployment adapters; infrastructure/export systems.
- **Langfuse:** model providers; agent frameworks; gateways/proxies; low-code platforms; coding tools; voice agents; evaluation/analytics tools; OpenTelemetry instrumentors; infrastructure/automation recipes; community SDKs.

Use the companion catalog to locate an exact provider or library. The catalog is intentionally broader than this readable feature inventory. Availability is established at the documentation/registry level, not through execution testing of every integration.
