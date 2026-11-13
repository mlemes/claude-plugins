# Data flow

Claude Code fetches .claude-plugin/marketplace.json from this public repository. On installation it fetches the selected plugin from its own GitHub repository at the pinned commit into the Claude Code plugin cache. Plugin setup and runtime data handling belong to that plugin. This catalog receives no quota credentials, ML datasets or runtime telemetry.

Register mlemes/claude-plugins as the source for the mlemes marketplace. Plugin repositories contain their own plugin manifests and runtime components.
