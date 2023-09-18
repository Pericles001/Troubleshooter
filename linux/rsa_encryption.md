## RSA 2048 PRIVATE KEY GENERATION

## PUBLIC KEY GENERATION

## SIGNATURE FOR FILE

-  openssl dgst -sha256 -sign madjovi_private_key.pem -out test.sig test\n

## VERIFY SIGNATURE 

- openssl dgst -sha256 -verify madjovi_public_key.pem -signature test.sig test\n
