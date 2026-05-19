# Generic Vendor Support

The project supports dynamically adding vendors without creating new command or subagent files.

Example:

```text
# Mistral

## API / Closed-Weight Models

- Models: ...
- Pricing: ...
```

Then run:

```text
/track-vendor Mistral
```

This generates:

```text
drafts/mistral.md
```

Then run:

```text
/generate-report
```

The new vendor will automatically appear in `models.md`.

`/track-all` also supports automatically scanning additional vendors in `links.md`.
