# Tasks — buildx-multiarch-image

- [ ] Confirm buildx + a running builder (colima on Apple-Silicon). — deferred to Finish (`colima start`); needs a live builder.
- [x] For each built image, add a buildx target `docker buildx build --platform linux/arm64 -t <image>:<tag>` (add `,linux/amd64` only if still needed). — `docker-buildx` target (`--platform=$(PLATFORMS)`, `-f build/Dockerfile.buildkit`) from the lte graft.
- [x] Make each Dockerfile multi-stage (compile per TARGETOS/TARGETARCH; don't copy a prebuilt amd64 binary). — `build/Dockerfile.buildkit` (`FROM --platform=$BUILDPLATFORM golang:1.26`).
- [x] Remove the `_AMD64/_ARM64V8/_ARM32V7` image-name variables. — retired (commented out) in the Makefile.
- [ ] `docker buildx imagetools inspect` each image → manifest list incl. linux/arm64. — deferred to Finish (needs a live builder).
- [ ] If deployed by an operator, update that operator's example CR to the arch-independent name. — N/A: this repo is a plain Go app (light on Kubernetes), not operator-deployed.
