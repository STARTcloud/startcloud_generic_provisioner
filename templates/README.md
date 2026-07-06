# Hosts Configuration Templates

This repository (`startcloud_generic_provisioner`) is a generic STARTcloud provisioner — a base box with no application stack baked in. You add the `startcloud.startcloud_roles` you need (e.g. `haproxy`, `keepalived`) under `roles:` in your `Hosts.yml`.

This directory contains the configuration templates: `example-Hosts.yml`, `debug-Hosts.yml`, and `Hosts.template.yml`.

## Directions

Access the template directory:

```bash
cd startcloud_generic_provisioner/templates
```

Copy your template of choice:

```bash
cp example-Hosts.yml ../Hosts.yml
```

Then go up a directory:

```bash
cd ../
```

Then edit your `Hosts.yml` (it is not tracked by git):

```bash
nano Hosts.yml
```

## Templates Overview

### example-Hosts.yml

- **Purpose**: A clean generic example — base foundation roles (setup, networking, disks, hostname, dependencies, service_user, sdkman, ssl) plus `vagrant_readme` and `lockdown`, with a commented spot to add the roles your box needs.
- **Usage**: Copy to `../Hosts.yml`, replace the `REPLACEME` values, and add roles.

### debug-Hosts.yml

- **Purpose**: A non-templated version a developer uses across various builds. Designed to work on both Bhyve and VirtualBox. A good reference for how to structure your own.
- **Usage**: Used directly without any templating.

### Hosts.template.yml

- **Purpose**: A pongo2 (Django-flavored Jinja2) template rendered by the hyperweaver-agent generator to produce the final `Hosts.yml`. Context comes from the machine spec: structured `settings`/`networks`/`roles` plus property values by exact field name; enabled spec roles are injected between the base foundation roles and `vagrant_readme`/`lockdown`.
- **Usage**: Rendered by the agent at machine start. Dialect note: pongo2, not full Jinja2 — filter args use colons (`|default:"x"`), no `is defined`, no parenthesized filter args.

### Add your own

If you add your own template, update this README.md with a brief description of what it does, and in your pull request mention why it differs from the existing ones.
