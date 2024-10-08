# Sovendus Voucher Network & Checkout Benefits Component for Svelte

## Install through npmjs

Execute the following command to install it through npm:

```bash
npm install --save sovendus-voucher-network-and-checkout-benefits-svelte
```

## Integrate into your Svelte app

You can then use the component as with the following example on your order success / thank you page:

[Click here for detailed information on the parameters and which ones are required.](https://developer-hub.sovendus.com/Voucher-Network-Checkout-Benefits/Parameter)

```svelte
<SovendusBanner
 trafficSourceNumber={YOU_TRAFFIC_SOURCE_NUMBER}
 trafficMediumNumber={YOU_TRAFFIC_MEDIUM_NUMBER}
 sessionId="session-sdsdfsdfsd"
 timestamp={1705504738}
 orderId="order-12345"
 orderValue={15.99}
 orderCurrency="EUR"
 usedCouponCode="CouponCodeFromOrder"
 consumerSalutation="Mrs."
 consumerFirstName="John"
 consumerLastName="Smith"
 consumerEmail="test@example.com"
 consumerPhone="+49155123456789"
 consumerStreet="Street Name"
 consumerStreetNumber="12/4"
 consumerCity="CityName"
 consumerCountry="DE"
 consumerZipcode="94419"
 consumerYearOfBirth={1991}
 consumerDateOfBirth={"01.12.2020"}
/>
```

### Additional steps for Switzerland

For Switzerland it is also required to add the following component on the home page / page where users will land coming from the Sovendus Voucher Network

```svelte
<SovendusLandingPage />
```
