---
title: "Logging"
slug: "logging"
excerpt: ""
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Thu Feb 22 2024 13:08:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 22 2024 13:40:31 GMT+0000 (Coordinated Universal Time)"
---
Tatum comes with a built-in logger which can help you debug your application, display errors and warnings from the inner workings of TatumSDK. You can also use it to log your own messages.

Tatum comes with 3 builtin loggers:

- `TatumDevelopmentLogger` - formats messages for easy viewing terminal
- `TatumDevelopmentBrowserLogger` - formats messages for browser console
- `TatumProductionLogger` - avoids formatting where possible, wraps global console

You can pick choose which logger you use based on your needs.

By default, Tatum will use of the development loggers if you are running in development mode, and `TatumProductionLogger` if you are running in production mode. Of course, you can override this behaviour by passing your own logger to Tatum SDK.

```typescript
import { TatumSDK, TatumDevelopmentLogger } from "@tatumio/tatum"

const logger = new TatumDevelopmentLogger()

const tatum = await TatumSDK.init<Ethereum>({
  logger,
  // ...
})
```

# Log levels

Tatum supports 5 logging levels in order of severity:

- `TRACE`
- `DEBUG`
- `INFO`
- `WARN`
- `ERROR`

> 📘 By specifying a certain log level, all logs with a lower severity will be ignored

You can set the log level by passing `level` to any of our loggers' constructor.

```typescript
import { TatumDevelopmentLogger, LogLevel } from "@tatumio/tatum"

const logger = new TatumDevelopmentLogger({ level: LogLevel.DEBUG })

logger.trace("This is a trace message") // will not be logged
logger.debug("This is a debug message")
logger.error("Ooopsie!")
```

# Bring your own logger

You can also use your own logger, as long as it implements the following interface importable from `@tatumio/tatum`:

```typescript
interface Logger {
  trace(...args: any[]): void
  debug(...args: any[]): void
  info(...args: any[]): void
  warn(...args: any[]): void
  error(...args: any[]): void
}
```

> 📘 Many popular off-the-shelf loggers such as pino, loglevel or log4js already do so! You can use them without any additional configuration

 Alternatively, you can implement it yourself:

```typescript
const myLogger = {
  trace(...args) {},
  debug(...args) {},
  info(...args) {},
  warn(...args) {},
  error(...args) {},
}

const tatum = await TatumSDK.init<Ethereum>({
  network: Network.ETHEREUM,
  logger: myLogger,
})
```
