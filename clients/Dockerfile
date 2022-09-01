FROM consul:1.10

RUN apk -U add bind-tools

RUN mkdir /var/lib/consul

CMD consul agent --node=$(hostname) --bind=$(hostname -i) --data-dir=/var/lib/consul --encrypt="HsCFOX2ToXK1cjTiXaCQ9tvrIfIiSrPNgOv9D8o0ND4=" --config-dir=/etc/consul.d --retry-join=consulserver01