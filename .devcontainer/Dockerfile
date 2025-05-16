FROM jellyfin_ffmpeg_runner_stage:ice_master-amd64 AS ffmpeg_image

FROM mcr.microsoft.com/devcontainers/dotnet:9.0-bookworm
USER root

RUN apt-get update && apt-get install -y net-tools iproute2 && apt-get clean

RUN mkdir /workspaces

COPY --from=ffmpeg_image /opt/ffmpeg_ice /opt/ffmpeg_ice
COPY --from=ffmpeg_image /usr/lib/x86_64-linux-gnu/libvpx* /usr/lib/x86_64-linux-gnu/libmp3lame* \
/usr/lib/x86_64-linux-gnu/libnuma* /usr/lib/x86_64-linux-gnu/libx26* /usr/lib/x86_64-linux-gnu/ \
x86_64-linux-gnulibxcb* /usr/lib/x86_64-linux-gnu/libfontconfig* /usr/lib/x86_64-linux-gnu

USER vscode

CMD exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"