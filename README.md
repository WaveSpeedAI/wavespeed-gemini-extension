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

Qwen Code installs Gemini extensions as-is:

```bash
qwen extensions install WaveSpeedAI/wavespeed-gemini-extension
```

## What the agent can do with it

```bash
# text → image (default model: Seedream 5 Pro)
wavespeed generate image "a cyberpunk skyline at golden hour" --json

# edit a local image (uploaded automatically via @path)
wavespeed edit image "replace the background with a sunlit kitchen" --image @./input.jpg --json

# image → video (default model: Seedance 2.5); price it first, nothing is submitted
wavespeed generate video "subtle parallax" --first-frame @./hero.jpg --estimate --json

# any other model on the platform
wavespeed run <model-id> -p "..." --json
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
