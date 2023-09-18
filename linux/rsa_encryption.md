## RSA 2048 PRIVATE KEY GENERATION

- openssl genrsa -des3 -out private.pem 2048

or

- openssl genpkey -algorithm RSA -out key.pem \
    -pkeyopt rsa_keygen_bits:2048 -pkeyopt rsa_keygen_pubexp:3

## PUBLIC KEY GENERATION

- openssl rsa -in private.pem -outform PEM -pubout -out public.pem


## SIGNATURE FOR FILE

-  openssl dgst -sha256 -sign madjovi_private_key.pem -out test.sig test\n

## VERIFY SIGNATURE 

- openssl dgst -sha256 -verify madjovi_public_key.pem -signature test.sig test\n
