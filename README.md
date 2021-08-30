# git-rev-parse-action

```
jobs:
  check_hash:
    outputs:
      src: ${{ steps.cache.outputs.cache-hit }}
    steps:
      - uses: actions/checkout@v2
      - uses: kyo-ago/git-rev-parse-action@v2
        id: cache
        with:
          target: |
            yarn.lock
            .github/workflows/on_push.yml
            src

  build_frontend:
    needs: check_hash
    if: needs.check_hash.outputs.src != 'true'
    steps:
      - uses: actions/checkout@v2
      # ...
```
