<script>
	
	/*
		cpsIsDisabled = true
		clicks = 0;
		CPS = 0;
		count = 0;
	*/
	
	
	export let clicks = 0;
	export let CPS = 0;
	let count = 0;
	let timerTime = 0
	let cpsIsDisabled = true;
	let timerIsDisabled = false;
	export let len;
	export let finalLen;

	function timer(time$s) {
		setTimeout(pause(), 1000)
		cpsIsDisabled = false;
		timerTime = setInterval(() => {
			count++
			if (count === time$s) { 
				clearInterval(timerTime)
				cpsIsDisabled = true;
				timerIsDisabled = true;
			}
		}, 1000)
	}
	function reset() {
		clicks = 0;
		CPS = 0;
		count = 0;
		timerIsDisabled = false;
	}
	function pause(){ console.log("paused") }
	function clicksFn(time$s){ clicks++; CPS = clicks / time$s }
	function timerLength(){
		len = window.prompt("Length of the timer")
		finalLen = parseInt(len)
	}

</script>

<main>
	<!-- create a counte for clicks -->
	<div class = "defDiv">
		
		<button class="Defbutton" disabled={ cpsIsDisabled } on:click={() => {clicksFn(finalLen)}}> <!-- creates a counter -->
			Clicks: {clicks}
			CPS: {CPS}
		</button>
		
	</div>
	<div class = "defDiv">

		<button class="Defbutton" disabled={ timerIsDisabled } id ="timer"on:click={() => {timer(finalLen);}}> <!-- creates a timer -->
			Timer: {count}
		</button>

	</div>

	<div class="defDiv">

		<button class="Defbutton" on:click={() => {reset();}}> <!-- resets the counter -->
			Reset
		</button>

	</div>
	<div class="defDiv">
		<button class=Defbutton on:click={() => {}}>
			Amount of seconds: { len }
		</button>
	</div>
</main>

<style>
	main {
		padding: 1em;
	}
	.Defbutton {
		border-radius: 12px;
		padding: 0.5em;
		background: rgb(255, 255, 255);
		border: none;
		font-size: 1.2em;
		width: 20%;
		height: 10%;
	}
	.Defbutton:active {
		background: rgb(202, 202, 202);
		

	}
	.defDiv {
		text-align: center;
	}
	.helpH1 {
		border-radius: 12px;
		padding: 0.5em;
		border: none;
		font-size: 1.2em;
		width: 20%;
		height: 10%;
		font-size: 1em;
		padding-top: 4em;
	}
</style>