# Snakeoil Certificates

The snakeoil certificates are used by default in the `ssl-cert` package on Debian and Ubuntu. They are used for testing
or private purposes.

## Generate new certificate
```bash
# install dependencies
sudo apt-get install ssl-cert
# add pi user to ssl-cert group
sudo adduser pi ssl-cert
# generate new certificates
make-ssl-cert generate-default-snakeoil --force-overwrite
```

This will generate the following files:
```bash
# certificate
/etc/ssl/certs/ssl-cert-snakeoil.pem
# private key
/etc/ssl/private/ssl-cert-snakeoil.key
```

## Use snakeoil certificate with Moonraker
To use the snakeoil certificate with Moonraker, you have to create symbol links to the certificate and the private key:
```bash
ln -s /etc/ssl/certs/ssl-cert-snakeoil.pem /home/pi/printer_data/certs/moonraker.cert
ln -s /etc/ssl/private/ssl-cert-snakeoil.key /home/pi/printer_data/certs/moonraker.key
```
after that, you have to restart Moonraker.

## Use snakeoil certificate with Mainsail/Nginx
Open your nginx config with `sudo nano /etc/nginx/sites-available/mainsail` and add the following lines:
```nginx
listen 443 ssl default_server;
ssl_certificate /etc/ssl/certs/ssl-cert-snakeoil.pem;
ssl_certificate_key /etc/ssl/private/ssl-cert-snakeoil.key;
```
To restart nginx, use `sudo systemctl restart nginx`.

Now you can open Mainsail with `https://<your-ip>`. You only have to "allow" the certificate in your browser because it
is self-signed and not signed by a trusted CA.