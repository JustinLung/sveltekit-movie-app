<script>
	let inputValue = '';
  import {goto} from '$app/navigation'

  function submitSearch() {
    goto('/search/' + inputValue)
  }
</script>

<form on:submit|preventDefault={submitSearch} class="search">
	<input bind:value={inputValue} type="search" name="search" placeholder="search for a movie..." />
	<button type="submit">Search</button>
</form>
