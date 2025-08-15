# Systemd

`systemd` is the init system and service manager used by most modern Linux distributions.

## systemd Core Utilities

### systemd utility List

| Utility                               | Description                                                    |
| ------------------------------------- | -------------------------------------------------------------- |
| [`systemctl`](#systemctl)             | Manages services (start, stop, restart, enable, disable, etc.) |
| [`journalctl`](#journalctl)           | Views and filters logs collected by the systemd journal        |
| [`loginctl`](#loginctl)               | Manages user logins and sessions                               |
| [`hostnamectl`](#hostnamectl)         | Sets or queries the hostname and related machine metadata      |
| [`timedatectl`](#timedatectl)         | Sets or queries the system date, time, and NTP settings        |
| [`systemd-analyze`](#systemd-analyze) | Analyzes system boot-up performance                            |
| [`systemd-cgtop`](#systemd-cgtop)     | Monitors control group resource usage in real time             |
| [`resolvectl`](#resolvectl)           | Resolves domain names using the systemd-resolved service       |
| [`busctl`](#busctl)                   | Interacts with the D-Bus message bus system                    |


### systemctl

#### systemctl - System Commands

- Manage systemd units and control system services (start, stop, enable, etc.).

| Command               | Description                                                        |
| --------------------- | ------------------------------------------------------------------ |
| `systemctl halt`      | Stop all running software, leave the hardware powered on.          |
| `systemctl hibernate` | Save contents of system memory to disk and power off the hardware. |
| `systemctl poweroff`  | Halt and power off the system.                                     |
| `systemctl reboot`    | Reboot the system.                                                 |

#### systemctl - Service Commands

| Command                       | Description                                  |
| ----------------------------- | -------------------------------------------- |
| `systemctl start <service>`   | Start a service immediately                  |
| `systemctl stop <service>`    | Stop a running service                       |
| `systemctl restart <service>` | Restart a service                            |
| `systemctl reload <service>`  | Reload service configuration without restart |
| `systemctl enable <service>`  | Enable service to start at boot              |
| `systemctl disable <service>` | Disable boot-time start                      |
| `systemctl status <service>`  | Show current status and recent logs          |
| `systemctl mask <service>`    | Prevent service from being started           |
| `systemctl unmask <service>`  | Remove mask so it can start again            |
| `systemctl list-units`        | List active units                            |
| `systemctl list-unit-files`   | List all unit files and their enabled state  |

### journalctl

- Query and filter logs from the systemd journal.

| Command                    | Description                               |
| -------------------------- | ----------------------------------------- |
| `journalctl`               | Show entire journal                       |
| `journalctl -b`            | Show logs from current boot               |
| `journalctl --list-boots`  | List all boot sessions                    |
| `journalctl -b -1`         | Logs from previous boot                   |
| `journalctl -u <service>`  | Show logs for a specific unit/service     |
| `journalctl -n 100`        | Show the last 100 log entries             |
| `journalctl -f`            | Follow new log entries (tail -f style)    |
| `journalctl -p err..emerg` | Show only error (and above) priority logs |
| `journalctl --disk-usage`  | Show disk usage of journal                |
| `journalctl --since today` | Show logs since today                     |

### busctl

- Inspect and monitor D-Bus (Desktop Bus) for debugging or introspection.

| Command                        | Description                                        |
| ------------------------------ | -------------------------------------------------- |
| `busctl list`                  | List all services/peers on the bus                 |
| `busctl status [SERVICE\|PID]` | Show process info & credentials for service or PID |
| `busctl monitor [SERVICE...]`  | Dump live message traffic, Ctrl+C to stop          |
| `busctl capture [SERVICE...]`  | Capture bus traffic to a pcap file                 |
| `busctl tree [SERVICE...]`     | Show object tree exported by service(s)            |

### loginctl

- Manages user sessions and login-related settings.

| Command                           | Description                                    |
| --------------------------------- | ---------------------------------------------- |
| `loginctl list-sessions`          | List all active sessions                       |
| `loginctl list-users`             | List logged-in users                           |
| `loginctl user-status <UID>`      | Show all sessions & processes for user `<UID>` |
| `loginctl session-status <ID>`    | Show detailed info and logs for session `<ID>` |
| `loginctl show-session <ID>`      | Show machine-parsable properties of a session  |
| `loginctl terminate-session <ID>` | End all processes in session `<ID>`            |
| `loginctl lock-session <ID>`      | Lock the specified session                     |
| `loginctl unlock-session <ID>`    | Unlock the specified session                   |

### systemd-analyze

- Analyze system boot performance and unit dependencies.

| Command                           | Description                           |
| --------------------------------- | ------------------------------------- |
| `systemd-analyze`                 | Show total boot time breakdown        |
| `systemd-analyze blame`           | List services ordered by startup time |
| `systemd-analyze plot > boot.svg` | Generate SVG visual of boot sequence  |

### systemd-cgtop

- Real-time monitoring of resource usage by cgroups (CPU, memory, I/O).

| Command                    | Description                        |
| -------------------------- | ---------------------------------- |
| `systemd-cgtop`            | Monitor top cgroups resource usage |
| `systemd-cgtop -c`         | Sort cgroups by CPU usage          |
| `systemd-cgtop -d <delay>` | Change refresh delay interval      |

### timedatectl

- Manage system date, time, timezone, and NTP synchronization.

| Command                             | Description                     |
| ----------------------------------- | ------------------------------- |
| `timedatectl status`                | Show current date/time settings |
| `timedatectl list-timezones`        | List all available timezones    |
| `timedatectl set-timezone <Zone>`   | Set system timezone             |
| `timedatectl set-time "YYYY-MM-DD"` | Manually set date               |
| `timedatectl set-time "HH:MM:SS"`   | Manually set time               |
| `timedatectl set-ntp true`          | Enable NTP sync                 |
| `timedatectl set-ntp false`         | Disable NTP sync                |

### resolvectl

- Interact with systemd-resolved DNS resolver service.

| Command                                | Description                                     |
| -------------------------------------- | ----------------------------------------------- |
| `resolvectl status`                    | Show DNS configuration and link info            |
| `resolvectl query <hostname>`          | Resolve hostname via systemd-resolved           |
| `resolvectl dns <interface> <IP>`      | Set DNS server(s) for a specific interface      |
| `resolvectl domain <interface> <name>` | Set search domain(s) for an interface           |
| `resolvectl flush-caches`              | Clear the DNS cache managed by systemd-resolved |
| `resolvectl reset-statistics`          | Reset all DNS resolution statistics             |

### hostnamectl

- Query and set the system hostname (static, transient, pretty) and related metadata.

| Command                                       | Description                                      |
| --------------------------------------------- | ------------------------------------------------ |
| `hostnamectl status`                          | Show current hostname & system info              |
| `hostnamectl hostname <NAME>`                 | Set the static/transient/pretty hostname         |
| `hostnamectl set-hostname <NAME> --static`    | Set only the static hostname                     |
| `hostnamectl set-hostname <NAME> --transient` | Set only the transient hostname                  |
| `hostnamectl set-hostname <NAME> --pretty`    | Set the pretty (user-friendly) hostname          |
| `hostnamectl set-chassis <TYPE>`              | Set chassis type (e.g., desktop, laptop, server) |

```markdown
- Static - The permanent hostname stored in `/etc/hostname`. Used at boot time.
- Transient - Temporary hostname set at runtime (often by DHCP or manually). Lost on reboot.
- Pretty - A user-friendly, display name (can include spaces and special characters).
```
