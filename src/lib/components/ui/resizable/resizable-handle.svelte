<script lang="ts">
	import type { MouseEventHandler } from 'svelte/elements';
	import DragHandleDots2 from 'svelte-radix/DragHandleDots2.svelte';
	import * as ResizablePrimitive from 'paneforge';
	import { cn } from '$lib/utils.js';

	interface Props extends Omit<ResizablePrimitive.PaneResizerProps, 'ondblclick'> {
		withHandle?: boolean;
		ondblclick?: MouseEventHandler<HTMLButtonElement>;
	}

	let { class: className, withHandle = false, el, ondblclick }: Props = $props();
</script>

<ResizablePrimitive.PaneResizer
	bind:el
	class={cn(
		'bg-border relative flex w-px items-center justify-center',
		'focus-visible:ring-ring focus-visible:outline-none focus-visible:ring-1 focus-visible:ring-offset-1',
		'data-[direction=vertical]:h-px data-[direction=vertical]:w-full data-[direction=vertical]:after:left-0 data-[direction=vertical]:after:h-1 data-[direction=vertical]:after:w-full',
		'data-[direction=vertical]:after:-translate-y-1/2 data-[direction=vertical]:after:translate-x-0',
		'[&[data-direction=vertical]>div]:rotate-90',
		'after:absolute after:inset-y-0 after:left-1/2 after:w-1 after:-translate-x-1/2',
		className
	)}
>
	{#if withHandle}
		<button
			class="bg-border z-10 flex h-4 w-3 cursor-ew-resize items-center justify-center rounded-sm border"
			{ondblclick}
		>
			<DragHandleDots2 class="h-2.5 w-2.5" />
		</button>
	{/if}
</ResizablePrimitive.PaneResizer>
