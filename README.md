# cron_job

The role cron_job helps to automate deployments of CRON jobs. Apart from this it can upload some custom scripts that can be used in cron jobs later

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [cron_jobs](#cron_jobs)
  - [cron_scripts](#cron_scripts)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.20`

## Default Variables

### cron_jobs

List of cron jobs to be applied to a target host.
The syntax of a single cron job is taken from [ansible.builtin.cron](https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/cron_module.html)

**_Required:_** `true`<br />
**_Type:_** List<br />

#### Example usage

```YAML
cron_jobs:
  - name: job_name_1
    user: ansible
    job: /bin/script.sh
    minute: '*/45'
  - name: job_name_2
    user: ansible
    job: /bin/script.sh
    hour: '1'
```

### cron_scripts

List of scripts to be uploaded to a target host. A script must be on ansible control node

**_Type:_** List<br />

#### Example usage

```YAML
cron_scripts:
  - src: /opt/some/script.sh
    dest: /usr/local/bin/script.sh
    owner: ansible
    group: ansible
    mode: '0700'
```

## Dependencies

None.

## License

MIT

## Author

freedform
