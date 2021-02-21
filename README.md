# components-practice

## Project setup
```
npm install
```

## Adding js files into convert-units node module
#### Añadiendo archivo currency.js en la ruta 'node_modules/convert-units/test'
```
var convert = require('../lib')
  , assert = require('assert')
  , tests = {};

tests['USD to USD'] = function () {
  assert.strictEqual( convert(1).from('USD').to('USD') , 1);
};

tests['EUR to EUR'] = function () {
    assert.strictEqual( convert(1).from('EUR').to('EUR') , 1);
};

tests['SVC to SVC'] = function () {
    assert.strictEqual( convert(1).from('SVC').to('SVC') , 1);
};
  
tests['GBP to GBP'] = function () {
    assert.strictEqual( convert(1).from('GBP').to('GBP') ,1);
};
  
tests['HKD to HKD'] = function () {
      assert.strictEqual( convert(1).from('HKD').to('HKD') , 1);
};
  
tests['AED to AED'] = function () {
      assert.strictEqual( convert(1).from('AED').to('AED') , 1);
};

tests['USD to EUR'] = function () {
    assert.strictEqual( convert(1).from('USD').to('EUR') , 1.21169);
  };

tests['USD to SVC'] = function () {
    assert.strictEqual( convert(1).from('USD').to('SVC') , 0.114286);
  };

tests['USD to GBP'] = function () {
  assert.strictEqual( convert(1).from('USD').to('GBP') , 1.40086);
};

tests['USD to HKD'] = function () {
    assert.strictEqual( convert(1).from('USD').to('HKD') , 0.12898);
};


module.exports = tests;
var convert = require('../lib')
  , assert = require('assert')
  , tests = {};


module.exports = tests;

```

#### Añadiendo archivo currency.js en la ruta 'node_modules/convert-units/lib/definitions'
```
var currency;

currency = {
  USD: {
    name: {
      singular: 'Dolar estadounidense'
    , plural: 'Dolar estadounidense'
    }
  , to_anchor: 1
  }
, EUR: {
    name: {
      singular: 'Euro'
      , plural: 'Euros'
    }
    , to_anchor: 1.21169
  }
, SVC: {
    name: {
      singular: 'Colon Salvadoreño'
      , plural: 'Color Salvadoreño'
    }
    , to_anchor: 0.114286
  }
, GBP: {
    name: {
      singular: 'Libra esterlina'
    , plural: 'Libras esterlinas'
    }
  , to_anchor: 1.4008
  }
, HKD: {
    name: {
      singular: 'Dolar de Hong Kong'
    , plural: 'Dolares de Hong Kong'
    }
  , to_anchor: 0.12898
  }
};

module.exports = {
  metric: currency
, _anchors: {
    metric: {
      unit: 'USD'
    , ratio: 1
    }
  }
};

```

#### Modificando el archivo index.js en la ruta 'node_modules/convert-units/lib'

```
Al objeto measures agregarle al final el valor ", currency : require('./definitions/currency')"
```


### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
