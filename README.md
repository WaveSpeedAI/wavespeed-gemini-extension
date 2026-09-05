# WaveSpeed extension for Gemini CLI

A [Gemini CLI](https://geminicli.com) extension that lets the agent generate and edit AI media — image, video, audio, 3D — through the [WaveSpeed](https://wavespeed.ai) platform, using the open-source [`@wavespeed/cli`](https://github.com/WaveSpeedAI/wavespeed-cli).

Every model on the platform is one `wavespeed run <model-id>` call. The bundled skill teaches the agent the find → inspect → run pattern: search the live catalog, read any model's input schema, execute it — including uploading local files with the `@path` marker and quoting prices before running.

## Requirements

- Node.js ≥ 18
- The WaveSpeed CLI: `npm install -g @wavespeed/cli`
- A WaveSpeed account — `wavespeed login` opens the key page at [wavespeed.ai](https://wavespeed.ai) and handles the rest

## Install

```bash
gemini extensions install https://github.com/WaveSpeedAI/wavespeed-gemini-extension
```

## What the agent can do with it

```bash
# text → image
wavespeed run bytedance/seedream-v5.0-pro -p "a cyberpunk skyline at golden hour" --json

# edit a local image (uploaded automatically via @path)
wavespeed run bytedance/seedream-v5.0-pro/edit -p "replace the background with a sunlit kitchen" \
  -i images='["@./input.jpg"]' --json

# image → video
wavespeed run wavespeed-ai/minimax-h3/image-to-video -p "subtle parallax" -i image=@./hero.jpg --json

# check the cost before running anything
wavespeed price bytedance/seedream-v5.0-pro -i resolution=2k
```

## Same skill, other agents

- Claude Code / Cursor / Codex: `wavespeed skill install`
- OpenCode: loads the installed skill as-is (`.claude/skills/` is on its search path)
- DeepSeek Harness: [WaveSpeedAI/wavespeed-dsh-skill](https://github.com/WaveSpeedAI/wavespeed-dsh-skill)
- Kimi Code CLI: [WaveSpeedAI/wavespeed-kimi-plugin](https://github.com/WaveSpeedAI/wavespeed-kimi-plugin)

## License

[MIT](LICENSE) — same as the CLI.

---

**[WaveSpeed AI](https://wavespeed.ai/)** — AI image & video generation platform.
Try it in the browser: **[Image generator](https://wavespeed.ai/image-generator)** · **[Video generator](https://wavespeed.ai/video-generator)**
