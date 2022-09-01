FROM consul:1.10

RUN apk -U add bind-tools

RUN mkdir /var/lib/consul

CMD consul agent --bind=$(hostname -i) --config-dir=/etc/consul.d --encrypt="HsCFOX2ToXK1cjTiXaCQ9tvrIfIiSrPNgOv9D8o0ND4="