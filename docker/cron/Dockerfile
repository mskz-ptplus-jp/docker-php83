FROM debian:bullseye-slim

RUN apt update && apt install -y \
    cron \
    php

CMD ["cron", "-f"]
