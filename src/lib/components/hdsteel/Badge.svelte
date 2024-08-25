<script lang="ts">
	export let text = "";
	export let isOutline = false;
	export let color = "blue";
	export let colorStrong = "900";

	let css = ``;
	if (isOutline) {
		css += `px-2 py-0.5 bg-white border-1 border-${color}-${colorStrong} text-${color}-${colorStrong}`;
	} else {
		css += `px-2 py-0.5 text-white bg-${color}-${colorStrong}`;
	}
</script>

<div class="fcc mx-auto w-[fit-content] rounded-full {css}">
	{text}
</div>
