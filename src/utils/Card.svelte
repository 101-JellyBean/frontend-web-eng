<script>
    export let title;
</script>

<div class="card" on:click>
    <div class="card-body">
      <h5 class="card-title">{title}</h5>
      <p class="card-text">
          <slot></slot>
      </p>
    </div>
</div>
