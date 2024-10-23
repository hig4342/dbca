<script lang="ts">
	import * as ResizablePrimitive from 'paneforge';
	import { cn } from '$lib/utils.js';

	let {
		children,
		class: className,
		direction,
		paneGroup = $bindable(),
		el,
		...rest
	}: ResizablePrimitive.PaneGroupProps = $props();
</script>

<ResizablePrimitive.PaneGroup
	bind:el
	bind:paneGroup
	{direction}
	class={cn('flex h-full w-full data-[direction=vertical]:flex-col', className)}
	{...rest}
>
	{@render children?.()}
</ResizablePrimitive.PaneGroup>
