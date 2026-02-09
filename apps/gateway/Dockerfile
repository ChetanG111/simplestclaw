#
# Build from the repository root:
#   docker build -f apps/gateway/Dockerfile -t simplestclaw-gateway .
#

FROM node:22-slim

ENV NODE_ENV=production
WORKDIR /app

# Enable pnpm and install only the gateway's runtime dependencies (cached layer)
RUN corepack enable pnpm
COPY pnpm-lock.yaml pnpm-workspace.yaml package.json ./
COPY apps/gateway/package.json apps/gateway/package.json
RUN pnpm install --filter @simplestclaw/gateway --production

# Copy the gateway source
COPY apps/gateway/ apps/gateway/

EXPOSE 3000

CMD ["pnpm", "--filter", "@simplestclaw/gateway", "start"]
