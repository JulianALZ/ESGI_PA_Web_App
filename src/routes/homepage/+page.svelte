<script>
	import "./homepage.css";

	import { onMount } from 'svelte';

	onMount(() => {
		const token = localStorage.getItem('token');

		if (!token) {
			window.location.href = '/login';
			return;
		}

		try {
			const decodedToken = jwt_decode(token);
			const currentTime = Date.now() / 1000;
			if(decodedToken.exp < currentTime){
				window.location.href = '/login';
			}
		} catch (error) {
			console.log(error);
		}
	});


	// Importez tous les composants ici
	import Header from './components/Header.svelte';
	import BalanceSummary from './components/BalanceSummary.svelte';
	import LineChart from './components/LineChart.svelte';
	import ActionButtons from './components/ActionButtons.svelte';
	import CryptoList from './components/CryptoList.svelte';


	import "./homepage.css";
</script>

<div class="gradient-custom">
	<Header />
	<BalanceSummary />
	<LineChart />
	<ActionButtons />
	<CryptoList />
</div>




