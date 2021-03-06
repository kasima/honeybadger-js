# Change Log
All notable changes to this project will be documented in this file. See [Keep a
CHANGELOG](http://keepachangelog.com/) for how to update this file. This project
adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased][unreleased]

## [0.4.6] - 2017-03-27
### Fixed
- Fixed a bug which caused `window.url` to be overridden.
- Updated typescript definitions.

## [0.4.5] - 2017-02-23
### Fixed
- Fix bug where default properties "name" and "message" on error objects were
  not reported by `Honeybadger.notify`.

## [0.4.4] - 2017-02-23
### Added
- Metadata such as context can now be added to thrown errors via properties.
- The `async` config option can be enabled to make requests asynchronously when
  using XHR.
- Type declarations for TypeScript. See
  [honeybadger-js.d.ts](./honeybadger-js.d.ts)
- Camel case is now preferred for config options -- use `apiKey` instead of
  `api_key` and `projectRoot` instead of `project_root`. The old options are
  deprecated but will continue to be supported for the foreseeable future.

### Fixed
- Fixed a bug when including objects created without a prototype (i.e. with
  `Object.create(null)` in context data.
- Enforce strict mode.

## [0.4.3] - 2016-09-26
### Added
- Added option to send params and cookies.

## [0.4.2] - 2016-04-14
### Fixed
- Fixed a bug where logging wasn't available when request setup failed due to an
  error, which could result in an uncaught error being thrown.
- Check for presence of addEventListener before instrumenting it.

## [0.4.1] - 2016-02-25
### Fixed
- Fixed a bug where our DOMContentLoaded event listener wasn't added until after
  the event had already fired which prevented requests from being made.

## [0.4.0] - 2016-02-22
### Added
- Support reading configuration from data attributes on script tag.
- Improved `window.onerror` handling for IE 10+.
- A call stack is now generated in IE < 10 when reporting errors manually via
  `Honeybadger.notify`.
- Support for CommonJS and AMD.
- Example projects added for Browserify, webpack and RequireJS. (See
  [examples/](./examples))
- Test suite is now executed against a browser matrix (IE 6+) on TravisCI
  (using Sauce Labs).

### Changed
- Underlying code has been rewritten in plain JavaScript (CoffeeScript
  development dependency removed).
- The `onerror` configuration option is now enabled by default. All unhandled
  errors will be reported automatically.
- `Honeybadger.Client()` has been renamed to `Honeybadger.factory()`.
- `context` and other objects now have a maximum depth of 5 nested objects.
  When the maximum depth is reached, recursion will be halted with the value
  "[MAX DEPTH REACHED]". Maximum depth can be configured via the `max_depth`
  option.

### Removed
- The `timeout` configuration option has been removed (this may be reintroduced
  in the future, or we may limit the number of connections per browser session
  instead).

## [0.3.1] - 2015-08-13
### Fixed
- Sanitization bugfixes.

## [0.3.0] - 2015-07-28
### Added
- Sanitize circular data structures.
- Generate source map.

## [0.2.0] - 2015-01-16
### Added
- Use CORS to send data via POST when available.
- Improved error grouping.
