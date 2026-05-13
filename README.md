# amalgame-math-vec

Pure-Amalgame **Vec3 / Vec4 / Mat4** for [Amalgame](https://github.com/amalgame-lang/Amalgame).
Column-major 4×4 matrix math (OpenGL convention), scalar 3D and 4D
vectors, translate / scale / rotate primitives. Designed for games
and graphics where you push matrices straight into a `glUniformMatrix4fv`
without transposing.

Originally bundled in amc's `src/stdlib/math_vec.am` (with the
runtime impl in `runtime/Amalgame_Math_Vec.h`); extracted into
this external package as part of the framework split (post-v0.7.5).
Companion package: [`amalgame-math`](https://github.com/amalgame-lang/amalgame-math)
ships the rest of `Amalgame.Math`.

## Install

```bash
amc package add math-vec                 # via curated index
amc package add github.com/amalgame-lang/amalgame-math-vec@v0.1.0
```

Requires **amc 0.7.6+** for the facade pre-compile pipeline.

## Surface

```amalgame
import Amalgame.Math.Vec

class Program {
    public static void Main() {
        let a = new Vec3(1.0, 2.0, 3.0)
        let b = new Vec3(4.0, 5.0, 6.0)
        let dot: float = a.Dot(b)              // 32.0
        let cross: Vec3 = a.Cross(b)
        let len: float = a.Length()            // sqrt(14)
        let unit: Vec3 = a.Normalize()

        let m = Mat4.Identity()
        let r = Mat4.RotateZ(0.785398)         // 45° (radians)
        let mr: Mat4 = m.Multiply(r)

        let v = new Vec4(1.0, 0.0, 0.0, 1.0)
        let v2: Vec4 = r.TransformVec4(v)      // rotated vector
    }
}
```

## Conventions

- Matrices are 4×4 column-major (OpenGL).
- `Vec4.W` is the homogeneous coordinate (1 = position, 0 = direction).
- Rotations are in radians.
- Mat4 internally stores 16 named float fields (`M00..M33`) for
  per-cell access without `List.Get(i)` indirection — keeps hot
  matrix math allocator-free per operation.

## Tests

```bash
./tests/run_tests.sh /path/to/amc
```

## License

Apache-2.0 — see `LICENSE`. No vendored third-party code.
