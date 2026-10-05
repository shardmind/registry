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
    "breferrari/obsidian-mind": { "repo": "breferrari/obsidian-mind" }
  }
}
```

- `schema_version` is the index format. It changes only when an older ShardMind would misread the index; a ShardMind that meets a newer format asks to be updated.
- `shards` is keyed by the name users type, `<namespace>/<name>`.
- An entry is just `repo`: the GitHub `owner/name` that serves the shard. It may differ from the key after a rename or a transfer.

Versions are not listed here. They come from the shard's own GitHub releases: a name resolves exactly as `github:<repo>` would, so `shardmind install breferrari/obsidian-mind` installs the newest stable release and `@9.0.1` installs that tag. A shard's new release needs no change to this repo.

The format is specified in ShardMind's [IMPLEMENTATION.md](https://github.com/breferrari/shardmind/blob/main/docs/IMPLEMENTATION.md) under "The registry index".

## Listing a shard

Open a pull request that adds the shard's entry to `index.json`. The shard must install with `shardmind install github:<owner>/<repo>`.

## License

[MIT](LICENSE)
