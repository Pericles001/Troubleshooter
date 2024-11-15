# RSA Key Generation and Signature Verification Guide

This guide provides instructions on generating RSA keys, creating public keys, signing files, and verifying signatures using OpenSSL.

---

## 1. RSA 2048 Private Key Generation

To generate a private key with RSA 2048-bit encryption, you can use the following OpenSSL commands.

### Option 1: Generate an Encrypted RSA Private Key

This command generates an RSA private key with a 2048-bit length, secured with a passphrase.

\`\`\`bash
openssl genrsa -des3 -out private.pem 2048
\`\`\`

### Option 2: Generate an RSA Private Key with Custom Options

This command uses the \`genpkey\` command with customizable parameters, such as key length (2048 bits) and a public exponent of 3.

\`\`\`bash
openssl genpkey -algorithm RSA -out key.pem \
    -pkeyopt rsa_keygen_bits:2048 -pkeyopt rsa_keygen_pubexp:3
\`\`\`

### Option 3: Generate a Private Key with Custom Output Filename

To save the private key with a specific filename, like \`madjovi_private.pem\`, you can use the following command:

\`\`\`bash
openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2048 -pkeyopt rsa_keygen_pubexp:3 -out madjovi_private.pem
\`\`\`

---

## 2. Public Key Generation

After generating a private key, you can extract the public key with the following command. The public key is generated in PEM format and stored in \`public.pem\`.

\`\`\`bash
openssl rsa -in private.pem -outform PEM -pubout -out public.pem
\`\`\`

---

## 3. Creating a Signature for a File

To sign a file, use your private key and the SHA-256 hashing algorithm. This command will generate a signature (\`test.sig\`) for a file named \`test\`.

\`\`\`bash
openssl dgst -sha256 -sign madjovi_private.pem -out test.sig test
\`\`\`

- **\`dgst -sha256\`**: Specifies the hashing algorithm (SHA-256).
- **\`-sign madjovi_private.pem\`**: Signs the file with the private key.
- **\`-out test.sig\`**: Outputs the signature to \`test.sig\`.
- **\`test\`**: The file to be signed.

---

## 4. Verifying a Signature

To verify the authenticity of a signed file, use the public key and the signature file.

\`\`\`bash
openssl dgst -sha256 -verify madjovi_public.pem -signature test.sig test
\`\`\`

- **\`dgst -sha256\`**: Specifies the SHA-256 hash function.
- **\`-verify madjovi_public.pem\`**: Verifies the signature with the public key.
- **\`-signature test.sig\`**: Specifies the signature file to be verified.
- **\`test\`**: The original file that was signed.

---

## Notes

- **Passphrase Protection**: It's recommended to use a passphrase when generating private keys to add an extra layer of security.
- **File Naming**: Customize filenames (e.g., \`madjovi_private.pem\`) to keep track of your key files.
- **Hash Algorithm**: SHA-256 is commonly used for strong security. Substitute another algorithm if specific requirements dictate.
