<script lang="ts">
	import { Switch as SwitchPrimitive } from 'bits-ui';
	import { cn } from '$lib/utils.js';

	type $$Props = SwitchPrimitive.Props;
	type $$Events = SwitchPrimitive.Events;

	let className: $$Props['class'] = undefined;
	export let checked: $$Props['checked'] = false;
	export let label: string = '';
	export let disabled: $$Props['disabled'] = false;
	export let onClick: ((event: MouseEvent) => void) | undefined = undefined;
	export let onKeydown: $$Events['keydown'] = undefined;
	export { className as class };
</script>

<label class="inline-flex items-center gap-2">
	{#if label}
		<slot name="label">{label}</slot>
	{/if}
	<SwitchPrimitive.Root
		bind:checked
		class={cn(
			'focus-visible:ring-ring focus-visible:ring-offset-background data-[state=checked]:bg-primary data-[state=unchecked]:bg-input peer inline-flex h-[20px] w-[36px] shrink-0 cursor-pointer items-center rounded-full border-2 border-transparent shadow-sm transition-colors focus-visible:ring-2 focus-visible:ring-offset-2 focus-visible:outline-none disabled:cursor-not-allowed disabled:opacity-50',
			className
		)}
		{...$$restProps}
		onclick={onClick}
		on:keydown={onKeydown}
		{disabled}
	>
		<SwitchPrimitive.Thumb
			class={cn(
				'bg-background pointer-events-none block h-4 w-4 rounded-full shadow-lg ring-0 transition-transform data-[state=checked]:translate-x-4 data-[state=unchecked]:translate-x-0'
			)}
		/>
	</SwitchPrimitive.Root>
</label>
