# WissKI Base stack

Compose template for a WissKI instance configured for the SCS Manager deployment
environment (WissKI Base image).

## Nextcloud private files (`private://nextcloud`)

The Drupal service bind-mounts the **project Team Folder** (not the owner's
whole Drive) into the container as `private://nextcloud`:

| Host (`NEXTCLOUD_USER_MOUNT_SOURCE`) | Container |
| --- | --- |
| `/var/lib/scs/nextcloud-mounts/<owner>/<project-label>` (set by SCS Manager) | `/opt/drupal/private-files/nextcloud` |

- Propagation is `rslave`: mounts created or renewed by the host sidecar after
  the container starts appear inside the container; the container cannot
  propagate mounts back to the host.
- Default source is `/var/lib/scs/nextcloud-mounts/_disabled` (empty directory)
  so instances without Nextcloud still start.
- No `cap_add`, `/dev/fuse`, or FUSE privileges are required in this stack; the
  sidecar owns the mount.

### Environment variables

| Variable | SCS default | Purpose |
| --- | --- | --- |
| `NEXTCLOUD_USER_MOUNT_SOURCE` | `/var/lib/scs/nextcloud-mounts/_disabled` | Host path bound into the container |
| `NEXTCLOUD_MOUNT_MODE` | `external` | `external` = consume sidecar mount; `sync` = legacy WebDAV sync; `none` = off |

`NEXTCLOUD_BASE_URL`, `NEXTCLOUD_LOGIN_NAME`, and `NEXTCLOUD_APP_PASSWORD` remain
for `NEXTCLOUD_MOUNT_MODE=sync` only. They are not needed for `external`.

### Operations note

If the container reports `Transport endpoint is not connected` under
`/opt/drupal/private-files/nextcloud`, the sidecar FUSE mount is broken.
Recovery is handled centrally by the Nextcloud mount reconciler; the WissKI
instance itself must not remount or repair it.
