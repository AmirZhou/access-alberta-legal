# Stage 1: Base setup and dependency installation
FROM node:18-alpine AS base
RUN corepack enable pnpm && corepack install -g pnpm@10.12.3
RUN apk add --no-cache libc6-compat

# Stage 2: Builder Stage, Dependency and build
FROM base AS builder
ENV NODE_ENV=production
WORKDIR /app

# Copy workspace configuration and root package.json
COPY package.json pnpm-lock.yaml pnpm-workspace.yaml ./

# Copy the acl-api package.json
COPY apps/acl-api/package.json ./apps/acl-api/

# Install dependencies for the entire workspace
RUN pnpm install --frozen-lockfile || pnpm install

# Copy source code for acl-api
COPY apps/acl-api/src ./apps/acl-api/src
COPY apps/acl-api/nest-cli.json ./apps/acl-api/
COPY apps/acl-api/tsconfig.json ./apps/acl-api/
COPY apps/acl-api/tsconfig.build.json ./apps/acl-api/

# Build the acl-api application
RUN cd apps/acl-api && pnpm run build

# Stage 3: Production stage
FROM node:18-alpine AS production
RUN corepack enable pnpm && corepack install -g pnpm@10.12.3
RUN apk add --no-cache libc6-compat

WORKDIR /app

# Copy workspace configuration
COPY package.json pnpm-lock.yaml pnpm-workspace.yaml ./
COPY apps/acl-api/package.json ./apps/acl-api/

# Install only production dependencies
RUN pnpm install --frozen-lockfile --prod || pnpm install --prod

# Copy built application
COPY --from=builder /app/apps/acl-api/dist ./apps/acl-api/dist

WORKDIR /app/apps/acl-api

EXPOSE 3000
CMD ["node", "dist/main.js"]




