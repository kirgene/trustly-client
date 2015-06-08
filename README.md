# Trustly Client

Node.js client for trusty integrations. Right now it doesn´t includes the withdrawal, feel free to submit a pull request. You can use callback style or promises.


##Getting started

Install the module with: `npm install trustly-client`

```javascript
    var tClient = require('trustly-client');
    var tClientKP = new Client (configuration);
   tClientKP.init()
   .then(function (tClientKP) {
        return tClientKP.deposit({
            NotificationURL: 'http://127.0.0.1:4343/notification',
            EndUserID: 'john.doe@example.com',
            MessageID: '111112111221',
            Locale: 'es_ES',
            Amount: '1.00',
            Currency: 'EUR',
            SuccessURL: 'http://127.0.0.1:4343/success',
            FailURL: 'http://127.0.0.1:4343/fail',
            HoldNotifications: 1
        });
    })
    .then(function (response) {
        console.log(util.inspect(response, false, 20, true));
    })
    .fail(function (error) {
        console.log(util.inspect(error, false, 20, true));
    });
```

## Documentation

Basically you should pass, the config object composed by:

- [required] privateKeyPath: Path to you private key
- [optional] publicKeyPath: Path to a public key (for the general cases you don't need it, i package the trusty public key)
- [required] username: Your trustly api username
- [required] password: Your trustly api password 

The 2 basic methods are: deposit, refund. They uses the parameters described in trusty documentation.
Then you have a method to handle the notifications: handleNotification. Accepts a Json string or a Json object, with the notification.

Also there are other functions to sign, verify the data, compose the request. Feel free to explore the code.

## Release History
####(1.0.0 Lastest)
- Firsts steps. Basic usage finishes: Deposit, refund and handleNotification functions.
- Sign, verify and compose requests, and responses done. 

## License
Licensed under the MIT license. 2015