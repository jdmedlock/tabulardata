<script>
  export let value
  export let decorators

  const pillColor = decorators.reduce((color, decorator) => { 
    return decorator.value === value ? decorator.pillColor : color
  }, '')

</script>

<td class="table-data">
  <span class="image-wrapper">
    <span aria-hidden class="pill-wrapper { pillColor }" />
    <span class="pill">{ value }</span>
  </span>
</td>

<style type="text/postcss">
  .table-data {
    @apply py-5 bg-white text-sm;
  }

  .image-wrapper {
    @apply relative inline-block py-1 font-medium text-gray-500 leading-tight;
  }

  .pill-wrapper {
    @apply absolute inset-0 opacity-50 rounded-full;
  }

  .pill {
    @apply relative p-2;
  }
</style>