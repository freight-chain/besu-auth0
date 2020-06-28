# Network Auth

## Auth0

# Certificate & JWT

$ brew install step

$ step crypto jwk create pub.json key.json

$ cat pub.json | step crypto jwk keyset add keys.json

$ JWT=$(step crypto jwt sign \
    --key key.json \
    --iss "admin@freighttrust.com" \
    --aud "sam@freighttrust.com" \
    --sub "ops@freighttrust.com" \
    --exp $(date -v+12M +"%s"))


$ echo $JWT | step crypto jwt verify \
    --jwks keys.json --iss "admin@freighttrust.com" --aud "sam@freighttrust.com"
    
$ cat pub.json
```json
{
  "use": "sig",
  "kty": "EC",
  "kid": "hrLqGEfX24GvJYohaTlpFtOGwUwdDPEYNbukzoacfC4",
  "crv": "P-256",
  "alg": "ES256",
  "x": "Bg78-qgXMjF_8sBteMJT_cNfTweTLymUEMvraRvmh2g",
  "y": "Z7f2pk7ulZ7jeqqhDw7_zEdGVcIJ05aQ4D647AKpIP8"
}
```
