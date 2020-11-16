# Explore accidental pushed secrets in github
Secret has been deleted with
```bash
java -jar bfg.jar --delete-files secret.txt --no-blob-protection accidental-secrets-pushed.git
```

It is gone from master (good)

It is not gone from these places:
- [PR adding secret.](https://github.com/devthat/accidental-secrets-pushed/pull/1/files) Branch was merged and deleted. Still deleted.
- [Original commit.](https://github.com/devthat/accidental-secrets-pushed/commit/a60d64e8a5e0358f25f0cfbfcfcf6e403e2e4dc9) Not referenced by any branch but still reachable by link.
- [PR added after secret.](https://github.com/devthat/accidental-secrets-pushed/tree/branch-with-more-stuff) Branch was originally merged and deleted. Then restored after running bfg.
