# The cause of the matter
I deployed my blog using github's own domain name site: https://rico00121.github.io/blog/ , this is a free Github Pages site.

Now I rented a server myself and want to apply for a new domain name. But I still want to keep the original github URL working. That means I want to map to two urls both to my own new server.

# The solution
The solution is to find a way to set up redirects on GitHub Pages.
## Method 1: use HTML redirect
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="refresh" content="0; url=https://www.yourdomain.com/">
        <title>Redirecting...</title>
    </head>
    <body>
        <p>If you are not redirected automatically, follow this <a href="https://www.yourdomain.com/">link</a>.</p>
    </body>
</html>
```

## Method 2: use Javascript redirect
```html
<script>
    window.location.href = "https://www.yourdomain.com/";
</script>
```