# jsonrpcserver Change Log

## 4.0.5 (Sep 10, 2019)

- Include license in package.

## 4.0.4 (Jun 22, 2019)

- Use faster method of jsonschema validation
- Use inspect from stdlib, removing the need for funcsigs

## 4.0.3 (Jun 15, 2019)

- Update dependencies to allow jsonschema version 3.x
- Support Python 3.8

## 4.0.2 (Apr 13, 2019)

- Fix to allow passing context when no parameters are passed.

## 4.0.1 (Dec 21, 2018)

- Include exception in ExceptionResponse. Closes #74.

## 4.0.0 (Oct 14, 2018)

_The 4.x releases will support Python 3.6+ only._

- Dispatch now works only with `Methods` object. No longer accepts a
  dictionary or list.
- `dispatch` no longer requires a "methods" argument. If not passed, uses the
  global methods object.
- Methods initialiser has a simpler api - Methods(func1, func2, ...) or
  Methods(name1=func1, name2=func2, ...).
- No more jsonrpcserver exceptions. Calling code will _always_ get a valid
  JSON-RPC response from `dispatch`. The old `InvalidParamsError` is gone
  - instead do a regular `assert` on arguments.
- `response.is_notification` renamed to `response.wanted`, which is the
  opposite of is_notification. This means the original request was not a
  notification, it had an id, and does expect a response.
- Removed "respond to notification errors" option, which broke the
  specification. We still respond to invalid json/json-rpc requests, in which
  case it's not possible to know if the request is a notification.
- Removed the "config" module. Added external config file, `.jsonrpcserverrc`.
  (alternatively configure with arguments to dispatch)
- Removed the "six" dependency, no longer needed.
- Configure logging Pythonically.
- Add type hints
- Move tests to pytest
- Passing a context object to dispatch now sets it as the first positional
  argument to the method. `def fruits(ctx, color):`
- Check params with regular asserts.

## 3.5.6 (Jun 28, 2018)
- Add trim_log_values dispatch param. (#65)
- Fix a missing import

## 3.5.5 (Jun 19, 2018)
- Rewrite of dispatch(), adding parameters to configure the dispatch that were
  previously configured by modifying the `config` module. That module is now
  deprecated and will be removed in 4.0.

## 3.5.4 (Apr 30, 2018)
- Refactoring

## 3.5.3 (Dec 19, 2017)
- Allow requests to have any non-None id

## 3.5.2 (Sep 19, 2017)
- Refactor for Request subclassing

## 3.5.1 (Aug 12, 2017)
- Include context data in regular (synchronous) methods.dispatch

## 3.5.0 (Aug 12, 2017)
- Pass some context data through dispatch to the methods.
- Fix not calling notifications in batch requests.

## 3.4.3 (Jul 13, 2017)
- Fix AttributeError on batch responses

## 3.4.3 (Jul 12, 2017)
- Add `Response.is_notification` attribute

## 3.4.2 (Jun 9, 2017)
- Fix `convert_camel_case` with array params

## 3.4.1 (Oct 4, 2016)
- Disable logging in config
- Performance improved
- Fix async batch requests

## 3.4.0 (Sep 27, 2016)
- Added asyncio support. (Python 3.5+)
- Added a *methods* object to the jsonrpcserver module (so you can import
  jsonrpcserver.methods, rather than instantiating your own).
- Added methods.dispatch().

## 3.3.4 (Sep 22, 2016)
- Fix Methods.serve_forever in python 2 (thanks @bplower)

## 3.3.3 (Sep 15, 2016)
- Updated method of logging exception (thanks @bplower)

## 3.3.2 (Aug 19, 2016)
- Pass Methods named args onto MutableMapping
- Remove unused logger

## 3.3.1 (Aug 5, 2016)
- Allow passing dict to Methods constructor

## 3.3.0 (Aug 5, 2016)
- A basic HTTP server has been added.
