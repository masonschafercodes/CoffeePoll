<script lang="ts">
	export let linkName: string;
	export let linkUrl: string;
</script>

<a href={linkUrl} class="font-brand hover:bg-gray-50 px-2 py-1.5 rounded">{linkName}</a>
