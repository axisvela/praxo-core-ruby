# PRAXO-CORE Ruby Core

Native Ruby Core for the PRAXO-CORE agent framework. This is the Ruby source
and gem distribution repository; the main contract and cross-language sources
live in [axisvela/praxo-core](https://github.com/axisvela/praxo-core).

- `SPEC_VERSION`: `0.2.0`
- Core version: `0.4.1`
- Tier: core
- License: MIT
- Dependencies: Ruby standard library only
- Ruby: `>= 3.1`

## Install

```bash
gem install praxo-core
```

## Quickstart

```ruby
require "praxo/agent"
require "praxo/models"

model = Praxo::Agent::StaticModel.new("hello")
options = Praxo::Agent::AgentOptions.new(model)
result = Praxo::Agent.run_agent(
  options,
  Praxo::Models.session(id: "demo"),
  "hello"
)
puts result[:output]
```

Tools register on the options object:

```ruby
require "praxo/agent"

registry = Praxo::Agent::ToolRegistry.new
registry.register(Praxo::Agent::FuncTool.new("echo", "Echo arguments", ->(arguments) {
  arguments
}))

options = Praxo::Agent::AgentOptions.new(model)
options.tools = registry
options.max_steps = 8
```

## Scope

The Core implements all eleven conformance vector groups: toolcall, JSON Schema,
plugin, memory, event, stream, checkpoint, policy, context, middleware, and the
agent loop. It also implements human-in-the-loop interrupt decisions, streaming,
cancellation, bounded parallel tools, and run-scoped call limits.

The gem contains `lib/`, `api/`, `README.md`, and `LICENSE`. Conformance,
compatibility, and behavior tests live in the main monorepo.

## Links

- Main repository: https://github.com/axisvela/praxo-core
- Ruby documentation: https://axisvela.github.io/praxo-core/languages/ruby/
- API snapshot: [`api/0.4.1.txt`](api/0.4.1.txt)
