# Install [Harbor](https://goharbor.io/)
* Container Registry
* Required docker and docker compose


```
$wget https://github.com/goharbor/harbor/releases/download/v2.13.2/harbor-offline-installer-v2.13.2.tgz
$tar -zxvf harbor-offline-installer-v2.13.2.tgz
$cd harbor/
```

Generate SSL certificated
```
sudo apt-get install ssl-cert
sudo make-ssl-cert generate-default-snakeoil
sudo usermod --append --groups ssl-cert yyuu
ls -l /etc/ssl/certs/ssl-cert-snakeoil.pem /etc/ssl/private/ssl-cert-snakeoil.key
```

Edit SSL in file `harbor.yml`
```
# https related config
https:
  # https port for harbor, default is 443
  port: 443
  # The path of cert and key files for nginx
  certificate: /etc/ssl/certs/ssl-cert-snakeoil.pem
  private_key: /etc/ssl/private/ssl-cert-snakeoil.key
```

Install
```
sudo ./install.sh
```

Login to Harbor
* user=admin
* password=Harbor12345