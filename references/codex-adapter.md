# Codex adapter (optional)

Read only when using Codex's built-in image generation. Other agents use their own tools and ignore these platform-specific names.

- Apply the available `imagegen` skill and follow its generation, saving, and delivery rules.
- Inspect local sources with `view_image` before generation.
- Use built-in `image_gen` with `transparent_background: true`.
- For local sources use `referenced_image_paths`; for conversation-only sources use the smallest `num_last_images_to_include` covering the source. Never supply both.
- Do not silently switch to a paid CLI/API fallback. Explain unavailable capabilities and offer the assembled prompt or a user-authorized fallback.
- `agents/openai.yaml` is optional display metadata, not core rendering instructions.
