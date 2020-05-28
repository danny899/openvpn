# How to automate SSL installation using Certbot
This tutorial uses certbot for automating SSL installation on apache web server

## Install Certbot on Fedora
Run the following command to install cerbot on fedora
```yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm```
```yum install certbot python2-certbot-apache```

Check your certbot installation
```certbot --version```

## Install SSL certificate for single domain
Run the following command to install SSL certifcate for a single domain, you can nominate your webroot folder using the `--webroot` parameter. Replace $EMAIL and $DOMAIN_NAME with your own values.
```sudo certbot certonly --no-self-upgrade --no-bootstrap  --email $EMAIL --agree-tos --webroot -w "/var/www/" -d "$DOMAIN_NAME"```


## Install SSL certificate for wildcard domain
This section is only valid for certbot version 0.22+.

Run the following command for manual SSL certificate installation
```sudo certbot certonly --manual --no-self-upgrade --no-bootstrap  --email $EMAIL --agree-tos  -d "domain.com" -d "*.domain.com" --manual-public-ip-logging-ok --preferred-challenges dns-01 --server https://acme-v02.api.letsencrypt.org/directory```