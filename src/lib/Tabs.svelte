<script lang="ts" context="module">
	export type RootContext = (s: string) => void;
	export const getRootContext = () => getContext<RootContext>('tab-root');
	const setRootContext = (ctx: RootContext) => setContext('tab-root', ctx);
</script>

<script lang="ts">
	import { Tabs } from 'radix-svelte';
	import { getContext, setContext } from 'svelte/internal';

	export { classes as class };
	let classes = 'w-full mt-4';

	let values = [] as string[];
	let value: string;
	setRootContext((s) => {
		values = [...new Set([...values, s])];
		value = values[0];
	});
</script>

<Tabs.Root class={classes} bind:value>
	<div class="flex flex-col-reverse">
		<slot />
		<Tabs.List class="flex items-center border border-zinc-700 p-2 rounded-md">
			{#each values as label}
				<Tabs.Trigger
					class="px-4 py-3 transition font-medium group relative flex items-center 
		justify-center {label === value && 'bg-zinc-800 rounded-md'}"
					value={label}
				>
					<span class="relative [data-state=active]:text-c-on-bg">{label}</span>
				</Tabs.Trigger>
			{/each}
		</Tabs.List>
	</div>
</Tabs.Root>
