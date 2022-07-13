# Upload core dumps from GitHub Actions

Sometimes your software segfaults when running tests in CI. That's great! Better it fail in CI than in production. But then you need to debug that segfault, in which case a coredump would be very helpful.

But how do you get a coredump to your computer?

In order to get coredumps you can debug, you need to:

1. Upload the binary that generated that coredump.
2. Make sure the coredump was stored to disk on segfaults and the like.
3. Upload the coredump even though a CI step has failed.

To ensure core dumps are stored to disk you need to:

1. Override `/proc/sys/kernel/core_pattern` so core dumps are written to file instead passed to `apport` (the default on Ubuntu).
2. Run `ulimit -c unlimited` in the relevant step to ensure core dumps get written to disk.

This repository demonstrates how to do this; see [the Workflow definition](.github/workflows/build.yml) to see the necessary steps.
The coredumps will end up as downloadable artifacts in the results of each relevant GitHub Actions runs.

## This repository is sponsored by [Sciagraph](https://sciagraph.com), a performance observability service for Python batch jobs.
