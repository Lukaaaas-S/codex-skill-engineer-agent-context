# Public Release Checklist

- [ ] `SKILL.md` has the expected name and description frontmatter.
- [ ] `agents/openai.yaml` is present when the skill needs agent configuration.
- [ ] Shared references point inside `references/shared/`.
- [ ] No package-local references are broken.
- [ ] No secrets, credentials, private keys, or environment files are included.
- [ ] No internal source paths, local filesystem paths, personal names, or private repository URLs remain.
- [ ] No sensitive brand or industry exclusion wording remains.

## Copied Shared Files

- [ ] `references/shared/boundaries/agent.md`
- [ ] `references/shared/boundaries/cross-family.md`
- [ ] `references/shared/patterns/attention-recirculation.md`
- [ ] `references/shared/patterns/failure-mode-map.md`
- [ ] `references/shared/patterns/filesystem-as-context.md`
- [ ] `references/shared/patterns/stable-prefix-cache.md`
- [ ] `references/shared/sources/source-policy.md`
