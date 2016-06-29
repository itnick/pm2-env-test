# pm2-env-test



## Node.js version: 4.2.3 // PM2 version: 0.15.10

### Case: when environment variable is undefined

```shell
echo $NODE_ENV
```

Expected output:

```

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



Run the program with pm2:

```shell
pm2 start env_test.json ; pm2 logs pm2-env-test
```

Expected output:

```
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
```



When you run `pm2 restart`:

```shell
pm2 restart pm2-env-test; pm2 logs pm2-env-test
```

Expected output:

```
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
```





### Case: when environment variable is defined

```shell
echo $NODE_ENV
```

Expected output:

```
development
```



If `NODE_ENV` is not defined, set it:

```shell
export NODE_ENV=development
```



Run the program without pm2:

```shell
node index.js
```

Expected output:

```
NODE_ENV: development
NODE_ENV: development
NODE_ENV: development
```



Run the program with pm2:

```shell
pm2 start env_test.json ; pm2 logs pm2-env-test
```

Expected output:

```
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
```



When you run `pm2 restart`:

```shell
pm2 restart pm2-env-test; pm2 logs pm2-env-test
```

Expected output: **FOR PM2 version 0.15.10**

`NODE_ENV` was changed after `pm2 restart`!

```
pm2-env-test-0 NODE_ENV: development
pm2-env-test-0 NODE_ENV: development
pm2-env-test-0 NODE_ENV: development
```





## Node.js version: 4.2.3 // PM2 version: 1.1.3

PM2 Change Log:

https://github.com/Unitech/PM2/blob/master/CHANGELOG.md



### Case: when environment variable is undefined

```shell
echo $NODE_ENV
```

Expected output:

```

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



Run the program with pm2:

```shell
pm2 start env_test.json ; pm2 logs pm2-env-test
```

Expected output:

```
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
```



When you run `pm2 restart`:

```shell
pm2 restart pm2-env-test; pm2 logs pm2-env-test
```

Expected output:

```
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
```





### Case: when environment variable is defined

```shell
echo $NODE_ENV
```

Expected output:

```
development
```



If `NODE_ENV` is not defined, set it:

```shell
export NODE_ENV=development
```



Run the program without pm2:

```shell
node index.js
```

Expected output:

```
NODE_ENV: development
NODE_ENV: development
NODE_ENV: development
```



Run the program with pm2:

```shell
pm2 start env_test.json ; pm2 logs pm2-env-test
```

Expected output:

```
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
pm2-env-test-0 NODE_ENV: testing
```



When you run `pm2 restart`:

```shell
pm2 restart pm2-env-test; pm2 logs pm2-env-test
```

Actual output:

`NODE_ENV` was changed after `pm2 restart`!

```
pm2-env-test-0 NODE_ENV: development
pm2-env-test-0 NODE_ENV: development
pm2-env-test-0 NODE_ENV: development
```



Try `--skip-env` option:

```
pm2 kill
pm2 start env_test.json ; pm2 logs pm2-env-test
pm2 restart --skip-env pm2-env-test; pm2 logs pm2-env-test
```

Actual output:

```
pm2-env-test-0 NODE_ENV: development
pm2-env-test-0 NODE_ENV: development
pm2-env-test-0 NODE_ENV: development
```

