<script>
    import Person from "./Person.svelte";

    let people = [
        {id: 1, name: "Maksim"},
        {id: 2, name: "Elena"},
        {id: 3, name: "Tatyana"}
    ];

    let value = "";

    function removeFirst() {
        people = people.slice(1)
    }

    function addPerson() {
        // people = people.concat([{
        //     id: Date.now(),
        //     name: value
        // }]);
        people = [...people, {
            id: Date.now(),
            name: value
        }]
        value = '';
    }
</script>

<input type="text" bind:value/>
<button on:click={addPerson}>Add person</button>
<button on:click={removeFirst}>Remove first</button>

<hr/>

{#each people as person, i (person.id)}
    <Person {...person} index={i}/>
{:else}
    <p>No people</p>
{/each}