<script>
  export let value
  export let decorators = null
</script>

<td class="table-data">
  <p class="text">{ value }</p>
</td>

<style type="text/postcss">
  .table-data {
    @apply px-2 py-5 border-b border-gray-200 bg-white text-sm
  }
  .text {
    @apply text-gray-900 whitespace-no-wrap;
  }
</style>