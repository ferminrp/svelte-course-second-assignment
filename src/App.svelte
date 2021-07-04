<script>
	let password = "";
	let generatedPasswords = [];

	function addPassword() {
		generatedPasswords = [ ...generatedPasswords, password];
		console.log(generatedPasswords);
	}

	function removePassword(password){
		console.log("will remove " + password)
		generatedPasswords = generatedPasswords.filter(n => n != password)
	}
</script>


<h1>Assignment</h1>

<p>Solve these tasks.</p>

<ol>
	<li>Add a password input field and save the user input in a variable.</li>
	<li>Output "Too short" if the password is shorter than 5 characters and "Too long" if it's longer than 10.</li>
	<li>Output the password in a paragraph tag if it's between these boundaries.</li>
	<li>Add a button and let the user add the passwords to an array.</li>
	<li>Output the array values (= passwords) in a unordered list (ul tag).</li>
	<li>Bonus: If a password is clicked, remove it from the list.</li>
</ol>

<input bind:value="{password}" type="password">
<button on:click="{addPassword}">Add Password</button>

{#if password.length > 0 && password.length < 5}

<p>Password is too short!</p>

{:else if password.length > 10}

<p>Password is too long!</p>

{:else}

<p>{password}</p>

{/if}


<h2>Generated Passwords</h2>
<ul>
{#each generatedPasswords as password, i}
<li on:click="{() => removePassword(password)}">{password}</li>
{/each}
</ul>
