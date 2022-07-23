
<script>
    import {goto} from "$app/navigation"
    let inputValue = ""
    function handelSeach() {
        if(inputValue) {
            goto("/search/"+inputValue)
        }
       
    }
</script>

<div class="search" svelkit:noscroll>
	<input bind:value={inputValue} type="text" placeholder="Seach movie" />
	<button on:click={handelSeach}>Search</button>
</div>

<style>
	.search {
		position: relative;
		width: 40%;
        margin: 0 auto 2rem;
        max-width: 350px;
	}
	button {
		position: absolute;
		right: 0;
		font-size: 0.7rem;
		padding: 0 1rem;
		height: 100%;
		background: rgb(96, 110, 201);
		border: none;
		bottom: 50%;
		transform: translate(0, 50%);
		color: white;
        border-radius: 0 10px 10px 0;
        cursor: pointer;
	}
	input {
		width: 100%;
		border: none;
		font-size: 1rem;
		outline: none;
		color: rgb(255, 255, 255);
		padding: 0.5rem 0.1rem;
		border-radius: 10px;
		background-color: rgb(63, 63, 63);
        box-sizing: border-box;
        padding: 1rem;
	}
</style>
