VERSION 0.7

FROM denoland/deno:alpine
WORKDIR /app
RUN apk add --no-cache tini
ENTRYPOINT ["/sbin/tini", "--"]

dist:
    COPY server.ts .
    RUN deno cache server.ts
    CMD ["deno", "run", "--allow-net", "./server.ts"]
    SAVE IMAGE --push theomessin/example
