FROM monica:fpm

# Use a modified php.ini tp increase `post_max_size` and `upload_max_filesize`
# Required to import vcard in bulk. See https://stackoverflow.com/a/11719522/7939550 for motivation
COPY php.ini "$PHP_INI_DIR/php.ini"
