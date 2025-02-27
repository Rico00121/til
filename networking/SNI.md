# Server Name Indication
Server Name Indication (SNI) is a TLS extension that allows a client to specify the hostname of the server it is connecting to, which allows **a server to present multiple certificates** on the **same IP address and TCP port number**.

## SNI handshake process 
### 1️⃣ Client sending TLS Client Hello

In Client Hello, the client specifies the target domain name in the Extended Field (SNI):

```yaml
Client Hello
├── TLS Version: TLS 1.2
├── Cipher Suites: ECDHE-RSA-AES256-GCM-SHA384
├── Extensions:
```

### 2️⃣ The server (Server) parses the SNI and returns the correct certificate
After the server receives Client Hello, check the SNI field.'
The server looks for the matching SSL certificate and returns to Server Hello:
```yaml
Server Hello
├── TLS Version: TLS 1.2
├── Selected Cipher Suite: ECDHE-RSA-AES256-GCM-SHA384
├── Certificate: example.com.pem
```

### 3️⃣ Both parties complete the TLS handshake and establish an HTTPS connection


## Specific implementation
### Client 
Client must support to access SNI-enabled websites.

Modern browsers (Chrome, Firefox, Edge, Safari) support SNI **by default**.

### Server
SNI must be configured to return the correct certificate for different domain names.

For example, in Nginx:

```nginx
server {
    listen 443 ssl;
    server_name example.com;
    ssl_certificate /etc/nginx/ssl/example.com.crt;
    ssl_certificate_key /etc/nginx/ssl/example.com.key;
}
server {
    listen 443 ssl;
    server_name example2.com;
    ssl_certificate /etc/nginx/ssl/example2.com.crt;
    ssl_certificate_key /etc/nginx/ssl/example2.com.key;
}
```