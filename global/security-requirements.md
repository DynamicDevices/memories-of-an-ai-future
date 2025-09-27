# Security Requirements - CRITICAL

> **Scope**: Universal security practices for all AI memory storage  
> **Criticality**: CRITICAL - Security violation prevention

## CRITICAL SECURITY RULE

**🚨 NEVER STORE SECRETS IN AI MEMORIES 🚨**

This public AI memories repository must NEVER contain:
- Private keys (SSH keys, signing keys, API keys)
- Passwords (database passwords, service passwords, user passwords)
- Tokens (authentication tokens, API tokens, access tokens)
- Certificates (private certificates, SSL private keys)
- Connection strings (database URLs with credentials)
- Personal information (emails, phone numbers, addresses)
- Proprietary code (confidential algorithms, trade secrets)

## What CAN Be Stored

**✅ Safe to store:**
- File paths and directory structures (without credentials)
- Configuration patterns and templates (without actual values)
- Architecture descriptions and system designs
- Best practices and development workflows
- Hardware specifications and pin assignments
- Build commands and procedures (without secrets)
- Error patterns and troubleshooting guides
- Code organization and structure guidelines

## Examples

**❌ NEVER store:**
```
# BAD - Contains actual secrets
DATABASE_URL=postgresql://user:password123@localhost/db
SSH_KEY="-----BEGIN PRIVATE KEY-----..."
API_TOKEN="sk-1234567890abcdef..."
```

**✅ Safe to store:**
```
# GOOD - Shows pattern without secrets
DATABASE_URL=postgresql://username:password@host:port/database
SSH_KEY="Path: ~/.ssh/id_rsa (never store actual key content)"
API_TOKEN="Use environment variable API_TOKEN"
```

## Security Validation

Before adding any memory:
1. **Scan for patterns**: Look for key=value pairs that might contain secrets
2. **Check for credentials**: Ensure no usernames/passwords are included
3. **Verify paths**: File paths should not reveal sensitive directory structures
4. **Review examples**: Code examples must use placeholder values only
5. **Consider context**: Could this information be used maliciously?

## Incident Response

If secrets are accidentally committed:
1. **Immediate action**: Remove the secret from the repository
2. **Rotate credentials**: Change any exposed passwords/keys immediately
3. **Git history**: Use `git filter-branch` to remove from history
4. **Force push**: Update remote repository to remove traces
5. **Audit access**: Check who had access to the exposed information

## Repository Security

- **Public repository**: Assume all content is publicly visible
- **Version control**: All commits are permanent and traceable
- **Access control**: Repository may be cloned by anyone
- **Search engines**: Content may be indexed by search engines
- **AI training**: Content may be used to train AI models

This security requirement is NON-NEGOTIABLE and applies to all contributors and AI assistants.
