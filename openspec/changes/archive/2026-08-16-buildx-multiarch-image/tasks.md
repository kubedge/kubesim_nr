# Tasks — buildx-multiarch-image

- [x] Confirm buildx + a running builder (colima on Apple-Silicon). — colima running; `multiarch` docker-container builder (buildkit v0.32.2) advertises linux/arm64 + linux/amd64.
- [x] For each built image, add a buildx target `docker buildx build --platform linux/arm64 -t <image>:<tag>` (add `,linux/amd64` only if still needed). — `docker-buildx` target (`--platform=$(PLATFORMS)`, `-f build/Dockerfile.buildkit`) from the lte graft.
- [x] Make each Dockerfile multi-stage (compile per TARGETOS/TARGETARCH; don't copy a prebuilt amd64 binary). — `build/Dockerfile.buildkit` (`FROM --platform=$BUILDPLATFORM golang:1.26`).
- [x] Remove the `_AMD64/_ARM64V8/_ARM32V7` image-name variables. — retired (commented out) in the Makefile.
- [x] `docker buildx imagetools inspect` each image → manifest list incl. linux/arm64. — multi-arch build produced manifest list `sha256:0d757ce7…` with `linux/arm64` (`sha256:e7a5236e…`) + `linux/amd64` (`sha256:a65afc91…`); verified via the OCI export (built without `--push`, so nothing hit Docker Hub).
- [ ] If deployed by an operator, update that operator's example CR to the arch-independent name. — N/A: this repo is a plain Go app (light on Kubernetes), not operator-deployed.
