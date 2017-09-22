# user-settings-dialog

A Polymer Element showing a button that opens a dialog with user settings.

### Example
```js
demo.buildSearchStateFunction = function(state) {
  return {
    date: state.date || [],
    list: state.list || []
  };
};

demo.buildSearchTermsFunction = function(state) {
  return {
    'Start Date': state.date && state.date.length === 2 && state.date[0] ? [state.date[0]] : [],
    'End Date': state.date && state.date.length === 2 && state.date[1] ? [state.date[1]] : [],
    'List Data': state.list
  };
};

demo.resetSearchDatesFunction = function(state, start, end) {
  return {
    date: (start || end) ? [start, end] : state.date,
    list: state.list
  };
};

demo.cases = [{
  name: 'Case #1',
  searches: [],
  sendEmailAlert: false
}, {
  name: 'Case #2',
  searches: [{
    lastAutomatedRun: new Date('01-05-2017'),
    lastViewedByUser: new Date('01-01-2017'),
    notify: false,
    uiState: '{\"list\": [\"item1\"]}'
  }],
  sendEmailAlert: false
}, {
  name: 'Case #3',
  searches: [{
    lastAutomatedRun: new Date('01-05-2017'),
    lastViewedByUser: new Date('01-02-2017'),
    notify: true,
    uiState: '{\"list\": [\"item1\", \"item2\"]}'
  }],
  sendEmailAlert: true
}, {
  name: 'Case #4',
  searches: [{
    lastAutomatedRun: new Date('01-05-2017'),
    lastViewedByUser: new Date('01-03-2017'),
    notify: false,
    uiState: '{\"date\": [\"01-01-2017\", null], \"list\": [\"item3\", \"item4\"]}'
  }, {
    lastAutomatedRun: new Date('01-05-2017'),
    lastViewedByUser: new Date('01-04-2017'),
    notify: true,
    uiState: '{\"date\": [\"01-02-2017\", \"01-03-2017\"], \"list\": [\"item5\", \"item6\"]}'
  }],
  sendEmailAlert: true
}];
```

```html
<user-settings-dialog
  build-search-state-function="[[buildSearchStateFunction]]"
  build-search-terms-function="[[buildSearchTermsFunction]]"
  reset-search-dates-function="[[resetSearchDatesFunction]]"
  show-search
  cases="[[cases]]"
  user-id="1234"
  username="demo_user"
  blur-images="{{blurImages}}"
  email-address="{{emailAddress}}"
  notifications="{{notifications}}"
  notification-date="{{notificationDate}}"
  notification-interval="{{notificationInterval}}"
  search-parameters="{{searchParameters}}">
</user-settings-dialog>
```

```
### Dependencies

Dependencies are installed using [Bower](http://bower.io/):

    npm install -g bower
    bower install

### Testing

Tests are run using [web-component-tester](https://github.com/Polymer/web-component-tester):

    npm install -g web-component-tester
    wct

### Demonstration & Documentation

Demonstration and documentation are viewed using [polyserve](https://github.com/PolymerLabs/polyserve):

    npm install -g polyserve
    polyserve

