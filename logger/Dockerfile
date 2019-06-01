FROM fluent/fluentd:onbuild

RUN apk add --update --virtual .build_deps --no-cache sudo build-base ruby-dev && \
    gem install fluent-plugin-aws-elasticsearch-service fluent-plugin-slack && \
    gem sources --clear-all && apk del .build_deps && rm -rf /home/fluent/.gem/ruby/2.4.0/cache/*.gem