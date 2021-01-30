# Installation
To install the module run the following command `npm install emberdyn-cron-scheduler`

# Configuration
* Create a config file containing configuration like this.
* Each cron is defined as a separate property of the object returned from the config file. 
* Each cron contains a `frequency` property which defines the cron frequency and also a `handler` property which defines the path to the handler that will be run when the cron job is executed. 

## config.js
```
module.exports = {
    sayhello: {
        frequency: '* * * * *',
        handler: 'handlers/sayhello'
    },
    saygoodbye: {
        frequency: '* * * * *',
        handler: 'handlers/saygoodbye'
    }
}
```

# Usage
```
const { initCrons } = require('emberdyn-cron-scheduler');
const config = require('./config');

initCrons(config)
```

Then in the location defined in the `handler` property create a file with the given name and return a function like this:

## handlers/sayhello.js
```
module.exports = () => {
    console.log("Hello World!");
}
```

## handlers/saygoodbye.js
```
module.exports = () => {
    console.log("Have a great day!");
}
```
