# Attendance System for Dolibarr

A Dolibarr module for importing clock events from ZKTeco attendance devices and converting paired attendance events into time spent on project tasks. It links device users to Dolibarr users and keeps imported events available for review.

This repository is a fork of [delcroip/dolibarr_attendance_system](https://github.com/delcroip/dolibarr_attendance_system).

## Features

- Register attendance devices and test their network connection.
- Import device users and attendance events through the bundled ZKLibrary.
- Link attendance-system users to Dolibarr users.
- Review events and process them into task time records.
- Configure event duration limits, overnight boundaries, and device-event retention.

## Requirements and compatibility

- A compatible ZKTeco device reachable from the Dolibarr server.
- Active Dolibarr projects and tasks, with the relevant users assigned.
- Administrator access for module installation and setup.

The legacy descriptor declares Dolibarr **9+** and PHP **5.0+**. Those declarations do not establish compatibility with current releases. Validate the module against your intended Dolibarr/PHP version and device before using it with staff records. Multi-company support is listed as unfinished in the original project.

## Installation

1. Back up the Dolibarr database and documents.
2. Copy the supplied `htdocs/attendanceSystem` directory into your Dolibarr `htdocs` directory. Retain the exact `attendanceSystem` spelling and case.
3. Sign in as an administrator and enable **AttendanceSystem** under **Setup → Modules/Applications**.
4. Open the module's setup page, `attendanceSystem/admin/setup.php`, and review processing settings and user permissions.

The repository's `htdocs` directory is a packaging wrapper; do not copy the entire repository as the module directory.

## Configure and use

1. Create a device record with its network address, port, and target task.
2. Test connectivity, import device users, and link them to the appropriate Dolibarr users.
3. Review event-processing limits and confirm that assigned project tasks are correct.
4. Import attendance events, inspect the records, then process them into task time.

**Review device-event retention before the first import.** The setting `ATTENDANCE_CLEAR_EVENT` defaults to enabled and instructs the importer to clear device attendance after reading it. Preserve device records until you have verified your import and recovery process.

Processing pairs events into working intervals and creates native task time. Check incomplete or unexpected event pairs before treating the result as final.

## Source layout

- [`htdocs/attendanceSystem/`](htdocs/attendanceSystem): installable module.
- [`class/AttendanceSystem.class.php`](htdocs/attendanceSystem/class/AttendanceSystem.class.php): device access and import.
- [`class/AttendanceSystemEvent.class.php`](htdocs/attendanceSystem/class/AttendanceSystemEvent.class.php): event processing and task time creation.
- [`admin/setup.php`](htdocs/attendanceSystem/admin/setup.php): processing configuration.

## License

The repository includes the [GNU Affero General Public License v3](LICENSE). Individual source files also retain their original contributor and GPL notices; preserve those notices when redistributing changes.
