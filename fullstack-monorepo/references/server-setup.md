# Server Setup Reference

Prefer:
```text
backend/src/app.ts
backend/src/server.ts
```

`app.ts` configures Express. `server.ts` starts the process.

Typical `app.ts` order:
1. configuration
2. Helmet
3. CORS
4. JSON/urlencoded parsers with size limits
5. cookie-parser
6. request logging
7. request ID/correlation ID
8. health/readiness
9. API routes
10. 404 handler
11. centralized error handler

Example shape:
```ts
const app = express();

app.use(helmet());
app.use(cors(corsOptions));
app.use(express.json({ limit: env.BODY_LIMIT }));
app.use(cookieParser());
app.use(morgan(env.LOG_FORMAT));

app.get("/health", healthHandler);
app.use("/api", apiRouter);

app.use(notFoundHandler);
app.use(errorHandler);

export { app };
```

`server.ts` should import the app, read validated config, listen, and handle graceful shutdown. Keep it small.

Use one configuration module such as `src/config/env.ts`; do not scatter `dotenv.config()` across features.
