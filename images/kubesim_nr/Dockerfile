FROM scratch
ADD kubesim_nr/ca-certificates.crt /etc/ssl/certs/
ADD kubesim_nr/goserv /goserv
EXPOSE 8080
CMD ["/goserv"]
