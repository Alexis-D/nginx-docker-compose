FROM busybox
ARG HTML
RUN mkdir /static && echo "$HTML" > /static/index.html
WORKDIR /static
CMD ["/bin/httpd", "-fv"]
