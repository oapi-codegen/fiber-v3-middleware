# Fiber v3 Middleware

⚠️ This README may be for the latest development version, which may contain unreleased changes. Please ensure you're looking at the README for the latest release version.

Middleware for the [Fiber v3 web server](https://github.com/gofiber/fiber) for use with [oapi-codegen](https://github.com/oapi-codegen/oapi-codegen).

> [!NOTE]
> Using Fiber v2? You want [`oapi-codegen/fiber-middleware`](https://github.com/oapi-codegen/fiber-middleware) instead.

## Validated request body value

By default, `OapiRequestValidator` and `OapiRequestValidatorWithOptions` enable kin-openapi's `openapi3filter.Options.KeepValidatedValue`, so the validated request body exposes the decoded value through a `ValidatedValue() any` method. This lets a handler, such as an oapi-codegen strict server, bind the exact value that passed validation instead of decoding the body a second time. Set `Options.DiscardValidatedValue` to `true` to turn this off, for example to limit memory retention for very large request bodies; it overrides `Options.Options.KeepValidatedValue`.

> [!NOTE]
> This middleware currently validates a copy of the request (built with Fiber's `adaptor.ConvertRequest`), so Fiber handlers do not yet receive the validated value. The default and the `DiscardValidatedValue` option exist for consistency with the other oapi-codegen middlewares and for a future change that exposes the value to handlers.

Licensed under the Apache-2.0.
