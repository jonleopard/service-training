# 36. Self Shutdown

Certain error conditions only occur because of programmer error. In those known
cases we can't let the service continue to run. The application must shut down.

- Pass the signal channel from `func main` down to the web framework.
- Add a special error type in `web/errors.go` that represents a shutdown error.
- Let the error return up from the `ErrorHandler` middleware.
- Make the top level web function detect unhandled errors and use the channel to shut the application down.

## File Changes:

```
Modified cmd/sales-api/internal/handlers/check.go
Modified cmd/sales-api/internal/handlers/routes.go
Added    internal/mid/panics.go
```