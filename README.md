# Next.js stack for Wodby

Deploy Next.js on Kubernetes with Wodby. This repository contains the stack
manifests used by the public Next.js stack in the Wodby catalog.

- [Next.js stack in the Wodby catalog](https://wodby.com/stacks/nextjs)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## What's included

| Component / service | Default configuration |
| --- | --- |
| Node.js (`nextjs`)<br>`nextjs` | required; enabled by default; links: `db` → `postgres`, `redis` → `valkey`, `sendmail` → `mailpit` |
| PostgreSQL (`postgres`)<br>`postgres` | optional; disabled by default; volumes: `data` 10 GB |
| Valkey<br>`valkey` | optional; disabled by default |
| Mailpit<br>`mailpit` | optional; disabled by default |
| OpenSMTPD<br>`opensmtpd` | optional; disabled by default |
| Gotenberg<br>`gotenberg` | optional; disabled by default |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Use this stack

The simplest path is to add the public stack from the Wodby catalog. Review the
enabled services, versions, storage sizes, links, and other defaults when
creating your app.

To maintain your own version of this stack:

1. Fork this repository.
2. Edit the stack manifest.
3. Import the repository as a
   [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

Wodby imports the manifest from the selected Git branch or tag and creates a new
stack revision when the Git-backed stack is updated.

## Customize the stack

Common changes include selecting different service versions, enabling or
disabling optional components, changing persistent volume sizes, adjusting
stack-level environment and workload overrides, or replacing one linked service
with another compatible service.

When replacing or renaming a stack service, update every corresponding
`services[].links` target and derivative reference. Stack-local names and
referenced service names are distinct identifiers and do not need to match.

Validate customized manifests with the Wodby CLI before importing them:

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

See the [stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)
for every supported field and the [managed services
index](https://github.com/wodby/services) for available service references.
