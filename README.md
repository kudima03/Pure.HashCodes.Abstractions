# Pure.HashCodes.Abstractions

Base interface for the **Pure** hash code ecosystem — a minimal, byte-enumerable contract for deterministic hash sequences.

[![.NET build & test](https://github.com/kudima03/Pure.HashCodes.Abstractions/actions/workflows/build-and-test.yml/badge.svg?branch=main)](https://github.com/kudima03/Pure.HashCodes.Abstractions/actions/workflows/build-and-test.yml)
[![Build and Deploy](https://github.com/kudima03/Pure.HashCodes.Abstractions/actions/workflows/publish-nuget.yml/badge.svg?branch=main)](https://github.com/kudima03/Pure.HashCodes.Abstractions/actions/workflows/publish-nuget.yml)
[![NuGet](https://img.shields.io/nuget/v/Pure.HashCodes.Abstractions)](https://www.nuget.org/packages/Pure.HashCodes.Abstractions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Overview

`Pure.HashCodes.Abstractions` defines a single interface — `IDeterminedHash` — that every deterministic hash type in the Pure ecosystem implements. The interface extends `IEnumerable<byte>`, exposing the underlying hash as an ordered byte sequence. This allows hash values from different domain types to be combined, compared, and composed without coupling to any concrete hash algorithm.

## Interface

```csharp
namespace Pure.HashCodes.Abstractions;

public interface IDeterminedHash : IEnumerable<byte>;
```

`IDeterminedHash` carries no methods beyond `IEnumerable<byte>`. Concrete implementations (in [`Pure.HashCodes`](https://github.com/kudima03/Pure.HashCodes) and domain-specific packages) are responsible for producing stable byte sequences. Calling `GetHashCode()` or `ToString()` on any `IDeterminedHash` implementation throws `NotSupportedException` by design — byte enumeration is the only supported equality mechanism.

## Design Principles

- **Single responsibility** — one interface, one concept: a deterministic byte sequence.
- **Composable** — byte sequences from multiple `IDeterminedHash` values concatenate cleanly to form compound hashes.
- **AOT-compatible** — no reflection, no generics constraints beyond `IEnumerable<byte>`.
