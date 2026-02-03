# Security Files Reference

**Created:** 2026-02-01 after ZeroLeaks vulnerability report

## Quick Reference - Where Everything Is

### Security Documentation
| File | Location | Purpose |
|------|----------|---------|
| Hardening Log | `/root/clawd/SECURITY_HARDENING.md` | Complete hardening history |
| Security Guide | `/root/clawd/SECURITY.md` | Secret management guide |
| Audit Script | `/root/clawd/security-audit.sh` | Automated security checks |
| Env Template | `/root/clawd/.env.template` | Safe .env template |

### Secret Storage
| Secret | Storage Location |
|--------|-----------------|
| Home Assistant Token | Clawdbot credential store + `.env` |
| Tavily API Key | Clawdbot config (skills.entries.tavily) |
| Browser-Use API Key | Clawdbot config (skills.entries.browser-use) |
| GitHub Token | `~/.config/gh/hosts.yml` |
| LLM API Keys | Clawdbot auth profiles |
| SSH Keys | `~/.ssh/` (600 permissions) |

### Key Commands
```bash
# Run security audit
./security-audit.sh

# Check file permissions
ls -la ~/.ssh/ /root/clawd/.env /root/clawd/MEMORY.md

# View security docs
cat SECURITY_HARDENING.md
cat SECURITY.md

# Verify git security
git ls-files | grep -E "\.env$|\.key$|\.token$"  # should be empty
```

### Token Rotation Checklist
- [ ] Home Assistant (Settings → Profile → Long-Lived Access Tokens)
- [ ] Tavily (tavily.com)
- [ ] Browser-Use (cloud.browser-use.com)
- [ ] GitHub (Settings → Developer Settings)

### Security Audit Schedule
- **Weekly:** Run `./security-audit.sh`
- **Quarterly:** Rotate all API tokens
- **Annually:** Rotate SSH keys

### Model Security (per ZeroLeaks)
- ❌ **Kimi K2.5**: 100% extraction rate - avoid for sensitive ops
- ❌ **Gemini 3 Pro**: 5/100 score - high vulnerability  
- ✅ **Claude Opus**: Recommended for security-critical operations
