# Deploying a static (angular) site

So I finish build my amazing angular app and now I need to deploy it,
but after `ng build` I only have a static site, how do I serve it over `https`.

Apparently, `pm2` also has an option to serve a static site.

```bash
$ pm2 serve <path> <port> --spa
``` 

Or if I am using a json file to run all my apps, I can add to `myApps.json`:

```json
{
  "apps": [
    {
        "name": "My amazing app",
        "cwd": "./path/to/dist/folder",
        "script": "serve",
        "env": {
          "PM2_SERVE_PATH": "./",
          "PM2_SERVE_PORT": 6770,
          "PM2_SERVE_SPA": "true",
          "PM2_SERVE_HOMEPAGE": "/index.html"
        }
    }
  ]
}
```
And then I just need to run
```bash
$ pm2 start myApps.json
```
