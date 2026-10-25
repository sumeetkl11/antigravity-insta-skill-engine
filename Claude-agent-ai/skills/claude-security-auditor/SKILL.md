# Claude Security Auditor

> **Version**: 1.0.0  
> **Category**: Security & Compliance  
> **Priority**: Critical

---

## Purpose

Pre-deployment security audit to catch the 6 most common vulnerabilities in AI-generated code before production.

---

## Trigger Conditions

- **Mandatory**: Before ANY production deployment
- **Manual**: `/security-audit` command
- **Recommended**: After every major feature implementation

---

## The 6 Common Vulnerabilities (AI-Generated Apps)

Most vibe-coded apps get hacked via these attack vectors:

### 1. SQL Injection
```yaml
vulnerability: "Direct SQL query construction with user input"
example_bad: |
  query = f"SELECT * FROM users WHERE id = {user_id}"
example_good: |
  query = "SELECT * FROM users WHERE id = ?"
  cursor.execute(query, (user_id,))
check_command: "Audit for SQL injection vulnerabilities"
```

### 2. XSS (Cross-Site Scripting)
```yaml
vulnerability: "Unescaped user input rendered in HTML"
example_bad: |
  return f"<div>Welcome {username}</div>"
example_good: |
  return f"<div>Welcome {escape(username)}</div>"
check_command: "Check for XSS attack vectors"
```

### 3. Exposed API Keys & Secrets
```yaml
vulnerability: "Hardcoded credentials in code or committed .env"
example_bad: |
  API_KEY = "sk-1234567890abcdef"
  git add .env
example_good: |
  API_KEY = os.getenv("API_KEY")
  # .env in .gitignore
check_command: "Scan for exposed API keys and secrets"
```

### 4. Insecure Authentication
```yaml
vulnerability: "Weak password policies, no rate limiting, missing 2FA"
example_bad: |
  if password == stored_password:  # Plain text comparison
example_good: |
  if bcrypt.checkpw(password, stored_hash):
check_command: "Review authentication/authorization logic"
```

### 5. Missing Input Validation
```yaml
vulnerability: "Accepting any user input without sanitization"
example_bad: |
  file_path = request.params["path"]
  open(file_path)  # Path traversal attack
example_good: |
  file_path = sanitize_path(request.params["path"])
  if not is_safe_path(file_path):
    raise SecurityError
check_command: "Validate all user input sanitization"
```

### 6. Unprotected Endpoints
```yaml
vulnerability: "API routes accessible without authentication"
example_bad: |
  @app.route('/admin/delete-user')
  def delete():  # No auth check
example_good: |
  @app.route('/admin/delete-user')
  @require_admin
  def delete():
check_command: "Verify HTTPS enforcement and CORS policies"
```

---

## Execution Instructions

### Step 1: Run Security Checklist

```markdown
Pre-Deployment Security Audit:

□ SQL Injection
  - Scan all database queries
  - Verify parameterized queries (no f-strings in SQL)
  - Check ORM usage (SQLAlchemy, Prisma, etc.)

□ XSS Protection
  - Audit all user input rendering
  - Verify HTML escaping
  - Check Content-Security-Policy headers

□ Secret Management
  - Scan for hardcoded API keys
  - Verify .env in .gitignore
  - Check environment variable usage
  - Audit git history for committed secrets

□ Authentication Security
  - Verify password hashing (bcrypt, argon2)
  - Check rate limiting on login endpoints
  - Validate session management
  - Review token expiration policies

□ Input Validation
  - Audit all user input entry points
  - Verify sanitization functions
  - Check file upload validation
  - Test for path traversal vulnerabilities

□ Endpoint Protection
  - Verify authentication on protected routes
  - Check HTTPS enforcement
  - Validate CORS configuration
  - Review API rate limiting
```

### Step 2: Automated Scanning Prompts

Generate security audit prompts for Claude:

