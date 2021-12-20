<script>
    export let title = 'title';
    export let uniqueId;

</script>

<script context="module">
    export function openModal(uniqueId) {
        let modal = document.getElementById(uniqueId + "-Modal");
        let background = document.getElementById(uniqueId + "-Modal-background");
        modal.style.display = "block";
        background.style.display = "block";
        window.onclick = (e) => {
            if (e.target == modal) {
                modal.style.display = "none";
                background.style.display = "none";
            }
        }
    }

    export function closeModal(uniqueId) {
        document.getElementById(uniqueId + "-Modal").style.display = 'none';
        document.getElementById(uniqueId + "-Modal-background").style.display = 'none';
    }

</script>

<div class="modalBackground" id="{uniqueId}-Modal-background" style="display:none">
    <!-- Modal -->
    <div class="modal" id="{uniqueId}-Modal" style="display:none">
        <div class="modal-dialog modal-dialog-scrollable" role="document">
        <div class="modal-content">
            <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">{title}</h5>
            <button type="button" class="close btn" on:click={closeModal(uniqueId)}>
                <span aria-hidden="true">&times;</span>
            </button>
            </div>
            <div class="modal-body">
                <slot></slot>
            </div>
        </div>
        </div>
    </div>
</div>

<style>
    .modalBackground {
        background-color: rgba(0,0,0,0.6); /* Black w/ opacity */
        z-index: 1;
        height: 100%;
        width: 100%;
        position: fixed;
        top:0;
        left:0;
    }
    
</style>