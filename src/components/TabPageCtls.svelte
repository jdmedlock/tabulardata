<script>
  export let rowsPerPage
  export let totalNoRows

  const firstRowDisplayed = 1
  const firstRow = firstRowDisplayed
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
    @apply px-5 py-5 bg-white border-t flex flex-col items-center;
  }

  .pagination-status-text {
    @apply text-xs text-gray-900;
  }

  .button-wrapper {
    @apply inline-flex mt-2;
  }

  .prev-button {
    @apply text-sm bg-gray-300 text-gray-800 font-semibold py-2 px-4 rounded-l;
  }

  .next-button {
    @apply text-sm bg-gray-300 text-gray-800 font-semibold py-2 px-4 rounded-r;
  }

  /* Extra small Screen */
  @screen sm {
    .pagination-controls {
      @apply flex-row justify-between;
    }

    .pagination-status-text {
      @apply text-sm;
    }
  
    .button-wrapper {
      @apply mt-0;
    }
  }

  /* Hover States */
  .prev-button:hover {
    @apply bg-gray-400;
  }

  .next-button:hover {
    @apply bg-gray-400;
  }
</style>