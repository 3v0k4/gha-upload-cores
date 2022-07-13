# Upload core dumps from GitHub Actions

Sometimes your software core dumps in CI. That's great! Better in CI than in production. But then you need to debug that core dump.

In order to do so, you need to:

1. Upload the binary.
2. Make sure the core dump was stored.
3. Upload the core dump.

This repository demonstrates how to do this.
