<script>
  export let definition // Array of data objects defining the report
  export let data // Array of data objects containing the data

  const components = definition.columns.map((columnData) => {
    let componentInvokation
    switch (columnData.type) {
      case 'image':
        break
      case 'pill':
        break
      case 'text':
        componentInvokation = `<TabTextCell dataName={ ${ columnData.dataName } } />`
        break
      default: 
        throw `Unknown cell type encountered (type: ${data.type})`
    }
  })

</script>

<div class="-mx-4 sm:-mx-8 px-4 sm:px-8 py-4 overflow-x-auto">
  <div class="inline-block min-w-full shadow rounded-lg overflow-hidden">
    <table class="min-w-full leading-normal">
      <thead>
        <tr>
          {#each definition.columns as column}
          <th class="column-heading">
            { column.heading }
          </th>
          {/each}
        </tr>
      </thead>
      <tbody>
        {#each data as item, index}
          <tr>
            {#each components as component}
              {@html component}
            {/each}
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
</div>

<style type="text/postcss">
  .column-heading {
    @apply px-2 py-3 border-b-2 border-gray-200 bg-gray-100
      text-left text-xs font-semibold text-gray-600 uppercase
      tracking-wider;
  }
</style>