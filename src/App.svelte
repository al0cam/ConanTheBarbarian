<script lang="ts">

type Item = {
  id: number,
  text: string,
}

// TODO: add base css classes for the items
// TODO: add change of color on items that arent hovered while one is
// TODO: add animations to the items
// TODO: add background images

let items: Item[] = [
  {
    id: 1,
    text: "To crush your enemies,",
  },
  {
    id: 2,
    text: "see them driven before you,",
  },
  {
    id: 3,
    text: "and to hear the lamenetation of their women!",
  }
]

function changeOpactiy(item: Item){

}

function resetOpacity() {

}

</script>

<!-- Tailwind to apply a class to all descendants of an element add [&_*]
    if only first children then [&>*]
    if specific element then [&_p] -->
<main id="menu" class="m-0 h-screen flex gap-4 items-center">
  <div id="items" class="flex flex-col gap-5 [&_*]:hover:opacity-25" on:mouseleave={() => resetOpacity()}>
    {#each items as item}
        <div class="transition ml-36 ease-in-out duration-200 text-5xl hover:!opacity-100 hover:scale-125" on:mouseover={()=> changeOpactiy(item)}>{item.text}</div>
    {/each}
  </div>
</main>