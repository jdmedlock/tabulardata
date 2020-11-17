<script>
  export let rowsPerPage
  export let firstRowDisplayed
  export let totalNoRows

  const firstRow = firstRowDisplayed + 1
  const lastRowDisplayed = firstRowDisplayed + rowsPerPage
</script>

<div class="pagination-controls">
  <span class="pagination-status-text">
    Showing {firstRow} to {lastRowDisplayed} of {totalNoRows} rows
  </span>
  <div class="button-wrapper">
    <button class="prev-button">Prev</button>
    <button class="next-button">Next</button>
  </div>
</div>

<style type="text/postcss">
  /* TODO: Resolve pseudo-classes prefix problem: https://stackoverflow.com/questions/61407335/tailwinds-directive-apply-not-working-on-nuxt */
  
  .pagination-controls {
    @apply px-5 py-5 bg-white border-t flex flex-col xs:flex-row items-center xs:justify-between;
  }

  .pagination-status-text {
    @apply text-xs xs:text-sm text-gray-900;
  }

  .button-wrapper {
    @apply inline-flex mt-2 xs:mt-0;
  }

  .prev-button {
    @apply text-sm bg-gray-300 hover:bg-gray-400 text-gray-800 font-semibold py-2 px-4 rounded-l;
  }

  .next-button {
    @apply text-sm bg-gray-300 hover:bg-gray-400 text-gray-800 font-semibold py-2 px-4 rounded-r;
  }
</style>