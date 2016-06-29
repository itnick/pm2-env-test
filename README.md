# pm2-env-test



## Node.js version: 4.2.3 // pm2 version: 0.15.10

### Case: when environment variable is undefined

```shell
echo $NODE_ENV
```



If `NODE_ENV` is defined, unset it:

```shell
unset NODE_ENV
```



Run the program without pm2:

```shell
node index.js
```

Expected output:

```
NODE_ENV: undefined
NODE_ENV: undefined
NODE_ENV: undefined
```

