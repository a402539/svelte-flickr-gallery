<script>
  import Gallery from './Gallery.svelte';
  import _ from 'lodash'

	let tag = 'dogs', searchVal = 'dogs', placeholder = 'dogs';
  let updateSearchDebounced = _.debounce(val => { tag = val ==='' ? placeholder : val}, 250, false);
  
  $: updateSearchDebounced(searchVal);
</script>

<div class="app-root">
	<div class="app-header" id="top">
		<h2>Svelte Flickr Gallery</h2>
		<input class="app-input" bind:value={searchVal} {placeholder}/>
	</div>
	<Gallery {tag}></Gallery>
</div>



<style>

.app-root {
  text-align: center;
}

.app-header {
  background-color: #222;
  padding: 10px;
  color: white;
  font-size: 20pt;
}

.app-input {
  line-height: 30px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 14px;
  padding: 0 8px;
  color: #666;
  width: 50%;
  margin-bottom: 30px;
}
</style>