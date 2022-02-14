<script>
  let count = 0;

  function inc() {
    count++;
  }

  function dec() {
    count--;
  }
</script>

<section>
  <div>
    {#if count <= 10}
      <button on:click={inc}>inc</button>
    {/if}
    {#if count > 10}
      <button on:click={dec}>dec</button>
    {/if}
  </div>
  <p>count {count}</p>
</section>
