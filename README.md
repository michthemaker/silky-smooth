### GitHub description (short)

```
Experimental graphics primitives in Silk — pixels, framebuffers, PPM, and the path toward a smooth design library.
```

### README.md

```markdown
# silky-smooth

Experimental graphics primitives written in [Silk](https://silklang.org/).

Early work toward a small, explicit design/graphics library: pixels, frame buffers, simple rendering, and the surrounding infrastructure needed to grow it.

## Status

Very early. Currently exploring:

- Bit-packed `Pixel` (RGBA)
- Frame buffers
- PPM (P3) output
- Ownership-friendly writers and format helpers
- Basic geometry and conversion traits (`From` / `Into`)
- Filesystem usage for writing results

This is primarily a learning and experimentation project while the Silk language and its standard library evolve.

## Layout

```
src/
  buffer/          # Pixel + FrameBuffer
  geom/            # Basic geometry
  lib/             # Shared helpers (writers, formatting, defaults…)
  main.silk
```

## Running

From the project root (the directory containing `silk.toml`):

```bash
silk test
# or
silk test --file src/buffer/frame_buffer.silk
```

Output files (e.g. PPM) are written relative to the current working directory.

## Goals (near-term)

- Solid, ownership-correct pixel and buffer primitives
- Clean test surface for visual output
- Simple path from buffer → file
- Keep everything explicit (no hidden allocation or ambient I/O)

## License

MIT
