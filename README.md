# reference-store

What an id written in prose names, who may see it, and where its page is.

Chats and pages draw ids such as `prediction_000012`, `repo:dash` or `dash@8487d32` as chips. reference-store holds the one list of those reference types — how each id looks, which service owns it, which field names a record, a few fields worth showing, its page — and looks ids up in the stores that own them, for a caller, under that caller's access.

```bash
curl -s localhost:8343/types | jq '.types[0]'
curl -s -X POST localhost:8343/resolve -H 'X-Reference-Store-Service-Token: …' \
  -d '{"ids":["prediction_000012","repo:dash"]}'
```

It has no database. It trusts `X-Principal-Id`, so it listens on loopback and is reached through llm-bridge-server's gateway. `AGENTS.md` says how it works.

MIT licensed.
