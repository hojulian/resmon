# Resource Monitor

## Features

Display CPU frequency, usage, memory consumption, and battery percentage remaining within the VSCode status bar.

## Screenshots

![Disk space feature](images/disk_space_screenshot.png).

## Requirements

Just the system information node module.

## Compile and Install locally

Install the `vsce` tool:

```
npm install -g @vscode/vsce
```

Package the extension locally:

```
vsce package
```

Install it on VSCode:

`Command + Shift + p` to open command panel, select `Extensions: Install from VSIX...`. Pick the compiled package (`resourcemonitor-xxx.vsix`) from this directory.

## Extension Settings

- `resmon.show.cpuusage`: Show CPU Usage. In Windows, this percentage is calculated with processor time, which doesn't quite match the task manager figure.
- `resmon.show.cpufreq`: Show CPU Frequency. This may just display a static frequency on Windows.
- `resmon.show.mem`: Show consumed and total memory as a fraction.
- `resmon.show.battery`: Show battery percentage remaining.
- `resmon.show.disk`: Show disk space information.
- `resmon.show.cputemp`: Show CPU temperature. May not work without the lm-sensors module on Linux. May require running VS Code as admin on Windows.
- `resmon.disk.format`: Configures how the disk space is displayed (percentage remaining/used, absolute remaining, used out of totel).
- `resmon.disk.drives`: Drives to show. For example, 'C:' on Windows, and '/dev/sda1' on Linux.
- `resmon.updatefrequencyms`: How frequently to query systeminformation. The minimum is 200 ms as to prevent accidentally updating so fast as to freeze up your machine.
- `resmon.freq.unit`: Unit used for the CPU frequency (GHz-Hz).
- `resmon.mem.unit`: Unit used for the RAM consumption (GB-B).
- `resmon.alignLeft`: Toggles the alignment of the status bar.
- `resmon.color`: Color of the status bar text in hex code (for example, #FFFFFF is white). The color must be in the format #RRGGBB, using hex digits.

## Known Issues

A better solution for Windows CPU Usage would be great. I investigated alternatives to counting Processor Time, but none of them seemed to match the Task Manager percentage.

---

## Change Log

## [1.0.8]
- Update `systeminformation` to v5.22.11 to support Apple Silicon M1/M2/M3.
- Update Node versions, JS dependency versions, and GH actions.

### [1.0.7]
- Changed underlying CPU frequency API, added hiding battery/CPU temp information if the device lacks a battery/doesn't support CPU temp sensing, added some clarifications about CPU frequency behavior on Windows.

### [1.0.6]

- Added DiskSpace, CPU Temperature. Adjusted battery icon.

### [1.0.5]

- Refactored code heavily, addressed Github issue with memory.used versus memory.active.

### [1.0.4]

- Added icon for store.

### [1.0.3]

- Changed icons. Added choosable units.

### [1.0.2]

- Actually properly added systeminformation as a real dependency.

### [1.0.1]

- Properly added systeminformation as a real dependency

### [1.0.0]

- Initial release
