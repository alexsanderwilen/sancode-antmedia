# Sancode Ant Media Community

Build and publish a Docker image for the **official Ant Media Server Community Edition** to GitHub Container Registry (GHCR).

- Source release: [Ant Media Server releases](https://github.com/ant-media/Ant-Media-Server/releases)
- Official Docker build recipe: [ant-media/Scripts/docker/Dockerfile_Process](https://github.com/ant-media/Scripts/blob/master/docker/Dockerfile_Process)
- License: check the [Community Edition license](https://github.com/ant-media/Ant-Media-Server/blob/master/COMMUNITY_EDITION_LICENSE) and the terms accompanying each release before redistribution.

This repository does not contain the Ant Media binary ZIP. The workflow downloads the selected release from the official Ant Media GitHub release page when a build is requested.

## Build and publish

1. Open **Actions** in this repository.
2. Select **Build and publish Ant Media Community image**.
3. Click **Run workflow**.
4. Enter a released Community version, initially `3.1.0`.
5. Wait for the workflow to finish successfully.

The workflow publishes these tags:

- `ghcr.io/alexsanderwilen/sancode-antmedia:3.1.0`
- `ghcr.io/alexsanderwilen/sancode-antmedia:community`

The `community` tag is convenient, but for production deployments prefer a pinned version tag.

### First-time GHCR setup

The workflow uses the automatically provided `GITHUB_TOKEN`; no personal access token should be committed to this repository. In repository settings, ensure Actions are allowed and the workflow has read/write access to packages.

After the first successful publication, open the package in GitHub under your profile's **Packages** and change its visibility to **Public** if you want your VPS to pull without authentication. The source repository being public does not automatically make the container package public.

## Important notes

- This workflow builds the selected release on GitHub-hosted runners. The official Community ZIP is large, so the first build may take several minutes.
- The workflow is manually triggered or can be triggered by pushing a version tag such as `v3.1.0`.
- A successful build does not by itself prove that streaming, WebRTC, RTMP, HLS, or your Traefik/Portainer configuration works in your environment. Validate those separately before replacing a running service.
- This repository does not automatically deploy to your VPS and does not modify your Portainer stacks.
- Do not add server passwords, license keys, tokens, `.env` files, or VPS-specific secrets to this repository.
