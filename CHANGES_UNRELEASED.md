**See [the release process docs](docs/howtos/cut-a-new-release.md) for the steps to take when cutting a new release.**

# Unreleased Changes

[Full Changelog](https://github.com/mozilla/application-services/compare/v0.27.2...master)

## FxA

### Breaking Changes

- `FirefoxAccount.ensureCapabilities` now takes a set of capabilities
   as a parameter. All the device registered "capabilities" such as Send
   Tab will be replaced by the passed set of new capabilities.

## Push

### Breaking Changes

- `PushManager.verifyConnection()` now returns a boolean. `true`
  indicates the connection is valid and no action required, `false`
indicates that the connection is invalid. All existing subscriptions
have been dropped. The caller should send a `pushsubscriptionchange`
to all known apps. (This is due to the fact that the Push API does
not have a way to send just the new endpoint to the client PWA.)
[#1114](https://github.com/mozilla/application-services/issues/1114)

- `PushManager.unsubscribe(...)` now will only unsubscribe a single
  channel. It will return `false` if no channel is specified or if the
channel was already deleted. To delete all channels for a given user,
call `PushManager.unsubscribeAll()`.
[#889](https://github.com/mozilla/application-services/issues/889)
