# Simple caching nginx image
# docker run --rm -ti -e UPSTREAM=1.1.1.1 -p 80:80 nginx-cache

FROM nginx:alpine
COPY nginx.conf /tmp/nginx.conf
ENTRYPOINT ["/bin/sh", "-c", "cat /tmp/nginx.conf | envsubst '$UPSTREAM' | tee /etc/nginx/nginx.conf; nginx -g 'daemon off;'"]
