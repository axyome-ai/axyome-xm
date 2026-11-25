# Axyome XM plugin for Claude Code

This plugin helps Claude Code use your Axyome XM memory. It adds:

- **an agent**, `xm-agent`, that answers questions about your past work from your memory before it reads the code;
- **four memory skills**: debugging with past errors (`memory-debug`), error patterns over time (`error-forensics`), code review with your history (`code-review-memory`), and past decisions (`decision-recall`).

## It needs the Axyome XM extension for VS Code

The extension records the memory: the files you edited, the errors you hit, the terminal commands you ran, your commits, and your Copilot, Claude Code and Codex sessions, stored on your own machine. The plugin helps Claude Code use that memory. Without the extension, the agent tells you where the memory comes from and does not guess.

[Install Axyome XM from the VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=axyome-ai.axyome-ai-xm) (also on [Open VSX](https://open-vsx.org/extension/axyome-ai/axyome-ai-xm))

**Already using the extension?** It installs this plugin for you when you agree to connect Claude Code on first run. You have nothing to do.

## Install from GitHub

In Claude Code:

```text
/plugin marketplace add axyome-ai/axyome-xm
/plugin install axyome-xm@axyome-ai
```

## Privacy

The plugin holds instructions only: it sends nothing anywhere. Your memory stays where the extension stores it, on your computer. See [Privacy](../../README.md#privacy).

## Support

Questions and problems: [GitHub issues](https://github.com/axyome-ai/axyome-xm/issues) or [axyome.ai/support](https://axyome.ai/support).

— Axyome.ai Team
