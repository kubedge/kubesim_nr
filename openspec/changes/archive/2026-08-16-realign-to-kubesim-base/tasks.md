# Tasks — realign-to-kubesim-base

- [x] Wait for `kubesim_base` to publish the new tag (its multimodule-tag-realign change). — v0.1.25 published.
- [x] `go get` each kubesim_base sub-module this repo requires (`config` and/or `connected`/`grpc/go`) at the new `<tag>`. — all three → v0.1.25.
- [x] `go mod tidy`; confirm every kubesim_base require moved to `<tag>`. — done; go directive folded 1.20 → 1.26.0.
- [x] `go build ./... && go vet ./... && go test ./... -race` green. — build (`-o /dev/null`, root `cmd/` collision) + vet green; `go test` green (no test files → see test-coverage-uplift).
