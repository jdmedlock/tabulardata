<script>
  import TabImageCell from './TabImageCell.svelte'
  import TabPillCell from './TabPillCell.svelte'
  import TabTextCell from './TabTextCell.svelte'

  export let definition 
  
  const data = definition.dataSource.reader(0, definition.dataSource.rowsPerPage)

  const componentRows = data.map((row) => {
    const rowKeys = Object.keys(row)
    return rowKeys.map((cellKey) => {
      const cellValue = row[cellKey]
      let componentInvocation

      const index = definition.columns.findIndex(column => column.dataName === cellKey);
      switch (definition.columns[index].type) {
        case 'image':
          componentInvocation = { component: TabImageCell, value: `${ cellValue }` }
          break
        case 'pill':
          componentInvocation = { component: TabPillCell, value: `${ cellValue }`, 
            decorators: definition.columns[index].decorators }
          break
        case 'text':
          componentInvocation = { component: TabTextCell, value: `${ cellValue }` }
          break
        default: 
          throw `Unknown cell type encountered (type: ${ definition.columns[index].type })`
      }
      return componentInvocation
    })

  })

</script>

<div class="-mx-4 sm:-mx-8 px-4 sm:px-8 py-4 overflow-x-auto">
  <div class="inline-block min-w-full shadow rounded-lg overflow-hidden">
    <table class="table">
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
        {#each componentRows as row}
          <tr>
          {#each row as cell}
            <td class="table-data">
              {#if cell.component === TabPillCell}
                <svelte:component this={ cell.component } value={ cell.value } decorators={ cell.decorators } />
              {:else}
                <svelte:component this={ cell.component } value={ cell.value } />
              {/if}
            </td>
          {/each}
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
</div>

<style type="text/postcss">
  .table {
    @apply min-w-full leading-normal;
  }

  .column-heading {
    @apply px-2 py-3 border-b-2 border-gray-200 bg-gray-100
      text-left text-xs font-semibold text-gray-600 uppercase
      tracking-wider;
  }

  .table-data {
    @apply px-2 py-5 border-b border-gray-200 bg-white text-sm
  }
</style>