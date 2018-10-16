FROM scratch
ADD kubesim_nr/ca-certificates.crt /etc/ssl/certs/
ADD kubesim_nr/goclient /goclient
EXPOSE 8080
CMD ["/goclient", "network", "Bluetooth"]
