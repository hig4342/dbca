<script lang="ts">
	import * as Resizable from '$lib/components/ui/resizable';
	import type { PaneGroupAPI } from 'paneforge';

	let paneGroup: PaneGroupAPI;
</script>

<Resizable.PaneGroup direction="horizontal" class="h-full w-full rounded-lg border" bind:paneGroup>
	<Resizable.Pane defaultSize={50}>
		<div class="flex h-full items-center justify-center p-6">
			<span class="font-semibold">Code Editor</span>
		</div>
	</Resizable.Pane>
	<Resizable.Handle
		withHandle
		ondblclick={() => {
			paneGroup.setLayout([50, 50]);
		}}
	/>
	<Resizable.Pane defaultSize={50}>
		<div class="flex h-full items-center justify-center p-6">
			<span class="font-semibold">Content</span>
		</div>
	</Resizable.Pane>
</Resizable.PaneGroup>
