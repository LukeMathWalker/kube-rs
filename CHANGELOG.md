0.7.0 / 2019-05-12
==================
  * `apiVersion` and `kind` on output object now found under `typemeta`

0.6.0 / 2019-05-12
==================
  * Expose getter `Informer::version`
  * Exose ctor `Informer::from_version`
  * Expose more attributes in `Metadata`
  * `Informer::reset` convenience method added
  * `Informer::poll` no longer returns events straight
  * an `Informer` now caches `WatchEvent` elements into an internal queue
  * `Informer::pop` pops a single element from its internal queue
  * `Reflector::refresh` renamed to `Reflector::reset` (matches `Informer`)
  * `Void` type added so we can use `Reflector<ActualSpec, Void>`
    - removes need for Spec/Status structs:
    - `ReflectorSpec`, `ReflectorStatus` removed
    - `InformerSpec`, `InformerStatus` removed
    - `ResourceSpecMap`, `ResourceStatusMap` removed
  * `WatchEvents` removed
  * `WatchEvent` exposed, and now wraps `Resource<T, U>``

0.5.0 / 2019-05-09
==================
  * added `Informer` struct dedicated to handling events
  * Reflectors no longer cache `events` - see #6

0.4.0 / 2019-05-09
==================
  * ResourceMap now contains the full Resource<T,U> struct rather than a tuple as the value. => `value.metadata` is available in the cache.
  * Reflectors now also cache `events` to allow apps to handle them

0.3.0 / 2019-05-09
==================
  * `Named` trait removed (inferring from metadata.name now)
  * Reflectors now take two type parameters (unless you use `ReflectorSpec` or `ReflectorStatus`) - see examples for usage
  * Native kube types supported via `ApiResource`
  * Some native kube resources have easy converters to `ApiResource`
