# silky_smooth

[![Status](https://img.shields.io/badge/status-alpha-8b5cf6)](https://silklang.org)

Alpha graphics library for rendering to PPM format. Uses Silk for memory safety and explicit effects.

## Install

```sh
silk init silky_smooth
cd silky_smooth
silk run
```

## Quick start

```silk
import buffer.frame_buffer { writeP7 }
import silk.io.logger { LogError }
import silk.mem.allocator { Allocator }
import silk.system.filesystem_native { OsFileSystem }

pub effect fn main() -> ()
  ! LogError {
  let mut allocator = Allocator.systemAllocatorProvider()
  let mut files = run OsFileSystem.make("/") |> Effect.provideMut(&mut allocator)

  let mut pixels = run List<Pixel>.makeWithCapacity(3840 * 2160)
    |> Effect.provideMut(&mut allocator)
  run pixels.appendRepeated(Pixel.fromU32(0xdc143cff), 3840 * 2160)
    |> Effect.provideMut(&mut allocator)

  run writeP7(3840, 2160, pixels.asSlice())
    |> Effect.provideMut(&mut files)
    |> Effect.provideMut(&mut allocator)
}
```

## Features

- Render to PPM format with alpha channel support
- Memory-safe pixel manipulation with explicit effects
- Allocator-driven memory management
- Error handling through typed failures (`FileError`, `OutOfMemoryError`, etc.)
- Testable with Silk's testing framework

## Build

```sh
silk build --release
```

## Test

```sh
silk test
```

## License

[MIT](LICENSE) © 2026 MichTheMaker

## Status

Alpha - API may change rapidly before 1.0
