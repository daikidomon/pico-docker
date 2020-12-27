FROM nginx:1.19.6

ADD conf /etc/nginx/conf.d

ARG TZ
RUN echo ${TZ} > /etc/timezone \
   && dpkg-reconfigure -f noninteractive tzdata

RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stdout /var/log/nginx/error.log