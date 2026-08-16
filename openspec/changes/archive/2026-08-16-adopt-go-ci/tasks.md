# Tasks — adopt-go-ci

- [x] From the meta session, run `/alemax:update-skills` so the class-M set (incl. `ci.yml`) is staged for this repo. — broadcast `meta-broadcast/deliver-class-m-templates-ciyml--hygiene` staged.
- [x] In this repo's session, run `/alemax:complete-update` to apply the update branch onto the working branch. — cherry-picked onto `main`.
- [x] Confirm `.github/workflows/ci.yml` present and its jobs gate on `go.mod`. — graft's lte `ci.yml` supersedes the broadcast one; go jobs use `go-version-file: go.mod`.
- [ ] Trial push the branch; confirm `go-build`/`go-vet`/`go-test`/`golangci-lint` are green. — deferred to the PR (CI runs on push); locally build/vet/test green.
- [x] Confirm the rest of class-M landed: `.editorconfig`, `.gitattributes`, `.github/*`, `dependabot.yml`, `.pre-commit-config.yaml`, `bin/set-secret.sh`. — all present (`dependabot.yml` carries `github-actions` + `gomod`).
