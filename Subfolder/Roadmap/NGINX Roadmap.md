## Nginx Roadmap

### 🔰 1. **Basics & Foundations**

- What is Nginx?
    - Event-driven architecture
    - Reverse proxy vs web server
    - Difference from Apache
- Installing Nginx (Linux, Windows, Docker)
- Nginx directory structure (`/etc/nginx/`)
- Main config file (`nginx.conf`)
- Nginx process model (`master` & `worker` processes)

---

### ⚙️ 2. **Core Configuration**

- `nginx.conf` structure
    - **Main context** (`events`, `http`)
    - **Server blocks**
    - **Location blocks**
- Directives syntax (`directive value;`)
- Reloading vs restarting Nginx (`nginx -s reload`)
- Testing configuration (`nginx -t`)

---

### 🌐 3. **Serving Static Content**

- Default root (`/usr/share/nginx/html`)
- `root` vs `alias` directive
- Setting `index.html`
- Custom error pages (`error_page`)

---

### 🛣️ 4. **Routing & Locations**

- Location matching:
    - Prefix match (`location /path`)
    - Exact match (`location = /path`)
    - Regex match (`location ~ \.php$`)
- Priority order of locations
- `rewrite` vs `return`

---

### 🔄 5. **Reverse Proxy Basics**

- `proxy_pass`
- Proxy headers (`proxy_set_header`)
- Handling redirects (`proxy_redirect`)
- Load balancing basics:
    - Round-robin
    - IP hash
    - Least connections

---

### 🛡️ 6. **Security & Access Control**

- Denying or allowing IPs (`allow`, `deny`)
- Rate limiting (`limit_req_zone`, `limit_req`)
- Basic HTTP Authentication (`auth_basic`)
- Hiding Nginx version (`server_tokens off`)

---

### 📜 7. **Logging**

- Access logs (`access_log`)
- Error logs (`error_log`)
- Log formats (`log_format`)
- Debugging requests

---

### 🔧 8. **Performance Tuning**

- Worker processes & connections (`worker_processes`, `worker_connections`)
- Keep-alive connections (`keepalive_timeout`)
- Gzip compression (`gzip`, `gzip_types`)
- Client body size limits (`client_max_body_size`)

---

### 🔐 9. **HTTPS / SSL/TLS**

- Serving HTTPS (`listen 443 ssl;`)
- Configuring certificates (`ssl_certificate`, `ssl_certificate_key`)
- Redirecting HTTP → HTTPS
- Basic SSL optimizations (`ssl_protocols`, `ssl_ciphers`)

---

### 🗂️ 10. **Serving Dynamic Content (via Upstreams)**

- Upstream backend servers (`upstream backend { server 127.0.0.1:8000; }`)
- Proxying to app servers (e.g., Python, PHP, Node.js)
- FastCGI for PHP (`fastcgi_pass`, `fastcgi_param`)

---

### 🏗️ 11. **Load Balancing (Built-in)**

- Simple load balancing with multiple upstream servers
- Health checks (passive only, active requires external module)
- Sticky sessions (limited built-in support)

---

### 📂 12. **Caching**

- Proxy cache (`proxy_cache`, `proxy_cache_path`)
- Cache keys & expiration (`proxy_cache_key`, `proxy_cache_valid`)
- Microcaching for performance

---

### 🌀 13. **Redirects & Rewrites**

- Simple redirects (`return 301`)
- Regex rewrites (`rewrite ^/old /new permanent;`)
- Canonical URL redirection

---

### 🛠️ 14. **Monitoring & Maintenance**

- Basic status module (`stub_status`)
- Checking open connections
- Log rotation (`logrotate`)

---

### 🧪 15. **Advanced Topics**

- Named vs anonymous locations
- Internal requests (`internal` directive)
- Conditional logic (`if` directive pitfalls)
- Combining multiple sites with server blocks
- Serving files efficiently (`sendfile`, `tcp_nopush`, `tcp_nodelay`)

---

### 🧰 16. **Deployment & Best Practices**

- Zero-downtime reloads (`nginx -s reload`)
- Separating configuration into `/etc/nginx/sites-available/` & `sites-enabled/`
- Testing configurations before deployment
- Hardening Nginx for production

---

### ✅ Optional Built-in Extras

- HTTP/2 (`listen 443 ssl http2;`)
- Brotli (if compiled with support)
- Using built-in modules only (`ngx_http_*`)

---

## ✅ What You’ll Be Able to Do with Just Built-in Nginx:

- Serve static websites
- Reverse proxy to app servers
- Secure sites with SSL
- Basic load balancing
- Basic caching & rate limiting
- Handle routing & rewrites
- Optimize performance for production