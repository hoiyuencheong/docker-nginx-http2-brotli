<p align="center">
    <img src="https://upload.wikimedia.org/wikipedia/commons/c/c5/Nginx_logo.svg" width="150" />
</p>

<p align="center">A web server that can also be used as a reverse proxy, load balancer, mail proxy, and HTTP cache.</p>

<p align="center">
<img src="https://github.com/InsulateJustf/docker-nginx-http2-brotli/actions/workflows/push.yml/badge.svg" />
<img src="https://img.shields.io/github/v/release/InsulateJustf/docker-nginx-http2-brotli" />
</p>

<p align="center">
<a href="https://github.com/InsulateJustf/docker-nginx-http2-brotli/blob/main/README.md">中文 |</a>
<a href="https://github.com/InsulateJustf/docker-nginx-http2-brotli/blob/main/README.EN.md">English</a>
</p>

---

## 这是个啥玩意儿？

这是一个稳定且最新的 Nginx 镜像，具备以下特性：

- **HTTP/2** 支持和 **Brotli 压缩**。
- **TLS 1.3** 支持，配备高级 OpenSSL 配置。
- 提供额外功能的多个模块，如 GeoIP2 和 Brotli。
- 使用优化的库（如 **Cloudflare 的 zlib** 和 **jemalloc**）以提升性能。

## 里面有些啥？

### 核心特性

- [Cloudflare 优化的 zlib](https://github.com/cloudflare/zlib)
- 支持 **TLS 1.3**、**ChaCha20-Poly1305 草案版本** 和 **BoringSSL 等价加密套件** 的 OpenSSL。
- [ngx_brotli](https://github.com/google/ngx_brotli) 用于 Brotli 压缩。
- [ngx_http_geoip2_module](https://github.com/leev/ngx_http_geoip2_module) 用于 GeoIP2 支持。

### Nginx 模块与构建详情

```plaintext
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

咋用？

快速开始

使用以下命令从 Docker Hub 拉取镜像：

docker pull justf/nginx-http2-brotli:latest

或者从 GitHub 容器注册表拉取镜像：

docker pull ghcr.io/InsulateJustf/nginx-http2-brotli:latest

配置说明

Nginx 配置
	•	挂载在 /etc/nginx/main.d 目录下的 .conf 文件会包含在 main 配置上下文中（如可在此使用 env 指令）。
	•	挂载在 /etc/nginx/conf.d 目录下的 .conf 文件会包含在 http 块中。

include /etc/nginx/main.d/*.conf;
...
http {
    ...;
    include /etc/nginx/conf.d/*.conf;
}

SSL 配置

镜像中已包含 Mozilla 提供的 DH 参数文件，存储在 /etc/ssl/dhparam.pem 中。
在你的 Nginx 配置中添加以下行：

ssl_dhparam /etc/ssl/dhparam.pem;

感谢

以下开源项目为本镜像提供了重要支持，特此感谢：
	•	@kn007/patch
	•	@akafeng/docker-nginx
	•	@macbre/docker-nginx-http3
