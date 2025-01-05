When we config Nginx, we need to set the server_name. But we don't know what is the server_name.

```
server {
    listen 80;
    server_name www.myowndomain.com rico00121.github.io;

    location / {
        proxy_pass http://localhost:8080; 
        proxy_set_header Host $host;
    }
}
```

The server_name directive in Nginx is used to specify the hostname or domain name of the server. It is used to match the incoming request's hostname against the server_name directive to determine which **server block** to use for processing the request.

By setting server_name `www.myowndomain.com rico00121.github.io;`, this tells Nginx that requests for both domains are handled by this server block.

# What happens if server_name is not set?
If server_name is not set, Nginx will match the request to the first configured server block (that is, the default server block).

**or we can use `server_name _;`**:

If you don't want to default to the first server block, you can set `server_name _;` explicitly to specify that all unknown requests be handled by it.
