

```
npm install --save-dev @hey-api/openapi-ts
mkdir -p src/api
npx @hey-api/openapi-ts --input ./docs/swagger.json --output src/api --client @hey-api/client-axios
```
 
```
src/api/
├── index.ts          # Main exports
├── types.gen.ts      # All API data types (37KB)
├── sdk.gen.ts        # All API functions (42KB)
├── client.gen.ts     # HTTP client configuration
├── config.ts         # Your configuration file
├── client/           # Client implementation
└── core/             # Core utilities
```

