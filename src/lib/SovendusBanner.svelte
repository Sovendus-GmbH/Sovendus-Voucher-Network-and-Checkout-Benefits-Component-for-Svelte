<script context="module" lang="ts">
	interface SovWindow extends Window {
		sovIframes: any;
		sovConsumer: any;
		sovDivId: number;
	}
	declare const window: SovWindow;
</script>

<script lang="ts">
	import { onMount } from 'svelte';
	export let trafficSourceNumber: number;
	export let trafficMediumNumber: number;
	export let sessionId: string = '';
	export let timestamp: number = 0;
	export let orderId: string = '';
	export let orderValue: number = 0;
	export let orderCurrency: string = '';
	export let usedCouponCode: string = '';
	export let consumerSalutation: string = '';
	export let consumerFirstName: string = '';
	export let consumerLastName: string = '';
	export let consumerEmail: string = '';
	export let consumerPhone: string = '';
	export let consumerStreet: string = '';
	export let consumerStreetNumber: string = '';
	export let consumerCity: string = '';
	export let consumerCountry: string = '';
	export let consumerZipcode: string = '';
	export let consumerDateOfBirth: string = '';
	export let consumerYearOfBirth: number = 0;
	let sovDivId: string = '';
	onMount(() => {
		window.sovDivId = 1 + (window.sovDivId || 0);
		sovDivId = `sovendus-integration-container-${window.sovDivId}`;

		window.sovIframes = window.sovIframes || [];
		window.sovIframes.push({
			trafficSourceNumber: trafficSourceNumber,
			trafficMediumNumber: trafficMediumNumber,
			sessionId: sessionId,
			timestamp: timestamp || '',
			orderId: orderId,
			orderValue: orderValue || '',
			orderCurrency: orderCurrency,
			usedCouponCode: usedCouponCode,
			iframeContainerId: sovDivId,
			integrationType: 'svelte-1.0.9'
		});
		window.sovConsumer = {
			consumerSalutation: consumerSalutation,
			consumerFirstName: consumerFirstName,
			consumerLastName: consumerLastName,
			consumerEmail: consumerEmail,
			consumerPhone: consumerPhone,
			consumerStreet: consumerStreet,
			consumerStreetNumber: consumerStreetNumber,
			consumerCity: consumerCity,
			consumerCountry: consumerCountry,
			consumerZipcode: consumerZipcode,
			consumerYearOfBirth: consumerYearOfBirth || '',
			consumerDateOfBirth: consumerDateOfBirth,
		};
		const script = document.createElement('script');
		script.async = true;
		script.src = 'https://api.sovendus.com/sovabo/common/js/flexibleIframe.js';
		script.type = 'text/javascript';
		const body = document.getElementsByTagName('body')[0];
		body.appendChild(script);
	});
</script>

<div id={sovDivId} />
