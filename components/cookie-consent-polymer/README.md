# cookie-consent-polymer
[![Bower version](https://badge.fury.io/bo/cookie-consent-polymer.svg)](http://badge.fury.io/bo/cookie-consent-polymer)
[![Build Status](https://travis-ci.org/zisismaras/cookie-consent-polymer.svg?branch=master)](https://travis-ci.org/zisismaras/cookie-consent-polymer)  

The cookie-consent-polymer element provides a dialog with the option to accept website cookies according
to the EU law.  
Uses [http://freegeoip.net](http://freegeoip.net) for geolocation and will only show for visitors from countries
where the law is active.


## Installing
```
bower install cookie-consent-polymer --save
```

## Using

```html
<cookie-consent-polymer
    dialog-text="This website uses cookies to ensure you get the best experience on our website."
    more-info-link="/policy"
    more-info-text="Learn more"
    button-text="Accept"
    expires-in-days=30></cookie-consent-polymer>
```

## Features

* Only show to EU visitors where the law is active
* Decline button option with an optional fallback url for redirection
* Implicit scrolling or navigating consent option
* Add custom text to dialog and buttons
* Support for custom themes using polymer shared styles
* ...More micro configurations like expiring time, auto reload, cookie path etc

Check the documentation and demo page for all available options [here](http://zisismaras.me/cookie-consent-polymer/components/cookie-consent-polymer/)

## Custom Themes

You can style the element as described in the [polymer documentation](https://www.polymer-project.org/1.0/docs/devguide/styling.html#style-modules).  
##### Example
First create a custom style element
```html
<link rel="import" href="../polymer/polymer.html">

<dom-module id="my-theme">
  <template>
    <style>
      cookie-consent-polymer {
        --dialog-theme: {
          top: 60px;
          background-color: #E1F5FE;
          color: #212121;
        };
        --accept-button-theme: {
          background-color: #29B6F6;
          color: #212121;
        };
        --decline-button-theme: {
          background-color: #29B6F6;
          color: #212121;
        };
      }
    </style>
  </template>
</dom-module>
```
To use it inside an element
```html
<link rel="import" href="../my-theme/my-theme.html">
<dom-module id="my-other-element">
  <template>
    <style include="my-theme"></style>
    Hi
  </template>
  <script>Polymer({is: 'my-other-element'});</script>
</dom-module>
```
To use it in the main document
```html
<link rel="import" href="../my-theme/my-theme.html">

<style is="custom-style" include="my-theme"></style>
```
##### Custom CSS properties
* `--cookie-consent-theme` => the element itself
* `--dialog-theme` => the whole paper-dialog
* `--dialog-body-theme`, `--policy-link-theme`, `--accept-button-theme`, `--decline-button-theme` => individual items
* `--dialog-items-theme` => all the items in the dialog

Check the demo directory for two examples.


## Blocking 3rd party services until cookie is set
If you have the decline option set, the element will set a cookie `acceptCookies=false` when the decline button is clicked, you can then query this before loading your services.
```javascript
var cookieValue = document.cookie.replace(/(?:(?:^|.*;\s*)acceptCookies\s*\=\s*([^;]*).*$)|^.*$/, "$1");
if (cookieValue == "true") {
  //load external service
}
```
This will block the services until the cookie has been set to `"true"`, use the `reload-after-action` property to do a reload after the user has consented.


## Contributing
1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

#### Licensed under MIT.
