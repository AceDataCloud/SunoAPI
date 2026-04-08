# SunoAPI

API documentation and integration guides for Suno AI music generation on AceDataCloud.

## Project Structure

```
README.md      — Service intro page with features, pricing, and examples
docs/          — Per-endpoint integration guides (markdown)
  suno_audios_generation_api_integration_guide.md
  suno_lyrics_generation_api_integration_guide.md
  suno_mashup_lyrics_generation_api_integration_guide.md
  suno_midi_api_integration_guide.md
  suno_mp4_api_integration_guide.md
  suno_persona_api_integration_guide.md
  suno_style_api_integration_guide.md
  suno_tasks_api_integration_guide.md
  suno_timing_api_integration_guide.md
  suno_upload_api_integration_guide.md
  suno_vox_api_integration_guide.md
  suno_wav_api_integration_guide.md
```

## Sync from Docs

When working on an auto-sync issue (labeled `auto-sync`), follow these rules:

1. **Compare guides** — Each API endpoint should have a corresponding guide in `docs/`. Add new guides for new endpoints, matching the naming pattern.
2. **Model versions** — Update model version tables in guides and README to match the latest from Docs.
3. **Parameters** — Update parameter documentation to match the OpenAPI spec.
4. **Examples** — Update code examples (curl, Python, JavaScript) with latest models and parameters.
5. **README** — Update feature list, model table, and pricing info.
6. **PR title** — Use format: `sync: <description> [auto-sync]`

## Writing Style

- English documentation
- Include curl examples for every endpoint
- Include model version table with launch dates and limits
- Include parameter reference tables
- Use consistent heading structure: Overview → Application → Basic Usage → Advanced → Response
