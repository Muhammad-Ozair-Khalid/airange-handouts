# BAZOOKA

The console boots. Its final cartridge does not.

A technician preserved three retail diagnostic captures before the arcade went
dark. Recover the missing launch record and open the cartridge's final
transmission. The service fixture can still run records, but its receipts do not
unlock the transmission.

## Run

Use Linux on an x86-64 CPU (a Linux VM, WSL2 Linux distribution, or Linux container
is fine). The executable is statically linked; Python and OpenSSL installations
are not required to run it. No root privileges or network access are needed.

```sh
sha256sum -c SHA256SUMS
chmod +x bazooka
./bazooka cartridge.bzk launch.run
```

`launch.run` is a binary record you must reconstruct. Its layout is part of the
challenge. A valid launch prints the flag; rejected input exits with a nonzero
status. The correct launch completes in under a second on the author's test
machine. There are no timing checks, intentional delays, or anti-debugging traps.

The diagnostic interface accepts structurally valid records and bypasses the
launch checks. It returns the resulting state and a semantic execution receipt:

```sh
./bazooka --probe cartridge.bzk launch.run
```

The three records in `service.capture` are examples for that interface, not
solutions. Their `record_hex` fields are hexadecimal encodings of the complete
binary record. `state_hex` uses little-endian words. You may alter local files,
debug, write emulators, or decrypt offline. Only the authentic transmission's flag
is accepted by the CTF platform. Keep the supplied cartridge for your final solve.

## Learn

[pwn.college — Reverse Engineering](https://pwn.college/program-security/reverse-engineering)

AI assistance is allowed. The task is to reconstruct and understand the machine;
there is no prohibition on generated analysis or tooling.

Flag format: `AIRANGE{...}`.
