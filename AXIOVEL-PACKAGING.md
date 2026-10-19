# Reproducible source installation

This branch packages unmodified pymavlink runtime sources from
`ArduPilot/pymavlink` at `bd0a1b29d5b8b54b7d66abfe9ac043c528ac490f`.

The `mavlink` submodule pins the XML message definitions to
`ArduPilot/mavlink` at `e03dad40efb3a4009ad6d78de5e55997139ac2f3`.
Pip and uv initialize Git submodules when installing a Git requirement;
`setup.py` already searches `mavlink/message_definitions` for these files.
This makes installation independent of an external checkout or `MDEF`.

The submodule and this note are the only additions to upstream. The paced
MAVFTP download idle-timeout patch is not included. A version string of
`2.4.50` alone does not identify this source revision; use the immutable
commit in the dependency requirement and installed `direct_url.json`.
