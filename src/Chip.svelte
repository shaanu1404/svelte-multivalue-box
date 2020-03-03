<script>
export let subject;
</script>

<div class="chip">
	{subject}
	<span on:click>&times;</span>
</div>

<style>
	.chip{
		font-size: .8rem;
		text-transform: capitalize;
		display: inline-block;
		background: orange;
		padding: 4px 8px;
		border-radius: 40px;
		margin: 0 4px 4px 0;
	}
	.chip span{
		cursor: pointer;
	}
</style>
