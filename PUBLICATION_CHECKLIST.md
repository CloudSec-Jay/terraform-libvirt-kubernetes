# Publication checklist

The repository may be public while incomplete runtime checks remain clearly
documented. Do not describe an unchecked item as validated.

- [x] Select and add an explicit open-source license.
- [x] Scan the initial Git content for common credential and private-key patterns.
- [x] Confirm examples contain no personal hostnames, addresses, usernames, or device identifiers.
- [x] Run `terraform fmt -check -recursive` and `terraform validate`.
- [ ] Test plan and apply against a disposable libvirt environment.
- [ ] Verify destroy behavior and document data-loss boundaries.
- [x] Add CI for formatting and validation.
- [x] Review generated inventory and state exclusions.
