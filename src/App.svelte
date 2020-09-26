<script>
	function calculate_age(dob) { 
		if(!dob){
			return undefined;
		}
		var diff_ms = Date.now() - new Date(dob).getTime();
		var age_dt = new Date(diff_ms); 
	
		return Math.abs(age_dt.getUTCFullYear() - 1970);
	}
	export let name;
	let dob;

	$: age = calculate_age(dob)
	_: data = `{
				testData {
				hello
				}
			}`
</script>

<main>
	<h1>Hello {name}!</h1>
	<input type="text" bind:value={name}>
	<input type="date" bind:value={dob}>
	<p>Your date of birth is: {dob} and your age is: {age}</p>
	<p>{data.testData.hello}</p>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>