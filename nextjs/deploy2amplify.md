# To deploy Nextjs to amplify  

## If your first app/page.tsx contains 'use client' at the top

### set your next.config.js as follow  

```typescript
/** @type {import('next').NextConfig} */
const nextConfig = {
  compiler: {
    styledComponents: true,
  },
  output: 'export',
};

module.exports = nextConfig;
```

### set your amplify.yml as follow
```yml
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - npm install
    build:
      commands:
        - npm run build
  artifacts:
    baseDirectory: out # here is out
    files:
      - "**/*"
  cache:
    paths:
      - node_modules/**
```

## If your first app/page.tsx is purely a serverside  

### set your amplify.yml as follow
```yml
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - npm install
    build:
      commands:
        - npm run build
  artifacts:
    baseDirectory: .next
    files:
      - "**/*"
  cache:
    paths:
      - node_modules/**
```
