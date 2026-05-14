---
name: best-practices
description: Apply modern web development best practices for security, compatibility, and code quality. Use when asked to "apply best practices", "security audit", "modernize code", "code quality review", or "check for vulnerabilities".
license: MIT
metadata:
  author: web-quality-skills
  version: "1.0"
---

# Best practices

Modern web development standards based on Lighthouse best practices audits. Covers security, browser compatibility, and code quality patterns.

## Security

### HTTPS everywhere

**Enforce HTTPS:**
```html
<!-- ❌ Mixed content -->
<img src="http://example.com/image.jpg">

<!-- ✅ HTTPS only -->
<img src="https://example.com/image.jpg">
```

**HSTS Header:**
```
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
```

### Content Security Policy (CSP)

```html
<!-- Basic CSP via meta tag -->
<meta http-equiv="Content-Security-Policy"
      content="default-src 'self';
               script-src 'self' https://trusted-cdn.com;
               style-src 'self' 'unsafe-inline';
               img-src 'self' data: https:;
               connect-src 'self' https://api.example.com;">
```

**CSP Header (recommended):**
```
Content-Security-Policy:
  default-src 'self';
  script-src 'self' 'nonce-abc123' https://trusted.com;
  style-src 'self' 'nonce-abc123';
  img-src 'self' data: https:;
  connect-src 'self' https://api.example.com;
  frame-ancestors 'self';
  base-uri 'self';
  form-action 'self';
```

**Using nonces for inline scripts:**
```html
<script nonce="abc123">
  // This inline script is allowed
</script>
```

### Trusted Types (modern DOM-XSS defense)

```
Content-Security-Policy: require-trusted-types-for 'script'; trusted-types default;
```

```javascript
const escape = trustedTypes.createPolicy('default', {
  createHTML: (s) => DOMPurify.sanitize(s, { RETURN_TRUSTED_TYPE: true })
});

// ❌ This now throws TypeError under enforcement
element.innerHTML = userInput;

// ✅ Goes through the policy
element.innerHTML = escape.createHTML(userInput);
```

### Subresource Integrity (SRI) for third-party scripts

Pin every `<script>` and `<link rel="stylesheet">` you load from a CDN you don't control.

```html
<script src="https://cdn.example.com/lib@1.2.3/dist/lib.js"
        integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho1wx4JwY8wC"
        crossorigin="anonymous"></script>
```

### Security headers

```
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
```

Note: Do NOT use X-XSS-Protection. It was deprecated/removed and introduced vulnerabilities.

### No vulnerable libraries

```bash
# Check for vulnerabilities
npm audit

# Auto-fix when possible
npm audit fix
```

### Input sanitization

```javascript
// ❌ XSS vulnerable
element.innerHTML = userInput;
document.write(userInput);

// ✅ Safe text content
element.textContent = userInput;

// ✅ If HTML needed, sanitize
import DOMPurify from 'dompurify';
element.innerHTML = DOMPurify.sanitize(userInput);
```

### Secure cookies

```javascript
// ❌ Insecure cookie
document.cookie = "session=abc123";

// ✅ Secure cookie (server-side)
Set-Cookie: session=abc123; Secure; HttpOnly; SameSite=Strict; Path=/
```

---

## Browser compatibility

### Doctype declaration

```html
<!-- ✅ HTML5 doctype -->
<!DOCTYPE html>
<html lang="en">
```

### Character encoding

```html
<!-- ✅ Charset as first element in head -->
<html>
<head>
  <meta charset="UTF-8">
  <title>Page</title>
</head>
```

### Viewport meta tag

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### Feature detection

```javascript
// ❌ Browser detection (brittle)
if (navigator.userAgent.includes('Chrome')) { }

// ✅ Feature detection
if ('IntersectionObserver' in window) {
  // Use IntersectionObserver
} else {
  // Fallback
}

// ✅ Using @supports in CSS
@supports (display: grid) {
  .container { display: grid; }
}
```

---

## Deprecated APIs

### Avoid these

