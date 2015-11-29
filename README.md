# cookie-consent-polymer
[![Bower version](https://badge.fury.io/bo/cookie-consent-polymer.svg)](http://badge.fury.io/bo/cookie-consent-polymer)  

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

Check the documentation and demo page for all available options [here](http://zisismaras.me/cookie-consent-polymer/components/cookie-consent-polymer/)

## Blocking 3rd party services
If you have the decline option set, the element will set a cookie `acceptCookies=false`, you can then query this before loading your services.
```javascript
var cookieValue = document.cookie.replace(/(?:(?:^|.*;\s*)acceptCookies\s*\=\s*([^;]*).*$)|^.*$/, "$1");
if (cookieValue == "true") {
  //load external service
}
```

## Todo

* custom theme support for style and position(you have to open it and hack the style for now)
* block cookies until consent option
* more geoip services?

## Contributing
1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

#### Licensed under MIT.
