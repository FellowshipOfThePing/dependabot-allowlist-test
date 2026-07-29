# dependabot-allowlist-test

Throwaway repo. Tests whether a `dependabot.yml` with an `allow` list plus
`target-branch` pointed at the default branch narrows Dependabot **security**
updates down to the allow list, or leaves them covering the whole manifest.

Deliberately vulnerable dependencies, none of which appear in the allow list
under test:

- `lodash@4.17.15` — direct dependency
- `express@4.16.0` — pulls vulnerable transitive dependencies

Default branch is `master` on purpose: the question is whether `target-branch`
naming *the default branch* still counts as "set" for the purposes of excluding
the entry from security-update configuration.

Method: confirm a security PR appears with no `dependabot.yml` (control), then
add the config and confirm whether one still appears.

Context: MercuryTechnologies/mercury-web#54712, FDX-1391.
