<script lang="ts">
	export let title = "";
</script>

<div class="bg-white py-5 rounded-lg border-1 border-gray-300 hds">
	<h3 class="text-lg font-bold text-gray-700 mb-2 border-l-3 border-blue-900 px-5 py-0.5">{title}</h3>
	<div class="px-5">
		<slot />
	</div>
</div>
