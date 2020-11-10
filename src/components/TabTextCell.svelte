<script>
  export let value
  export let decorators = null
</script>

<p class="text">{ value }</p>

<style type="text/postcss">
  .text {
    @apply text-gray-900 whitespace-no-wrap;
  }
</style>