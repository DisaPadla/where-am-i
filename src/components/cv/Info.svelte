<script lang="ts">
	let count = 0;

	function add() {
		count += 1;
	}

	function subtract() {
		count -= 1;
	}
</script>

<div class="info">
  <p class='text typewriter'>
    A man moving his hands away from his forehead sideways, in a mind-explosion gesture. An overlaid animation enforces the explosion character.
	</p>
</div>

<style>
	@keyframes typing {
		from { width: 0 }
		to { width: 100% }
	}

	@keyframes blink-caret {
		from, to { border-color: transparent }
		50% { border-color: orange; }
	}

	.typewriter {
		overflow: hidden;
  	border-right: .15em solid orange;
		white-space: nowrap;
		animation: typing 4s steps(40, end), blink-caret 2s step-end infinite;
	}
</style>
