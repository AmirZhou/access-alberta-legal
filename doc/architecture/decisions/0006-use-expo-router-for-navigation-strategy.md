# 6. Use Expo Router for navigation strategy

Date: 2025-06-30

## Status

Accepted

## Context

The Access Alberta Legal app requires a robust navigation system to handle:
- Multiple legal document categories and subcategories
- User authentication flows
- Search and filtering interfaces
- Bookmarks and user profiles
- Deep linking to specific legal documents

We need to choose between traditional React Navigation and Expo Router for our navigation strategy.

## Decision

We will use Expo Router as our navigation strategy for the Access Alberta Legal mobile app.

## Consequences

### Positive
- **File-based routing**: Intuitive folder structure mirrors app navigation
- **Type-safe navigation**: Built-in TypeScript support reduces runtime errors
- **Deep linking**: Automatic URL generation for sharing legal documents
- **Web compatibility**: Same codebase works for potential web version
- **Simplified setup**: Less boilerplate compared to React Navigation
- **Layout sharing**: Easy to create consistent headers/footers across sections

### Negative
- **Newer technology**: Less community resources than React Navigation
- **Expo dependency**: Tied to Expo ecosystem
- **Learning curve**: Team needs to learn file-based routing concepts

### Risks
- Migration complexity if Expo Router proves insufficient
- Potential performance concerns with complex nested routes
