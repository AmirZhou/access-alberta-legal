# 2. Pnpm as package manager

Date: 2025-06-25

## Status

Accepted

## Context

The Access Alberta Legal app is a full-stack app, so that it needs it's own backend and frond-end. The team needs a way to manage the architecture of multiply apps.

## Decision

We decided to use the pnpm workspace to implement a mono-repo structure.

## Consequences

- The app then be self contained in a shared project repo, which can serve all apps, pacaages, and docs of the project.
