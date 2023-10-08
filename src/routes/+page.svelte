<script>
    import { arrPokemon } from "../stores/pokestore.js";
    import PokemonCard from "../components/pokemonCard.svelte";

    let searchTerm = '';
    let filteredPokemon = [];

    $: {
        if (searchTerm){
            filteredPokemon = $arrPokemon.filter(pokemon => pokemon.name.includes(searchTerm));
        } else {
            filteredPokemon = [...$arrPokemon];
        }
    }

</script>

<svelte:head>
    <title>포켓몬위키</title>
</svelte:head>

<h1 class="text-3xl text-center my-8 underline">
    포켓몬 위키
</h1>

<input type="text"
       class="w-full rounded-md text-lg p-4 mb-8 border-2 border-gray-200"
       placeholder="포켓몬 검색"
       bind:value={searchTerm}
/>

<div class="grid gap-4 md:grid-cols-3 grid-cols-2">
    {#each filteredPokemon as pokemon}
        <PokemonCard pokemon="{pokemon}"/>
    {/each}
</div>
