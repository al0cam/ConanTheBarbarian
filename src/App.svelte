<script lang="ts">

type Item = {
  id: number,
  text: string,
  opacity: string
}

// TODO: add base css classes for the items
// TODO: add change of color on items that arent hovered while one is
// TODO: add animations to the items
// TOOD: add background images

let items: Item[] = [
  {
    id: 1,
    text: "To crush your enemies,",
    opacity: "opacity-100"
  },
  {
    id: 2,
    text: "see them driven before you,",
    opacity: "opacity-100"
  },
  {
    id: 3,
    text: "and to hear the lamenetation of their women!",
    opacity: "opacity-100"
  }
]

function changeOpactiy(item: Item){
  items = items.map(i => {
    if(i.id === item.id){
      return {
        ...i,
        opacity: "opacity-100"
      }
    } else {
      return {
        ...i,
        opacity: "opacity-35"
      }
    }
  })
}

function resetOpacity() {
  items = items.map(i => {
    return {
      ...i,
      opacity: "opacity-100"
    }
  })
}

</script>

<main id="menu" class="m-0 h-screen flex gap-4 items-center">
  <div id="items" class="flex flex-col gap-5" on:mouseleave={() => resetOpacity()}>
    {#each items as item}
        <div class="transition ease-in-out duration-200 text-5xl {item.opacity}" on:mouseover={()=> changeOpactiy(item)}>{item.text}</div>
    {/each}
  </div>
</main>