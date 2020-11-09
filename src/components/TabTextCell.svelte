<script>
  export let data
</script>

<td class="px-2 py-5 border-b border-gray-200 bg-white text-sm">
  <p class="text">{ data }</p>
</td>

<style type="text/postcss">
  .text {
    @apply text-gray-900 whitespace-no-wrap;
  }
</style>