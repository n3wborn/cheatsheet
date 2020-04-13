# CERTIFICATS

#### Source

[howtoforge.com](https://www.howtoforge.com/tips-and-tricks-to-secure-your-nginx-web-server/)


### Key Generation

`openssl genrsa -aes256 -out nginx.key 1024`

### CSR Generation

`openssl req -new -key nginx.key -out nginx.csr<Paste>`

### Certificate Siging

`openssl x509 -req -days 365 -in nginx.csr -signkey nginx.key -out nginx.crt`


