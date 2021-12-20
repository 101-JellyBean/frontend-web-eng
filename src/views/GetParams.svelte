<script>
//    let getParams = {
// 		limit: 12,
// 		offset: 0,
// 		orderBy: 'none',
// 		orderDir: 'asc'
// 	}

//     import Modal from "../utils/Modal.svelte";
//     import { createEventDispatcher } from 'svelte';
//     const dispatch = createEventDispatcher();

//     $: dispatch("updateGetParams",getParams);

</script>

<!-- <Modal title="Settings" uniqueId="settings">
    <form on:submit|preventDefault={() => dispatch("useGetParams")}>
        <div class="input-group">
            <div class="input-group-prepend">
                <span class="input-group-text" id="basic-addon1">Limit</span>
            </div>
            <input type="number" class="form-control" id="limitInput" min=1 max=100 bind:value={getParams.limit}>
        </div>
        <div class="input-group">
            <div class="input-group-prepend">
                <span class="input-group-text" id="basic-addon1">Offset</span>
            </div>
            <input type="number" class="form-control" id="offsetInput" min=0 bind:value={getParams.offset}>
        </div>
        <div class="input-group">
            <div class="input-group-prepend">
                <span class="input-group-text" id="basic-addon1">Order by</span>
            </div>
            <select class="form-select" aria-label="Default select example" bind:value={getParams.orderBy}>
                <option value="none">None</option>
                <option value="title">Title</option>
                <option value="year">Year</option>
                <option value="rating">Rating</option>
            </select>
            <div class="input-group">
                <div class="form-check form-check-inline">
                    <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1" value="asc" bind:group={getParams.orderDir}>
                    <label class="form-check-label" for="inlineRadio1">ASC</label>
                </div>
                <div class="form-check form-check-inline">
                    <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2" value="desc" bind:group={getParams.orderDir}>
                    <label class="form-check-label" for="inlineRadio2">DESC</label>
                </div>
            </div>
            <div class="input-group">
                <button class="btn btn-outline-primary col">Find</button>
            </div>
            
        </div>
    </form>
</Modal> -->