<script lang="ts">
	import { Tabs } from 'radix-svelte';
	import { getRootContext } from './Tabs.svelte';
	import { getContext } from 'svelte';
	import { browser } from '$app/environment';
	export let value: string;

	const fn = getRootContext();
	fn(value);
</script>

<Tabs.Content class="w-full" {value}>
	<slot />
</Tabs.Content>
<div class="first:{browser ? 'hidden' : 'block'} hidden">
	<slot />
</div>
