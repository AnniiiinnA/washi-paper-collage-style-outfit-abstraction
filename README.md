# Washi-paper collage style outfit abstraction

[中文说明](README.zh-CN.md)

An agent-independent workflow that turns the main outfit in a fashion or travel photo into a minimal flat handmade washi-paper collage on a true transparent PNG background. It preserves silhouette, colors, structure, layering, and material character using a few large paper shapes.

## Method 1: Give the repository link to your agent

No installation is needed if your agent can read GitHub files. Attach your photo and send:

```text
Read SKILL.md and the complete references/exact-prompt.md in this repository, then follow the workflow to turn the main outfit in my photo into a transparent washi-paper collage:
https://github.com/AnniiiinnA/washi-paper-collage-style-outfit-abstraction
If you cannot access the files or generate images, tell me what capability is missing.
```

If your agent supports GitHub skill installation, ask it to install this repository using its supported mechanism and preserve the directory structure. Alternatively, clone it and ask the agent to read the local `SKILL.md`:

```sh
git clone https://github.com/AnniiiinnA/washi-paper-collage-style-outfit-abstraction.git
```

Cloning downloads the workflow; automatic skill discovery depends on the host's installation mechanism.

## Method 2: Upload the files to a conversational AI

Click **Code → Download ZIP** on GitHub, extract it, and upload:

- `SKILL.md`
- All Markdown files in `references/` (the exact prompt is essential; the Codex adapter is optional outside Codex)
- Your fashion or travel photo

Then send:

```text
Read the uploaded SKILL.md and references/exact-prompt.md completely. Follow the workflow to analyze the main outfit in my photo and generate a minimal flat washi-paper collage as a true transparent PNG. Use the Codex adapter only in Codex. If you cannot generate images, give me the full assembled prompt and label it as a prompt-only handoff.
```

If document uploads are unsupported, paste the complete contents of `SKILL.md` and `references/exact-prompt.md`. Do not summarize the exact prompt.

## Method 3: Install as a local skill

Use your agent's documented skill directory or GitHub installer. Keep `SKILL.md` and `references/` together. `agents/openai.yaml` is optional Codex metadata; other hosts can ignore it.

For Codex, copy the repository folder to:

- Windows: `%USERPROFILE%\.codex\skills\washi-paper-collage-style-outfit-abstraction`
- macOS/Linux: `~/.codex/skills/washi-paper-collage-style-outfit-abstraction`
- Custom `CODEX_HOME`: its `skills` subdirectory

Start a new session, attach a photo, and ask:

```text
Use $washi-paper-collage-style-outfit-abstraction to abstract the main outfit in this photo.
```

Hosts without `$skill-name` syntax can use an ordinary request to follow `SKILL.md`.

## Capabilities and limitations

| Host capabilities | Available result |
| --- | --- |
| Read instructions, inspect photos, reference-guided image generation with PNG alpha | Full image workflow |
| Read instructions and inspect photos, but no image generation | Analysis and full generation prompt; no finished image |
| Cannot inspect photos | Load the workflow, then transfer to a vision-capable environment |

The workflow is portable; it cannot add vision, browsing, image generation, or transparency support to a host. Other agents do not require Codex or its `imagegen` skill. Codex-specific instructions are isolated in `references/codex-adapter.md`. No Python is required for the core workflow; provider setup and costs depend on the host.

The target is a body-free outfit centered at 45–55% of canvas height with real transparency. Separate accessories such as bags, jewelry, hats, and shoes are excluded by default. Selection, analysis order, shape planning, and prompt assembly are repeatable; generated pixels are not deterministic. One correction is allowed, with remaining artifacts disclosed. Execution has not been tested on every agent platform.

The original rendering prompt remains verbatim in `references/exact-prompt.md` (formerly `.txt`). No source photos or generated images are included.
