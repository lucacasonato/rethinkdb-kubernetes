FROM rethinkdb:2.4.0

RUN apt-get update && \
  apt-get install -yq curl iproute2 && \
  rm -rf /var/cache/apt/* && rm -rf /var/lib/apt/lists/* && \
  curl -L http://stedolan.github.io/jq/download/linux64/jq > /usr/bin/jq && \
  chmod u+x /usr/bin/jq

COPY ./run.sh /usr/bin/run.sh
RUN chmod u+x /usr/bin/run.sh

CMD "/usr/bin/run.sh"
