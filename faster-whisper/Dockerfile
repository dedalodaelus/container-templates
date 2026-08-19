FROM lscr.io/linuxserver/faster-whisper:3.6.0-gpu

# Required by the "hass" extra in wyoming-faster-whisper 3.6.0
RUN /lsiopy/bin/pip install --no-cache-dir "aiohttp>=3.8,<4"

# Replace only the LinuxServer launcher
COPY --chmod=755 run /etc/s6-overlay/s6-rc.d/svc-whisper/run