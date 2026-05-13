# NOTICE — amalgame-math-vec

## Authorship

Copyright 2026 Bastien Mouget. The Amalgame facade code in this
repository is original work — see `facade.am` and the
`amalgame.toml` manifest.

This package is part of the Amalgame ecosystem
([github.com/amalgame-lang/Amalgame](https://github.com/amalgame-lang/Amalgame)).
It was extracted from amc's bundled `src/stdlib/math_vec.am`
(with the runtime impl originally in `runtime/Amalgame_Math_Vec.h`)
during the framework split (post-v0.7.5).

## License

Licensed under the Apache License, Version 2.0 — see `LICENSE`.

## Third-party content

None. The facade is 100% pure-Amalgame; the two `@c { … }` blocks
delegate to libm `sqrt` (Vec3.Length) and `cos`/`sin` (Mat4 Rotate
helpers), which the host C toolchain provides.
