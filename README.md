# Distributed Logical Time

Typescript implementation of [Distributed Logical Time](https://longform.asmartbear.com/distributed-logical-time/).

Features:

* Timestamp fits into a Javascript `number`, as a precise integer (i.e. less than 2^53 bits).
* Extremely fast, because system-time is read only occasionally.
* No other library dependencies.

100% test coverage.

## Usage

```typescript
const lt = new LogicalTime()
console.log(lt.now)     // 3120866120
console.log(lt.now)     // 3120866121
console.log(lt.now)     // 3120866122
lt.useSystemTimeNext()  // will refresh system time on the next timestamp,
                        // even if in a back-off period.
lt.update(t)            // ensure we are later than `t` including an
                        // additional random interval, used to synchronize
                        // but hopefully not duplicate another machine.
```

## Development Usage

Build:

```bash
npm run build
```

Unit tests:

```bash
npm run test
```

Unit tests, refreshed live:

```bash
npm run watch
```

Prepare for release (e.g. run tests and bump version number), then publish to npm:

```bash
npm run release && npm publish
```
