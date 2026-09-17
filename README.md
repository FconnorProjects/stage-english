# English Enforcer for Chub

A background Chub Stage that keeps character replies in English.

## What it does

- Appends an English-only instruction before every model generation.
- Detects Korean, Japanese, Chinese and several other non-Latin scripts in bot replies.
- If foreign-script text is detected, uses Chub's own `generator.textGen()` service to translate the reply into English.
- Replaces the original bot response with the English translation, so subsequent chat history also stays in English.
- Runs invisibly with `position: NONE`.

## Configuration

The Stage metadata exposes three settings:

- `force_english`: adds the English-only prompt instruction. Default: `true`.
- `auto_translate`: translates detected foreign-script replies. Default: `true`.
- `sensitivity`: `strict`, `balanced`, or `conservative`. Default: `balanced`.

## Deployment

This repository uses the Chub Stage template GitHub Actions workflow. Pushes to `main` should build and upload the Stage when the repository has a valid `CHUB_AUTH_TOKEN` Actions secret.
