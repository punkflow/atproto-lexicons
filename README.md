# atproto-lexicons

AT Protocol Lexicon definitions published by PunkFlow. Schemas for creator-owned video infrastructure and related domains.

## What this is

This repository contains [AT Protocol Lexicon](https://atproto.com/specs/lexicon) definitions for video and creative work metadata. Lexicons are JSON schemas that describe record types stored in AT Protocol repositories (the same protocol that powers Bluesky).

These schemas exist so that video metadata can be:

- **Portable.** Records published to your AT Protocol repo are readable by any client that understands the schema.
- **Signed.** Each record is cryptographically signed by the creator's DID, making authorship verifiable.
- **Open.** No central platform decides what fields exist or how they're used.
- **Resilient.** Your metadata persists in your repo even if the platform that originally published it disappears.

## Why this exists

Mainstream video platforms (YouTube, TikTok, etc.) treat creator metadata as their property. Schemas are opaque, change without notice, and routinely get co-opted for AI training and derivative generation without creator consent.

This repo defines schemas with the opposite stance:

- **Explicit AI permissions** baked into every record, with creator-protective defaults
- **Structured credits** so collaborators are properly attributed, not buried in descriptions
- **Canon and version semantics** for serialized creative work
- **Sponsor disclosures** as first-class structured data, not buried in descriptions
- **Content warnings** as standardized vocabulary, not afterthoughts
- **Access models** that don't assume ad-supported as the default

The goal is infrastructure that embodies creator agency at the data layer, not just at the policy layer.

## What's inside

Current schemas:

- `lexicons/com/punkflow/video/episode.json` - Single video metadata record

More schemas will be added over time. Planned:

- `com.punkflow.video.channel` - Creator channel/profile metadata
- `com.punkflow.video.playlist` - Playlist/collection records
- `com.punkflow.video.series` - Richer series metadata
- `com.punkflow.video.viewerState` - Per-viewer watch state (separate from creator-published metadata)
- `com.punkflow.canon.entry` - Worldbuilding/canon documentation records
- `com.punkflow.canon.character` - Character profiles for serialized work

## Lexicon namespace

All schemas in this repo use the `com.punkflow.*` namespace, owned by PunkFlow (punkflow.com).

This namespace is intentional: it brands schemas that originate here while leaving room for community-contributed schemas under different namespaces. Schemas may eventually be contributed to the [Lexicon Community](https://github.com/lexicon-community) for shared standardization.

## Using these schemas

If you're building an AT Protocol client or app and want to read or write records of these types:

1. Reference the Lexicon ID in your record (e.g. `com.punkflow.video.episode`)
2. Validate records against the schema in this repo
3. Honor the AI permissions and other creator-protective fields

Schema implementation libraries are available in the AT Protocol ecosystem. See the [official AT Protocol documentation](https://atproto.com) for client SDKs in TypeScript, Python, and other languages.

## Honoring creator declarations

Schemas in this repo include creator-protective fields, especially `aiPermissions`, that downstream consumers should respect:

- **searchIndexing** allow/deny: whether AI search indexing is permitted
- **aiSummarization** allow/deny: whether AI summaries that displace clicks are permitted
- **semanticEmbedding** allow/deny: whether vector embedding for similarity matching is permitted
- **training** allow/deny: whether use as AI training data is permitted
- **generation** allow/deny: whether use as input for AI-generated derivatives is permitted
- **excerpting** allow/deny: whether AI extraction of clips/frames/snippets is permitted

When a field is missing or unspecified, the default is creator-protective: `searchIndexing` allowed, all others denied. Consumers building AI systems should treat missing declarations as denial of permission.

This is a structural statement, not just a policy. The schema embeds the principle that AI use of creator content requires explicit creator consent, not platform consent.

## Contributing

These schemas are published under the MIT License. They are open infrastructure: fork, extend, or adapt them for your own work.

If you're building something compatible and want to discuss schema design, reach out via Bluesky [@punkflow.com](https://bsky.app/profile/punkflow.com).

## License

MIT. See [LICENSE](LICENSE).
