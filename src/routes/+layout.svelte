<script lang="ts">
	import '../app.css';
	import Nprogress from 'nprogress';
	import { beforeNavigate, afterNavigate } from '$app/navigation';
	
	let { children } = $props();

	beforeNavigate(() => Nprogress.start());
	afterNavigate(() => Nprogress.done());
	Nprogress.configure({
		showSpinner: false,
	});
</script>

{@render children()}
