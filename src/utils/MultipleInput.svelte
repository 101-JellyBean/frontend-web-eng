<script>
    // the title should be unique to find the right data
    export let title;
    export let type = "text"
    export let required = true;
    export let data = [];

    import Card from './Card.svelte';
    import { onMount } from 'svelte';

    function addInput(value = "") {
        let inputs = document.getElementById(title + "-inputs");
        // create div that holds our button and input
        let div = document.createElement("div");
        div.classList.add("form");
        div.classList.add("row");
        // create the deletion button
        let del = document.createElement("btn");
        del.classList.add("btn");
        del.classList.add("m-1");
        del.classList.add("btn-danger");
        del.classList.add("col-2");
        del.innerText = "X";
        del.onclick = () => {
            div.remove();
        }
        del.type = "button";
        // create the input field
        let input = document.createElement("input");
        input.type = type;
        input.classList.add("form-control");
        input.classList.add("m-1");
        input.classList.add("col");
        input.required = required;
        if (typeof value === 'string' || value instanceof String) {
            input.value = value;
        }
        // adding it to the view
        div.appendChild(input);
        div.appendChild(del);
        inputs.appendChild(div);
    }

    export function getData() {
        let inputs = document.getElementById(title + "-inputs");
        data = [];
        inputs.childNodes.forEach((div,i) => {
            data[i] = div.firstChild.value;
        });
    }

    onMount(() => data.forEach((input) => addInput(input)));
</script>

<Card {title}>
    <div id="{title}-inputs">
    </div>
    <button type="button" class="btn btn-outline-primary" on:click={addInput}>+</button>
</Card>