# Chatterbox TTS - Colab Notebook

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/manzardev/chatterbox-tts-colab/blob/main/chatterbox-tts-colab.ipynb)

A ready-to-run Google Colab notebook for **Chatterbox**, an open-source, state-of-the-art voice cloning text-to-speech model by Resemble AI.

Clone any voice from a short audio sample and generate speech in that voice, right in your browser — no local setup, GPU included via Colab's free tier.

## What this fixes

The official install has a few dependency conflicts on Colab that this notebook works around:
- **TensorFlow/protobuf conflict** — `transformers` tries to import TensorFlow, which needs a newer `protobuf` than Chatterbox needs. This notebook removes TensorFlow so it's never triggered.
- **huggingface_hub version mismatch** — pinned to a compatible range so imports don't break.
- **Unquoted version specifiers** — fixed a shell-parsing bug where `>=` in pip install commands was being interpreted as file redirection instead of a version constraint.

## What's included

A Gradio web UI where you can:
- Upload a voice sample (WAV, ~10-30 seconds)
- Type text to synthesize
- Adjust exaggeration and CFG weight for expressiveness
- Generate and play back the cloned voice, saved to your Google Drive

## How to use

1. Click the "Open in Colab" badge above
2. Go to **Runtime → Change runtime type → T4 GPU**
3. Run **Cell 1** (installs dependencies, then restarts the kernel — this is expected, just wait for it to finish)
4. Run **Cell 2** (loads the model, mounts Google Drive)
5. Run **Cell 3** (launches the Gradio UI — click the `*.gradio.live` link it prints)
6. Upload a voice sample, type your text, hit Generate

## Notes

- Free Colab sessions disconnect after periods of inactivity or after ~12 hours — you'll need to rerun the cells to get a fresh session and a new Gradio link.
- Cell 3 auto-loads the model if it's missing from memory, so you don't strictly need to run Cell 2 first — but running cells in order avoids confusion.
- Voice samples work best when clean, ~10-30 seconds, minimal background noise.

## Credits

Built on [Chatterbox TTS](https://github.com/resemble-ai/chatterbox) by Resemble AI (MIT licensed).

## Disclaimer

This tool is for legitimate use cases (content creation, accessibility, dubbing, etc.). Only clone voices you have permission to use. Don't use it to impersonate people without consent.
