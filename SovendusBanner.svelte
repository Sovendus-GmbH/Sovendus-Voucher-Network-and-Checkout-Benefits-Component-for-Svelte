<script context="module" lang="ts">
	interface SovWindow extends Window {
		sovIframes: any;
		sovConsumer: any;
		sovDivId: number;
	}
	declare const window: SovWindow;
</script>

<script lang="ts">
	export let trafficSourceNumber: number;
	export let trafficMediumNumber: number;
	export let sessionId: string;
	export let timestamp: number;
	export let orderId: string;
	export let orderValue: number;
	export let orderCurrency: string;
	export let usedCouponCode: string = '';
	export let consumerSalutation: string = '';
	export let consumerFirstName: string = '';
	export let consumerLastName: string = '';
	export let consumerEmail: string = '';
	export let consumerStreet: string = '';
	export let consumerStreetNumber: string = '';
	export let consumerCity: string = '';
	export let consumerCountry: string = '';
	export let consumerZipcode: string = '';
	export let consumerYearOfBirth: number = 0;

	window.sovDivId = 1 + (window.sovDivId || 0);
	let sovDivId = `sovendus-integration-container-${window.sovDivId}`

	window.sovIframes = window.sovIframes || [];
	window.sovIframes.push({
		trafficSourceNumber: trafficSourceNumber,
		trafficMediumNumber: trafficMediumNumber,
		sessionId: sessionId,
		timestamp: timestamp,
		orderId: orderId,
		orderValue: orderValue,
		orderCurrency: orderCurrency,
		usedCouponCode: usedCouponCode,
		iframeContainerId: sovDivId
	});
	window.sovConsumer = {
		consumerSalutation: consumerSalutation,
		consumerFirstName: consumerFirstName,
		consumerLastName: consumerLastName,
		consumerEmail: consumerEmail,
		consumerStreet: consumerStreet,
		consumerStreetNumber: consumerStreetNumber,
		consumerCity: consumerCity,
		consumerCountry: consumerCountry,
		consumerZipcode: consumerZipcode,
		consumerYearOfBirth: consumerYearOfBirth || ''
	};
	const script = document.createElement('script');
	script.async = true;
	script.src = 'https://api.sovendus.com/sovabo/common/js/flexibleIframe.js';
	script.type = 'text/javascript';
	const body = document.getElementsByTagName('body')[0];
	body.appendChild(script);
</script>

<div id={sovDivId} version="Sovendus Svelte 1.0.0" ></div>
