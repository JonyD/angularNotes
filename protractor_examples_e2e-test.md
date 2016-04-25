## protractor examples (e2e test)
([from](https://docs.angularjs.org/tutorial/step_03)
```javascript
// index.html
/////////////
<html ng-app="phoneCatApp">
<body ng-controller="PhoneListCtrl">
...
Search: <input ng-model="query">
...
<li ng-repeat="phone in phones | filter:query"> </li>
```
```javascript
// test/e2e/scenarios.js
////////////////////////

describe('PhoneCat App', function() {
  describe('Phone list view', function() {

    beforeEach( function(){
      browser.get('app/index.html');
    });

    it('should filter the phone list as a user types into the search box', funtion(){
      var phoneList = element.all( by.repeater( 'phone in phones' ) );	// pick element from the repeater
      var query = element( by.model( 'query') );  			// pick value from the model

      expect( phoneList.count() ).toBe(3);

      query.sendKeys( 'nexus' );
      expect( phoneList.count() ).toBe(1);

      query.clear();
      query.sendKeys( 'motorola' );
      expect( phoneList.count() ).toBe(2);
    });
  
  });
});
```
### main functions to select elements (mostly)
* [element( <LOCATOR> ) - ElementFinder](http://angular.github.io/protractor/#/api?view=ElementFinder)
* [element.all( <LOCATOR> ) - ElementArrayFinder](http://angular.github.io/protractor/#/api?view=ElementArrayFinder)
* [element( by.model() ) - by.model(modelName) ](http://angular.github.io/protractor/#/api?view=ProtractorBy.prototype.model)
* [element( by.repeater() ) - ProtractorBy.prototype.repeater](http://angular.github.io/protractor/#/api?view=ProtractorBy.prototype.repeater)