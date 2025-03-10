timelapse
=========
[![Ansible Lint](https://github.com/oxivanisher/role-timelapse/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/oxivanisher/role-timelapse/actions/workflows/ansible-lint.yml)

Install and configure:
* Take pictures with rpicam-still (libcamera-still on Raspberry OS < 12>)
* Upload mechanism for [TimelapseLiveView](https://github.com/oxivanisher/TimelapseLiveView) aka "Chickencam".
* Upload (archive) the pictures to a rsync server

Notes
-----

It is strongly advised to also use the `oxivanisher.raspberry_pi.tmp_ramfs` as in the example below to prolong the live span of the SD cards in your Raspberry Pis!

Role Variables
--------------

| Name          | Comment                              | Default value |
|---------------|--------------------------------------|---------------|
| timelapse_greyworld_awb | Use the greyworld awb | `0`          |
| timelapse_libcamera_verbose | Make rpicam-still be verbose  | `0`          |
| timelapse_libcamera_awb | The used awb for rpicam-still | `auto`          |
| timelapse_libcamera_exposure | The used exposure for rpicam-still | `normal`          |
| timelapse_libcamera_brightness | The used brightness for rpicam-still | `0`          |
| timelapse_upload_key | The key for the upload to TimelapseLiveView |       |
| timelapse_upload_server | The key for the upload to TimelapseLiveView |           |
| timelapse_upload_protocol | The protocol for the upload to TimelapseLiveView. Available is `https` and `http` | `https`          |
| timelapse_upload_server_ip | The ipv4 server ip for the upload to TimelapseLiveView |           |
| timelapse_upload_server_ip6 | The ipv6 server ip for the upload to TimelapseLiveView |           |
| timelapse_upload_every | The systemd timer seting when to trigger uploads | `*:0/30` |
| timelapse_upload_ransomization | The systemd time randomization in seconds | `120` |
| timelapse_rsync_server | Rsync server |           |
| timelapse_rsync_user | Rsync user |           |
| timelapse_rsync_password | Rsync password |           |
| timelapse_rsync_path | Rsync path |           |
| timelapse_rsync_speed_limit  | Rsync upload speed limit    | `10000`          |

Example Playbook
----------------

```yaml
- name: Timelapse done with raspi camera
  hosts: timelapse
  roles:
    - role: oxivanisher.raspberry_pi.tmp_ramfs
    - role: oxivanisher.raspberry_pi.timelapse
```

License
-------

BSD

Author Information
------------------

This role is part of the [oxivanisher.raspberry_pi](https://galaxy.ansible.com/ui/repo/published/oxivanisher/raspberry_pi/) collection, and the source for that is located on [github](https://github.com/oxivanisher/collection-raspberry_pi).
