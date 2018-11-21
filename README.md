

# Setup

Tested OS: `Debian GNU/Linux 9.6 (stretch)` / `amd64`

Install following requirements:

```bash
sudo apt-get install -y ruby-dev bundler git nodejs
```

Now checkout this project (as unprivileged Linux user):
```bash
git clone https://github.com/hpaluch-pil/awestruct-bootstrap-example.git
cd awestruct-bootstrap-example/
```

For the 1st time install bundler packages:
```bash
bundler install
```

# Running awestruct in development mode

To use development mode with embedded server issue this command:
```bash
bundler exec awestruct -d -b 0.0.0.0 -u http://YOUR_VM_IP:4242/
```

> NOTE: Replace `YOUR_VM_IP` with your Debian IP address
> (for example in VirtualBox it is typically `192.168.56.101`
> for host-only network)

And point your browser to `http://YOUR_VM_IP:4242/` - you should
see welcome page styled in bootstrap.

# Running awestruct in generator mode

To generate static pages (to be server by `apache2` or `nginx` webserver)
use this command:
```bash
bundler exec awestruct -g -u YOUR_SITE_URL
```

Where `YOUR_SITE_URL` is full url of your site including trailing slash `/`,
for example: `http://192.168.56.101/`

To server these static pages you can for example:
* install nginx using command:
  
  ```bash
  sudo apt-get install nginx
  ```
* change `root` directive in `/etc/nginx/sites-available/default` to:
  ```
  root /home/MY_USER/awestruct-boostrap-example/_site/;
  ```
  
  > NOTE: replace `MY_USER` with your unprivileged username.

* verify nginx configuration using:
  ```bash
  sudo /usr/sbin/nginx -t
  ```

* restart nginx using:
  ```bash
  sudo systemctl restart nginx
  ```
* point browser to your nginx url...



# Resources

* Official Awestruct site: http://awestruct.org/
* How to fix missing bootstrap styles: https://github.com/awestruct/awestruct/issues/530#issuecomment-280930190


