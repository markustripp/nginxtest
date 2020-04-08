FROM nginx:1.17

### nginx-after

RUN sed -i 's/user\s*nginx/user  root/' /etc/nginx/nginx.conf

RUN set -eux; \
	{ \
		echo 'server {'; \
		echo '    listen       80;'; \
		echo '    server_name  localhost;'; \
		echo '    location / {'; \
		echo '        root   /root/workspace/nginxtest;'; \
		echo '        index  index.html index.htm;'; \
		echo '    }'; \
		echo '    error_page   500 502 503 504  /50x.html;'; \
		echo '    location = /50x.html {'; \
		echo '        root   /root/workspace/nginxtest;'; \
		echo '    }'; \
		echo '}'; \
	} | tee /etc/nginx/conf.d/default.conf

ENTRYPOINT ["service", "nginx", "start"]
