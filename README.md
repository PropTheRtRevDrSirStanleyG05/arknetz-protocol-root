# arknetz-protocol-root

Protocol-root manifest for ArkNetzWebWeaver by STANBEYOND (MIT).

This repo holds one file, `manifest.json`: the current protocol version,
`DEFAULT_ROOT_REPO`, the master public identity (`PropTheRtRevDrSirStanleyG05`), the shard repo
lists and shard keys, directory categories, feed shards, mirror locations, and
the Zstd dictionary pointer. It never grows. Clients fetch this first, then go
straight to the shard they need; if it is down, they fall back to a cached copy
in IndexedDB.

- Protocol: https://github.com/PropTheRtRevDrSirStanleyG05/arknetz-protocol
- Client: https://github.com/PropTheRtRevDrSirStanleyG05/ArkNetzWebWeaver
- Spec: `PROTOCOL.md` in arknetz-protocol (v0.1.0, 2026-11-20).

`directoryCategories` is an additive manifest field (new in this seed): it makes
the per-category directory repos discoverable instead of hard-coding the default
list (`tech`, `cinema`, `games`) in the client. Older clients ignore unknown
fields, so this is a minor, backwards-compatible addition.

`pendingRepos` lists the central repos that do not exist on GitHub yet
(blocked 2026-11-21 by GitHub's "created too many repositories, too
quickly" rate limit). The 16+16 shard lists are the addressing scheme —
a domain hashes to its shard whether or not that repo exists yet — while
`pendingRepos` is the honest existence record. Clients treat a missing
shard repo as empty.
