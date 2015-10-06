# stub-service

__NOTE__ this is a work in progress, not a production-ready
documentation

Create stub http(s) services for e2e tests

Start as many services as you need. Use an interface
similar to angularjs ngMockE2E.$httpBackend to configure them.

```javascript
var factory = require('stub-service');
var options = {
  address: 'localhost',
  port: 3005,
  baseAddress: '/api/v2.2'
};

var service = factory.create(options);

var items = [1,2,3];

service.whenGet('/items').respond(items);

service.whenPost('/items').respond( function (method, url, data) {
  var item = JSON.parse(data);
  items.push(item);
  return [200, item, {}];
});
```
