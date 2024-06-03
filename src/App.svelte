<script lang="ts">

type Item = {
  id: number,
  text: string,
  hovered: boolean
}

// TODO: add base classes for the items
// TODO: add change of color on items that arent hovered while one is
// TODO: add animations to the items
// TOOD: add background images

let items: Item[] = [
  {
    id: 1,
    text: "To crush your enemies,",
    hovered: false
  },
  {
    id: 2,
    text: "see them driven before you,",
    hovered: false
  },
  {
    id: 3,
    text: "and to hear the lamenetation of their women!",
    hovered: false
  }
]

function changeOpactiy(item: Item) {
  items = items.map(i => {
    if(i.id === item.id) {
      return {
        ...i,
        hovered: true
      }
    } else {
      return {
        ...i,
        hovered: false
      }
    }
  })
}


</script>

<main id="menu" class="m-0 h-screen flex gap-4 items-center">
  <div id="items" class="flex flex-col gap-5" >
    {#each items as item}
        <div class="text-5xl {item.hovered ? 'opacity-100' : 'opacity-5'}" on:mouseover={()=> changeOpactiy(item)}>{item.text}</div>
    {/each}
  </div>
</main>