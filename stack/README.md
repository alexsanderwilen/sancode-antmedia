# Portainer deployment notes

Use this directory for deployment examples only after the GHCR image has been built and tested.

Image reference:
`ghcr.io/alexsanderwilen/sancode-antmedia:3.1.0`

Ant Media uses multiple media ports and WebRTC commonly requires UDP connectivity; routing only the web management UI through Traefik is not sufficient for all streaming protocols. Confirm the exact ports and external-IP/WebRTC settings for your VPS before deploying.

**Do not replace the existing `antmedia-server` stack until the new image has been tested.** Back up the current stack definition and persistent data first. A Swarm stack may require host-mode published ports for UDP/media traffic, while HTTP/HTTPS management can be routed through Traefik separately.
