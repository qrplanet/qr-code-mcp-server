# Prompt: Manage QR Code folders

Use this to create folders, move QR Codes into folders, and inspect folder-level performance.

## Create a folder

```
Create a QR Code folder called "Retail Displays".
```

## Move QR Codes

```
Move all QR Codes tagged "retail" into the folder "Retail Displays".
```

## Folder performance

```
Show scan statistics for the folder "Retail Displays" for the last 30 days.
```

## What happens

The agent calls `list_folders` to resolve folder names, `create_folder` if a folder does not exist, and `update_qr_code` with `folder_id` to move QR Codes. For reporting, it calls `get_folder_stats`; if asked to reset folder statistics, it calls `reset_folder_stats`.
