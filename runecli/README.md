Rune Command-Line Tools
=======================

Library of various command-line tools to interact with the Rune platform.

These tools are supported for Linux or OSX Terminal. A subset of the tools may
also be compatible with Windows PowerShell. Python 3 must already be installed
on the system.

To get started, clone this repository on your local machine:
```bash
git clone https://github.com/rune-labs/opensource.git
```
You may also use your favorite Git desktop client to do this.


## patient-data-sessions

### System Requirements

* Python 3.6 or above
* Python packages `gql` and `requests` (available from PIP or Conda)

### Description

Download device data sessions for a patient. Data sessions are raw,
unprocessed datasets that a patient device (implant, wearable, phone app) has
recorded, before any processing has occurred on the platform.

This tool requires a valid Client Key to authenticate with the Rune API.

For complete description of usage, call
```
./patient-data-sessions --help
```

### Examples

Download all device session data from last 30 days to local folder
`~/my-data/patient-abc123`.

```bash
cd /path/to/opensource/runecli
./patient-data-sessions  \
    --patient-id=abc123  \
    --client-key-id=def456   \
    --client-key-secret=ghi789  \
    --start-time=-30d  \
    --end-time=now  \
    ~/my-data/patient-abc123
```

Download only sessions recorded by device `jkl012`, and for a specific
date/time range.

```bash
cd /path/to/opensource/runecli
./patient-data-sessions  \
    --patient-id=abc123  \
    --device-id=jkl012  \
    --client-key-id=def456   \
    --client-key-secret=ghi789  \
    --start-time=2020-06-01  \
    --end-time=2020-08-25T10:14:37  \
    ~/my-data/patient-abc123
```
