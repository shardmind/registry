# ShardMind Registry

The shard index for [ShardMind](https://github.com/breferrari/shardmind). It maps a short name to the GitHub repository that serves the shard, so

```sh
shardmind install breferrari/obsidian-mind
```

resolves without the `github:` prefix. A shard that is not listed here still installs straight from GitHub:

```sh
shardmind install github:owner/repo
```

## The index

`index.json` at the root of `main`:

```json
{
  "schema_version": 1,
  "shards": {
    "breferrari/obsidian-mind": {
      "repo": "breferrari/obsidian-mind",
      "latest": "9.0.1",
      "versions": ["9.0.1", "9.0.0", "8.6.0"]
    }
  }
}
```

- `schema_version` is the index format. It changes only when an older ShardMind would misread the index; a ShardMind that meets a newer format asks to be updated.
- `shards` is keyed by the name users type, `<namespace>/<name>`.
- `repo` is the GitHub `owner/name` that serves the shard. It may differ from the key after a rename or a transfer.
- `versions` lists release versions, semver without a `v`, newest first. Each one is a tag `v<version>` in `repo` whose `.shardmind/shard.yaml` declares that version.
- `latest` is one of `versions`, and is what a name without `@version` installs.

The format is specified in ShardMind's [IMPLEMENTATION.md](https://github.com/breferrari/shardmind/blob/main/docs/IMPLEMENTATION.md) under "The registry index".

## Listing a shard

Open a pull request that adds or updates the shard's entry in `index.json`.

## License

[MIT](LICENSE)
