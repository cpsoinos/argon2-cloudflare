# argon2-cloudflare


## Overview
Cloudflare worker for hashing and verifying passwords with argon2.
Can be used via a service binding.


## Dev

### Install deps
npm install

### Dev server
npm run dev

### Deploy worker to cloudflare
npm deploy


## Api


### Hash

#### Endpoint
`POST /hash`

#### Request
```json
{
    "password": "foo"
}
```
or with options:
```json
{
    "password": "some-password",
    "options": {
        "timeCost": 2,
        "memoryCost": 19456,
        "parallelism": 1
    }
}
```

#### Response
```json
{
    "hash": "$argon2id$v=19$m=19456,t=2,p=1$2FtyxY2Dz8nfis44QbdqUA$+HDTT2BgERMyXEEX/o2LbKdROHzQeL4VWbyM7U0p8Ag"
}
```


### Verify

#### Endpoint
`POST /verify`

#### Request

```json
{
    "password": "foo",
    "hash": "$argon2id$v=19$m=19456,t=2,p=1$2FtyxY2Dz8nfis44QbdqUA$+HDTT2BgERMyXEEX/o2LbKdROHzQeL4VWbyM7U0p8Ag"
}
```

#### Response
```json
{
    "matches": true,
}
```