```javascript
// ❌ document.write (blocks parsing)
document.write('<script src="..."></script>');

// ✅ Dynamic script loading
const script = document.createElement('script');
script.src = '...';
document.head.appendChild(script);

// ❌ Synchronous XHR (blocks main thread)
const xhr = new XMLHttpRequest();
xhr.open('GET', url, false); // false = synchronous

// ✅ Async fetch
const response = await fetch(url);
```

### Event listener passive

```javascript
// ✅ Passive listeners (allows smooth scrolling)
element.addEventListener('touchstart', handler, { passive: true });
element.addEventListener('wheel', handler, { passive: true });
```

---

## Console & errors

### No console errors

```javascript
// ✅ Proper error handling
try {
  riskyOperation();
} catch (error) {
  errorTracker.captureException(error);
  showErrorMessage('Something went wrong. Please try again.');
}
```

### Global error handler

```javascript
window.addEventListener('error', (event) => {
  errorTracker.captureException(event.error);
});

window.addEventListener('unhandledrejection', (event) => {
  errorTracker.captureException(event.reason);
});
```

---

## Source maps

### Production configuration

```javascript
// ✅ Hidden source maps (uploaded to error tracker)
module.exports = {
  devtool: 'hidden-source-map',
};

// ✅ Or no source maps in production
module.exports = {
  devtool: process.env.NODE_ENV === 'production' ? false : 'source-map',
};
```

Strip `sourcesContent` from production maps when uploading to your error tracker. For Vite, prefer `sourcemap: 'hidden'`.

---

## Performance best practices

### Avoid blocking patterns

```html
<!-- ❌ Blocking script -->
<script src="heavy-library.js"></script>

<!-- ✅ Deferred script -->
<script defer src="heavy-library.js"></script>

<!-- ❌ Blocking CSS import -->
@import url('other-styles.css');

<!-- ✅ Link tags (parallel loading) -->
<link rel="stylesheet" href="styles.css">
```

### Memory management

```javascript
// ❌ Memory leak (never removed)
window.addEventListener('resize', handler);

// ✅ Cleanup when done
window.addEventListener('resize', handler);
// Later:
window.removeEventListener('resize', handler);

// ✅ Using AbortController
const controller = new AbortController();
window.addEventListener('resize', handler, { signal: controller.signal });
// Cleanup:
controller.abort();
```

---

## Code quality

### Semantic HTML

```html
<!-- ❌ Non-semantic -->
<div class="header"><div class="nav"><div class="nav-item">Home</div></div></div>

<!-- ✅ Semantic HTML5 -->
<header><nav><a href="/">Home</a></nav></header>
<main><article><h1>Headline</h1></article></main>
```

---

## Audit checklist

### Security (critical)
- [ ] HTTPS enabled, no mixed content
- [ ] No vulnerable dependencies (`npm audit`)
- [ ] CSP headers configured
- [ ] `require-trusted-types-for 'script'` enforced (or report-only)
- [ ] Third-party scripts pinned with SRI hashes
- [ ] Security headers present (HSTS, X-Content-Type-Options, Referrer-Policy)
- [ ] No exposed source maps

### Compatibility
- [ ] Valid HTML5 doctype
- [ ] Charset declared first in head
- [ ] Viewport meta tag present
- [ ] No deprecated APIs used
- [ ] Passive event listeners for scroll/touch

### Code quality
- [ ] No console errors
- [ ] Valid HTML (no duplicate IDs)
- [ ] Semantic HTML elements used
- [ ] Proper error handling
- [ ] Memory cleanup in components

### UX
- [ ] No intrusive interstitials
- [ ] Permission requests in context
- [ ] Clear error messages
- [ ] Appropriate image aspect ratios

---

## Tools

| Tool | Purpose |
|------|---------|
| `npm audit` | Dependency vulnerabilities |
| [SecurityHeaders.com](https://securityheaders.com) | Header analysis |
| [W3C Validator](https://validator.w3.org) | HTML validation |
| Lighthouse | Best practices audit |
| [Observatory](https://observatory.mozilla.org) | Security scan |

## References

- [MDN Web Security](https://developer.mozilla.org/en-US/docs/Web/Security)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
