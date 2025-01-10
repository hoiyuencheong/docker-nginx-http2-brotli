以下是更新后的 README 内容：

<p align="center">
    <img src="https://upload.wikimedia.org/wikipedia/commons/c/c5/Nginx_logo.svg" width="150" />
</p>

<p align="center">A web server that can also be used as a reverse proxy, load balancer, mail proxy and HTTP cache.</p>

<p align="center">
<img src="https://github.com/InsulateJustf/docker-nginx-http2-brotli/actions/workflows/push.yml/badge.svg" />
<img src="https://img.shields.io/github/v/release/InsulateJustf/docker-nginx-http2-brotli" />
</p>

<p align="center">
<a href="https://github.com/InsulateJustf/docker-nginx-http2-brotli/blob/main/README.md">中文 |</a>
<a href="https://github.com/InsulateJustf/docker-nginx-http2-brotli/blob/main/README.EN.md">English</a>
</p>

---

## What is this?

This project provides a stable and up-to-date Nginx image with the following features:

- **HTTP/2** and **Brotli compression**.
- **TLS 1.3** support with advanced OpenSSL configurations.
- Modules for additional functionality, including GeoIP2 and Brotli.
- Built with optimized libraries such as **zlib by Cloudflare** and **jemalloc** for better performance.

## What's inside?

The image includes:

- [zlib by Cloudflare](https://github.com/cloudflare/zlib)
- OpenSSL with **TLS 1.3**, **ChaCha20-Poly1305 Draft Version**, and **Equal Preference Cipher Grouping** support.
- [ngx_brotli](https://github.com/google/ngx_brotli) for Brotli compression.
- [ngx_http_geoip2_module](https://github.com/leev/ngx_http_geoip2_module) for GeoIP2 support.

### Modules and Details:

```text
nginx version: nginx/1.26.2
built by gcc 12.2.1 (Alpine 12.2.1_git20220424)
built with OpenSSL 3.0.0
TLS SNI support enabled
configure arguments:
        --prefix=/etc/nginx \
        --sbin-path=/usr/sbin/nginx \
        --modules-path=/usr/lib/nginx/modules \
        --conf-path=/etc/nginx/nginx.conf \
        --error-log-path=/var/log/nginx/error.log \
        --http-log-path=/var/log/nginx/access.log \
        --pid-path=/var/run/nginx.pid \
        --lock-path=/var/run/nginx.lock \
        --http-client-body-temp-path=/var/cache/nginx/client_temp \
        --http-proxy-temp-path=/var/cache/nginx/proxy_temp \
        --http-fastcgi-temp-path=/var/cache/nginx/fastcgi_temp \
        --http-uwsgi-temp-path=/var/cache/nginx/uwsgi_temp \
        --http-scgi-temp-path=/var/cache/nginx/scgi_temp \
        --user=nginx \
        --group=nginx \
        --with-http_ssl_module \
        --with-http_realip_module \
        --with-http_addition_module \
        --with-http_sub_module \
        --with-http_dav_module \
        --with-http_flv_module \
        --with-http_mp4_module \
        --with-http_gunzip_module \
        --with-http_gzip_static_module \
        --with-http_random_index_module \
        --with-http_secure_link_module \
        --with-http_stub_status_module \
        --with-http_auth_request_module \
        --with-http_xslt_module=dynamic \
        --with-http_image_filter_module=dynamic \
        --with-http_geoip_module=dynamic \
        --with-threads \
        --with-stream \
        --with-stream_ssl_module \
        --with-stream_ssl_preread_module \
        --with-stream_realip_module \
        --with-stream_geoip_module=dynamic \
        --with-http_slice_module \
        --with-mail \
        --with-mail_ssl_module \
        --with-compat \
        --with-file-aio \
        --with-http_v2_module \
        --with-zlib=/usr/src/zlib \
        --with-pcre=/usr/src/pcre2-${PCRE_VERSION} \
        --with-pcre-jit \
        --with-libatomic=/usr/src/libatomic_ops-${LIBATOMIC_VERSION} \
        --add-module=/usr/src/headers-more-nginx-module-${HEADERS_MORE_VERSION} \
        --add-module=/usr/src/ngx-fancyindex-${FANCYINDEX_VERSION} \
        --add-module=/usr/src/ngx_brotli \
        --add-module=/usr/src/ngx_http_geoip2_module \
        --add-module=/usr/src/nginx-http-flv-module \
        --add-module=/usr/src/ngx_http_substitutions_filter_module \
        --add-module=/usr/src/nginx_upstream_check_module \ 
        --with-openssl=/usr/src/libressl-${LIBRESSL_VERSION} \
        --with-openssl-opt='zlib enable-tls1_3 enable-weak-ssl-ciphers enable-ec_nistp_64_gcc_128 -ljemalloc -Wl,-flto'

How to Use?

Quick Start

Pull the image from Docker Hub:

docker pull justf/nginx-http2-brotli:latest

Alternatively, pull from GitHub Container Registry:

docker pull ghcr.io/InsulateJustf/nginx-http2-brotli:latest

Configuration
	•	.conf files in /etc/nginx/main.d are included in the main nginx context (useful for global settings like env).
	•	.conf files in /etc/nginx/conf.d are included in the http nginx context.

SSL Configuration

This image includes DH parameters for secure DHE ciphers. Add the following to your Nginx configuration:

ssl_dhparam /etc/ssl/dhparam.pem;

Credits

Special thanks to:
	•	@kn007/patch
	•	@akafeng/docker-nginx
	•	@macbre/docker-nginx-http3
