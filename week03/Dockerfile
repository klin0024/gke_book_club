FROM alpine:3.14
ARG whoami=Allen
WORKDIR /var/www/localhost/htdocs
COPY ./ ./
RUN apk --update add apache2; \
    rm -rf /var/cache/apk/*; \
    cat ./index_new.html > index.html; \
    sed -i "s/Page Not Fully Loaded/Excellent! Page Fully Loaded/g" index.html; \
    sed -i "s/Solve It Now/Solved/g" index.html; \
    sed -i "s/Achieved by Unknown/Achieved by ${whoami}/g" index.html; 
ENTRYPOINT ["httpd","-D","FOREGROUND"]