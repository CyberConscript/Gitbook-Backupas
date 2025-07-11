# Registry

## Windows Registry

The Windows Registry is a hierarchical database that stores all kinds of settings and configuration information for your Windows operating system, as well as for installed applications and user preferences. Think of it as the control centre for your computer's settings.

The Windows Registry is stored in various Hive files, mainly in the `%SystemRoot%\System32\config` directory. The main Hive files are:

| Hive File             | Mapped Key Path          | Purpose                                                                                                        |
| --------------------- | ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| **SAM**               | `HKLM\Local_Machine\SAM` | The Security Account Manager stores user account and security policy data.                                     |
| **SECURITY**          | `HKLM\SECURITY`          | Holds security-related configuration data, including user authentication and permissions.                      |
| **SYSTEM**            | `HKLM\SYSTEM`            | Stores system-related configuration data, including hardware, device drivers, and startup settings.            |
| **SOFTWARE**          | `HKLM\SOFTWARE`          | Contains configuration information for installed software and system-wide settings.                            |
| **DEFAULT**           | `HKU\.DEFAULT`           | Acts as a template for creating new user profiles, providing default settings for user-specific configuration. |
| **NTUSER.DAT**        | `HKCU`                   | Contains user-specific settings for each user profile, including user preferences and specific configurations. |
| **USRCLASS.DAT**      | `HKCU\Software\Class`    | Stores user-specific configuration.                                                                            |
| HKEY\_CURRENT\_CONFIG |                          |                                                                                                                |
| HKEY\_USERS           |                          |                                                                                                                |
| HKEY\_LOCAL\_MACHINE  |                          |                                                                                                                |
| HKEY\_CLASSES\_ROOT   |                          |                                                                                                                |
| HKEY\_CLASSES\_ROOT   |                          |                                                                                                                |
