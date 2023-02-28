<script>
	import { onMount } from 'svelte';
	import { WalletProvider, ConnectionProvider } from '@svelte-on-solana/wallet-adapter-ui';
	import { clusterApiUrl } from '@solana/web3.js';

	import '../app.css';

	let wallets;

	const network = clusterApiUrl('mainnet-beta');
	// const network = clusterApiUrl('devnet');

	const localStorageKey = 'solWalletAdapter';

	onMount(async () => {
		const { PhantomWalletAdapter } = await import('@solana/wallet-adapter-wallets');

		wallets = [new PhantomWalletAdapter()];
	});
</script>

<WalletProvider {localStorageKey} {wallets} autoConnect />
<ConnectionProvider {network} />

<slot />
