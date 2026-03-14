---
created: 2026-03-14
modified: March 14th 2026, 12:26:29 am
---
| Error                                                                                                                      | Fix                                                      |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| Colcon building inside dockerfile and encounter:<br>`'builtin_interfaces__rosidl_generator_c' which couldn't be found<br>` | Remove the colcon build and do it later in the container |
| Building dockerfile and encounter:<br>`no space left on device`                                                            | Free up space with `jlumbroso/free-disk-space@main`      |
|                                                                                                                            |                                                          |
