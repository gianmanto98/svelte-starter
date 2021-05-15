<script>

    import axios from "axios";
    import { onMount } from "svelte";

    let personen = [];

    onMount(()=>{ 
        getPersons();
    })

    function getPersons(){
        axios.get("http://localhost:8080/infections/persons")
        .then(respons =>{
            personen = respons.data;
        })
    }
</script>

<h1>Personen</h1>

<table class = "table">
    <thead>
    <tr>
        <th>ID</th>
        <th>Name</th>
        <th>Birthdate</th>
    </tr>
</thead>

{#each personen as person}
<tr>
    <td>{person.id}</td>
    <td>{person.name}</td>
    <td>{person.birthdate}</td>
</tr>
{/each}
</table>

{#each {length: 3} as _, i}
    <li>{i + 1}</li>
{/each}