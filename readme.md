# Integration Guideline

## Prerequisite

* https://d-64.org/check-in-app/
* Whitepaper explaining security concept especially how data is stored

## The Flow

* Data stored in the app only
* Data copied into the the form of the checkin provider
* Reading data from the checkin-page (name of the place, confirmation information)
* Storing contact tracing entry on the phone 
* All data stored locally

## Changes to be done by the provider

* Check-in form inputs should use [`autocomplete`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete) attributes for
  * `name` (or `given-name` and `family-name` separately)
  * `tel`
  * `street-address`
  * `postal-code`
  * `address-level2`

* For signaling check-in and check-out to the app
  * the `check-in` element should have a `data-wfd-action="check-in"`
  * the `check-out` element should have a `data-wfd-action="check-out"`

* Other data
  * the `location` name on an element (can be anything) with `data-wfd-location="<restaurant-name>"`

## HTML examples

Here is how the check-in form should look like. 

The order of the fields doesn't matter.

You can include the `location` on the `check-in` or in the `check-out` page.

```html
<!-- using name only for the full user name -->
<form data-wfd-location="Frische Küche Restaurant">
  <input autocomplete="name" type="text" />
  <input autocomplete="tel" type="text" />
  <input autocomplete="street-address" type="text" />
  <input autocomplete="postal-code" type="text" />
  <input autocomplete="address-level2" type="text" />
​
  <button data-wfd-action="check-in" type="submit">check-in</button>
</form>
​
<!-- using first and last name separately -->
<form data-wfd-location="Frische Küche Restaurant">
  <input autocomplete="given-name" type="text" />
  <input autocomplete="family-name" type="text" />
  <input autocomplete="tel" type="text" />
  <input autocomplete="street-address" type="text" />
  <input autocomplete="postal-code" type="text" />
  <input autocomplete="address-level2" type="text" />

  <button data-wfd-action="check-in" type="submit">check-in</button>
</form>
```

Example check-out page

```html
<form data-wfd-location="Café um die Ecke">
  <button data-wfd-action="check-out" type="submit">check-out</button>
</form>
```

Other data like the location can be added to any element. In these examples was added to the form for simplicity.

# Submitting the app 

* Please add an issue here: https://github.com/railslove/wfd-masterapp-backlog/issues?q=is%3Aissue+is%3Aopen+label%3A%22integration+done%22
* Please add the "integraton done label"
* Please provide us some information to test the app: Name of your service, logo, URL and a example QR-Code
* Please provide us a link to the security paper, data privacy especially how you're encrypt and store the data. If your service is open source please provide us a link
