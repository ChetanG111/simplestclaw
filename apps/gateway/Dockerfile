FROM node:22-slim

ENV NODE_ENV=production
WORKDIR /app

# Install only the gateway's runtime dependencies
COPY apps/gateway/package.json ./
RUN npm install --omit=dev

# Copy the gateway source
COPY apps/gateway/ ./

EXPOSE 3000

CMD ["node", "server.js"]
