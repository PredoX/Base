FROM nginx:1.19.2-alpine
RUN echo 'http://dl-4.alpinelinux.org/alpine/edge/community/' >> /etc/apk/repositories
ENV TIMEZONE=America/Santiago
RUN apk add tzdata && cp /usr/share/zoneinfo/America/Santiago /etc/localtime
CMD ["nginx", "-g", "daemon off;"]
EXPOSE 80 443