```markdown
Prompt 1: SQL Injection Scan
"Scan all database query code. List any queries that directly interpolate user input without parameterized queries or ORM protection. Flag as HIGH RISK."

Prompt 2: Secret Exposure Scan
"Search codebase for patterns: API_KEY=, SECRET=, TOKEN=, password=, sk-*
Check if any secrets are hardcoded. Verify .env file is in .gitignore.
List all findings with file paths and line numbers."

Prompt 3: Authentication Review
"Review all authentication logic. Check:
1. Are passwords hashed with bcrypt/argon2?
2. Is there rate limiting on login endpoints?
3. Do sessions expire properly?
4. Is 2FA implemented or planned?"

Prompt 4: Input Validation Audit
"Identify all user input entry points (forms, API params, file uploads).
For each: verify sanitization is applied before processing.
Flag any direct usage of unsanitized input."

Prompt 5: Endpoint Security
"List all API routes. For each:
- Is authentication required? (flag if missing)
- Is HTTPS enforced?
- Is CORS configured properly?
- Is rate limiting applied?"
```

### Step 3: Generate Security Report

```markdown
**Security Audit Report**
Generated: 2026-10-25T09:32:07.464Z

**CRITICAL Issues (Block Deployment):**
- [ ] SQL injection vulnerabilities: X found
- [ ] Exposed API keys: X found
- [ ] Unprotected admin endpoints: X found

**HIGH Issues (Fix Before Launch):**
- [ ] Missing input validation: X instances
- [ ] XSS vulnerabilities: X found
- [ ] Weak password policies: X issues

**MEDIUM Issues (Fix Soon):**
- [ ] Missing rate limiting: X endpoints
- [ ] Incomplete CORS config: X routes
- [ ] Session management: X improvements needed

**Status**: ❌ BLOCKED / ⚠️ FIX REQUIRED / ✅ APPROVED

**Next Steps:**
1. [Specific remediation steps]
2. Re-run audit after fixes
3. Schedule penetration testing
```

---

## Integration Points

- **Ponytail Pipeline**: Runs automatically before deployment phase
- **Manual Delegator**: Creates human tasks for external security tools
- **Verification Runner**: Blocks deployment if critical issues found

---

## Examples

### Example 1: Failed Audit

```
User: "Ready to deploy authentication system"

Claude (runs security auditor):
⚠️ **CRITICAL SECURITY ISSUES FOUND**

SQL Injection:
- Line 45: Direct query interpolation in login function
- File: auth.py → Use parameterized query

Exposed Secrets:
- Line 12: Hardcoded JWT_SECRET in config.py
- Action: Move to .env, add .env to .gitignore

Missing Rate Limiting:
- POST /api/login has no rate limit
- Risk: Brute force attack vulnerability

Status: ❌ DEPLOYMENT BLOCKED

Fix these 3 critical issues before proceeding.
```

### Example 2: Passed Audit

```
User: "Ready to deploy user management API"

Claude (runs security auditor):
✅ **Security Audit: PASSED**

Checks completed:
✓ SQL Injection: All queries use parameterized statements
✓ Secrets: All keys in .env, .gitignore configured
✓ Authentication: bcrypt hashing, 15-min rate limit
✓ Input Validation: Sanitization on all endpoints
✓ XSS Protection: HTML escaping applied
✓ Endpoint Security: Auth middleware on all routes, HTTPS enforced

Status: ✅ APPROVED FOR DEPLOYMENT

Recommendations:
- Consider adding 2FA for admin accounts
- Schedule penetration test within 30 days
```

---

## Success Metrics

- ✅ Zero critical vulnerabilities in production
- ✅ All 6 common attack vectors checked
- ✅ Security audit runs before every deployment
- ✅ Clear remediation steps provided

---

*Extracted from: Knowledge Vault - 05_dev_productivity.md (Reel #33)*  
*Based on: "6 ways vibe-coded apps get hacked" research*
