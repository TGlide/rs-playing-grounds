<script lang="ts">
	import { Slider, Toggle } from 'radix-svelte';
	import type { ResolvedProps } from 'radix-svelte';

	let toggleProps: ResolvedProps<typeof Toggle> = {
		Root: {
			pressed: false
		}
	};
</script>

<Toggle.Root
	aria-label="Toggle italic"
	class="grid h-9 w-9 place-items-center items-center
	justify-center rounded bg-white text-base leading-4 text-orange-800 shadow-lg
	hover:bg-orange-100 focus:ring-2 focus:ring-black
	data-[state=on]:bg-orange-200 data-[state=on]:text-orange-900"
	bind:pressed={toggleProps.Root.pressed}
>
	✔
</Toggle.Root>

<form>
	<Slider.Root
		class="relative flex h-5
		w-[200px] touch-none select-none items-center 
		data-[orientation=vertical]:h-[200px] 
		data-[orientation=vertical]:w-5 
		data-[orientation=vertical]:flex-col
		"
		value={[50]}
		aria-label="Volume"
	>
		<Slider.Track
			class="relative grow rounded-full bg-black/50 
					data-[orientation=horizontal]:h-[3px] 
					data-[orientation=vertical]:w-[3px]
					h-[3px]"
		>
			<Slider.Range
				class="absolute rounded-full bg-white 
				data-[orientation=horizontal]:h-full data-[orientation=vertical]:w-full"
			/>
		</Slider.Track>
		<Slider.Thumb
			class="block h-5 w-5 rounded-[10px] bg-white shadow-[0_2px_10px] shadow-black/10 
					hover:bg-vermilion-100 focus:shadow-[0_0_0_5px] focus:shadow-black/30 focus:outline-none"
		/>
	</Slider.Root>
</form>
