# Bitbucket Pipelines PHP 7.3 image

[![](https://images.microbadger.com/badges/version/pyguerder/bitbucket-pipelines-php73.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php73 "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/pyguerder/bitbucket-pipelines-php73.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php73 "Get your own image badge on microbadger.com")

## Based on Ubuntu 18.04

### Packages installed

- `php7.3-zip`, `php7.3-xml`, `php7.3-mbstring`, `php7.3-curl`, `php7.3-json`, `php7.3-imap`, `php7.3-mysql`, `php7.3-tokenizer`, `php7.3-xdebug`, `php7.3-intl`, `php7.3-soap`, `php7.3-pdo`, `php7.3-cli`, `php7.3-gd`, `php7.3-gmp` and `php7.3-apcu`
- wget, curl, unzip
- Composer
- Mysql 5.7
- Node + Yarn

### Sample `bitbucket-pipelines.yml`

```YAML
image: pyguerder/bitbucket-pipelines-php73
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost -u root -proot -e "CREATE DATABASE test;"
          - composer install --no-interaction --no-progress --prefer-dist
          - ./vendor/phpunit/phpunit/phpunit -v --coverage-text --colors=never --stderr
```
