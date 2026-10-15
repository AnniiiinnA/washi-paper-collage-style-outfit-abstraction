# Washi-paper collage style outfit abstraction

A Codex skill that turns the main outfit in a photo into a minimal, flat handmade washi-paper collage on a transparent PNG background.

It analyzes silhouette, color, garment structure, layering, material appearance, and clothing-integral accessories, then uses a small number of large paper shapes. The original rendering prompt is preserved verbatim in `references/exact-prompt.txt`.

## Install

Download this repository and copy its folder to your Codex skills directory:

- Windows: `%USERPROFILE%\.codex\skills\washi-paper-collage-style-outfit-abstraction`
- macOS/Linux: `~/.codex/skills/washi-paper-collage-style-outfit-abstraction`
- If you use a custom `CODEX_HOME`, use its `skills` subdirectory instead.

The destination folder must contain `SKILL.md`, `agents/openai.yaml`, and `references/exact-prompt.txt` directly. Start a new Codex session after installation.

## Use

Attach a fashion or travel photo and ask:

```text
Use $washi-paper-collage-style-outfit-abstraction to abstract the main outfit in this photo.
```

Requires an environment with the built-in image generation tool and the `imagegen` skill. Python and an API key are not required for the default rendering workflow.

## Output and limitations

The target is an isolated outfit made from a few flat paper shapes, without a person or mannequin, on a true transparent background. The outfit should occupy 45–55% of image height. Separate accessories such as bags, jewelry, hats, and shoes are excluded by default.

Selection, analysis order, shape planning, and prompt assembly are repeatable. Image generation is stochastic and can leave edge artifacts or miss the requested composition; the skill checks the result, allows one correction, and reports remaining limitations. It does not guarantee pixel-identical output.

No source photos or generated images are included in this repository.
