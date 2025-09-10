## Apache

### 🔰 1. **Basics & Foundations**

- What is Apache HTTP Server?
    - Process-based architecture (MPM)
    - Difference vs Nginx
- Installing Apache (`httpd`) on Linux/Windows
- Apache directory structure:
    - `/etc/httpd/` or `/etc/apache2/`
    - `httpd.conf` main config
    - `conf.d/` and `sites-available/`
- Basic commands:
    - `apachectl start|stop|restart|graceful|configtest`

---

### ⚙️ 2. **Core Configuration**

- Structure of `httpd.conf`
- Directives syntax (`Directive value`)
- ServerRoot, Listen, User/Group
- Including other configs (`Include`, `IncludeOptional`)
- Testing config (`apachectl configtest`)

---

### 🌐 3. **Serving Static Content**

- DocumentRoot
- DirectoryIndex (`index.html`)
- Directory listings (`Options +Indexes`)
- Alias vs Redirect

---

### 🛣️ 4. **Virtual Hosts**

- Name-based virtual hosting
- IP-based virtual hosting
- Setting `ServerName` & `ServerAlias`
- Separate logs for each vhost

---

### 📜 5. **URL Routing & Rewriting**

- Simple redirects (`Redirect 301 /old /new`)
- Mod_rewrite basics:
    - RewriteRule syntax
    - RewriteCond conditions
- Canonical URL handling

---

### 🔄 6. **Dynamic Content (CGI, Proxy, FastCGI)**

- Running CGI scripts (`mod_cgi`)
- Reverse proxy basics (`mod_proxy`):
    - `ProxyPass`, `ProxyPassReverse`
- Connecting to app servers (PHP, Python, Node.js)

---

### 🛡️ 7. **Security & Access Control**

- Denying or allowing IPs (`Require ip`)
- Basic Authentication (`mod_auth_basic`)
    - `htpasswd` for password files
- Access control with `<Directory>` and `<Location>`
- Hiding Apache version (`ServerTokens Prod`, `ServerSignature Off`)

---

### 📂 8. **Directory & File Handling**

- `<Directory>` and `<Files>` directives
- `.htaccess` files (allow/deny overrides)
- MIME types (`AddType`)

---

### 🏗️ 9. **Modules & MPM**

- Loading modules (`LoadModule`)
- Multi-Processing Modules (MPM):
    - `prefork`
    - `worker`
    - `event`
- Choosing the right MPM for performance

---

### 📜 10. **Logging**

- Access log (`CustomLog`)
- Error log (`ErrorLog`)
- Log formats (`LogFormat`)
- Separate logs per vhost

---

### 🔧 11. **Performance Tuning**

- KeepAlive settings (`KeepAlive`, `KeepAliveTimeout`)
- MaxClients/Threads (`MaxRequestWorkers`)
- `Timeout` directive
- Output compression with `mod_deflate`
- Caching headers with `mod_expires`

---

### 🔐 12. **HTTPS / SSL/TLS**

- `mod_ssl` basics
- Creating and configuring certificates (`SSLCertificateFile`, `SSLCertificateKeyFile`)
- Redirect HTTP → HTTPS
- SSL optimizations (`SSLProtocol`, `SSLCipherSuite`)

---

### 🗂️ 13. **Caching & Compression**

- `mod_cache` for basic caching
- `mod_expires` for client-side caching
- `mod_deflate` for Gzip compression

---

### 🧪 14. **.htaccess & Overrides**

- When to allow `.htaccess`
- Performance impact of `.htaccess`
- Common `.htaccess` use cases (redirects, rewrites, auth)

---

### 🛠️ 15. **Monitoring & Status**

- `mod_status` for server info & live stats
- `ExtendedStatus On`
- Checking requests per second, uptime, workers

---

### 🧰 16. **Maintenance & Deployment**

- Graceful restarts (`apachectl graceful`)
- Reloading without downtime
- Separating configs into `sites-enabled/`
- Hardening Apache for production

---

### 🌀 17. **Advanced Topics**

- `<IfModule>` for conditional loading
- `<If>` directives (Apache 2.4+)
- Using `SetEnv` and environment variables
- Handling large file uploads (`LimitRequestBody`)
- ETags & caching headers

---

### ✅ Optional Built-in Extras

- HTTP/2 (`mod_http2` if compiled)
- Reverse proxy load balancing (`mod_proxy_balancer`)
- Basic WebDAV (`mod_dav`)

---

## ✅ What You Can Do with Just Built-in Apache:

- Serve static websites
- Host multiple sites with virtual hosts
- Reverse proxy to backend servers
- Secure with SSL/TLS
- Redirect & rewrite URLs
- Basic load balancing (with built-in proxy modules)
- Optimize & cache for performance