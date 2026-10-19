# Reproducible source installation

This branch starts from pymavlink upstream
`ArduPilot/pymavlink` at `bd0a1b29d5b8b54b7d66abfe9ac043c528ac490f`.

The `mavlink` submodule pins the XML message definitions to
`ArduPilot/mavlink` at `e03dad40efb3a4009ad6d78de5e55997139ac2f3`.
Pip and uv initialize Git submodules when installing a Git requirement;
`setup.py` already searches `mavlink/message_definitions` for these files.
This makes installation independent of an external checkout or `MDEF`.

The runtime change keeps paced MAVFTP downloads alive while accepted data,
EOF, or gap repair makes progress. Duplicate, stale, and foreign replies
cannot renew the idle timer, and the caller's overall deadline still applies.
The regression tests exercise a 500-packet burst that lasts longer than the
default 3.7-second idle timeout, plus traffic that makes no useful progress.

The fix is carried only in the Axiovel fork. A version string of `2.4.50`
alone does not identify this source revision; use the immutable commit in
the dependency requirement and installed `direct_url.json`.
