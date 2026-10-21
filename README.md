# Ghost Hat Studio plugins for Claude Code

The catalog of Claude skills and Claude Code plugins published by
[Ghost Hat Studio](https://ghosthatstudio.com/toolbox/). Add it once and install anything in it.

## Add the catalog

In a Claude Code session:

```
/plugin marketplace add ghosthat-studio/marketplace
```

If this machine has no SSH key for GitHub, start Claude Code with
`CLAUDE_CODE_PLUGIN_PREFER_HTTPS=1` so the catalog clones over HTTPS.

## What's in it

| Plugin | What it does | Install |
|---|---|---|
| [local-agents](https://ghosthatstudio.com/toolbox/local-agents/) | A skill that teaches Claude to build, run and debug agents on locally hosted models (Ollama, vLLM, llama.cpp, LM Studio, MLX) without starving the model of context, time, tools or reasons. | `/plugin install local-agents@ghosthat-studio` |

Browse it inside Claude Code with `/plugin`, under **Discover**.

## Staying up to date

Run `/plugin marketplace update ghosthat-studio`, or turn on auto-update for this catalog under
**Marketplaces** in `/plugin`. Each plugin entry pins a release tag, so you get a new version
only when it is released here.

## For maintainers

Each plugin lives in its own repository. An entry in `.claude-plugin/marketplace.json` points
at that repository and pins the release tag. To release a new version of a plugin:

1. Bump `version` in the plugin's own `.claude-plugin/plugin.json`, tag the release there
   (`vX.Y.Z`), and publish its GitHub release.
2. Move the entry's `ref` here to the new tag and `sha` to the commit it points at.
3. Run `claude plugin validate . --strict`, then push.

Never rename a plugin's `name`: it is the install id. To change what people see, set
`displayName`; to retire a plugin, remove the entry and map its name to `null` under `renames`.

## License

The catalog file is MIT. Each plugin carries its own license in its repository.
